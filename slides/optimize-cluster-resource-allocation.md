
class: title

# Optimize Cluster Resource Allocation

---

class: segue

# Harrison Harnisch
## Senior Software Engineer @ Buffer
### [@hjharnis](https://twitter.com/hjharnis)

???

- Helping Buffer transition from a monolith application to a service oriented architecture on Kubernetes
- Roughly 75% of all production traffic is served by Kubernetes

---

class: fifty-fifty

.left-panel[
# Case Study: Links Service
]
.right-panel[
- Preexisting endpoint in our monolith
- Serve the number of times a link is shared within Buffer
]

???

- powers the Buffer share button count, used on various blogs
- the highest throughput endpoint in the Buffer API

---

class: fifty-fifty

.left-panel[
# Case Study: Links Service
]
.right-panel[
- Settled on a simple design using Node and DynamoDB

<img src="{{baseurl}}/images/KubernetesResourceOptimization/Node.png" alt="Node" width="35%" />
<img src="{{baseurl}}/images/KubernetesResourceOptimization/DynamoDB.png" alt="DynamoDB" width="35%" />
]

???

- optimized for speed and cost
- all persistent storage handled outside Kubernetes

---

class: fifty-fifty

.left-panel[
# Case Study: Links Service
]
.right-panel[
- Deployed the service to Kubernetes (4 replicas)
- Manually verified that the service was operational
]

???

- We started doing a slow rollout

---

class: segue

# 1%

---

class: segue

# 1% ➡️️ 10%

---

class: segue

# 1% ➡️️ 10% ➡️️ 50%

---

class: segue

# 1% ➡️️ 10% ➡️️ 🔥

---

class: fifty-fifty

.left-panel[
# Case Study: Links Service
]
.right-panel[
- Scale up replicas (5x - 20 pods)
- Helped, but pods still repeatedly dying
]

???

- repeated this process until the service seem stable but ended up being a ~100 containers before steady state was reached

---

class: segue

# Back to 0%

---

class: fifty-fifty

.left-panel[
# Postmortem
]

.right-panel[
- I had copied and pasted a `Deployment` from another service
- The `Deployment` included resource limits
]

???

- resource limits set to 100Mi memory
- it got me thinking about what optimal resource limits look like

---

# Resource Limits

- limits can be set on both CPU and memory utilization
- pods run with unbounded CPU and memory limits
- Kubernetes will restart containers when limits a reached

???

- capable of consuming all resources on a node

---

class: segue

# How do we optimally set CPU and Memory limits?

---

class: fifty-fifty

.left-panel[
# Optimal Limits
]

.right-panel[
- Pods have enough resources to complete their task
- Nodes run maximum amount of pods
]

---

class: segue

# Under/Over/Even Resource Allocation

---

class: fifty-fifty

.left-panel[
# Under-allocation
]

.right-panel[
- Pods are exceeding resource limits
- Kubernetes kills Pods


.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/UnderAllocation.png" alt="Node" width="70%" />]
]

---

class: fifty-fifty

.left-panel[
# Overallocation
]

.right-panel[
- Pods can never fully utilize resources
- Kubernetes lets pods run, but each pod is allocated extra resources


.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/OverAllocation.png" alt="Node" width="70%" />]
]

---

class: segue

# Overallocation is _tricky_

---

class: segue

# It becomes a problem when you _scale up_ replicas

---

class: center, middle

<img src="{{baseurl}}/images/KubernetesResourceOptimization/OverAllocation.png" alt="Node" width="50%" />

# vs

<img src="{{baseurl}}/images/KubernetesResourceOptimization/JustRight.png" alt="Node" width="50%" />

---

class: segue

# That's one extra pod that could be running

---

class: fifty-fifty

.left-panel[
# Even
]

.right-panel[
- Pods have enough resources to complete the task
- Kubernetes allocates a nodes resources efficiently


<img src="{{baseurl}}/images/KubernetesResourceOptimization/JustRight.png" alt="Node" width="70%" />
]

---

class: segue

# Let's Set Some Limits

---

# Setting Resource Limits

- Goal: Understand what **one pod** can handle
- Start with a very conservative set of limits

```yaml
# for node might be something like
replicas: 1
...
cpu: 100m
memory: 100Mi
```

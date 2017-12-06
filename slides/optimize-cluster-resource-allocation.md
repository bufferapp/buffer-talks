
class: segue

# Load Testing Kubernetes
## How To Optimize Your Cluster Resource Allocation in Production

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
- Serves the number of times a link is shared within Buffer
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
- Scaled up replicas (5x - 20 pods)
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
# Case Study: Links Service
]

.right-panel[
- I had copied and pasted a `Deployment` from another service
- The `Deployment` included resource limits
- `kubectl describe` was reporting `OOMKilled`
]

???

- OOMKilled occurs when Kubernetes kills a pod due to memory constraints
- I could adjust the memory limits, but how much would be enough?

---

# Resource Limits

- Limits can be set on both CPU and memory utilization
- Containers run with unbounded CPU and memory limits
- Kubernetes will restart containers when limits are exceeded

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
- Nodes run maximum number of pods
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
.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/UnderAllocation.png" alt="Node" width="70%" />]
]

???

- Containers are exceeding resource limits
- Kubernetes kills Pods

---

class: fifty-fifty

.left-panel[
# Overallocation
]

.right-panel[
.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/OverAllocation.png" alt="Node" width="70%" />]
]

???

- Pods can never fully utilize resources
- Kubernetes lets pods run, but each pod is allocated extra resources

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
<img src="{{baseurl}}/images/KubernetesResourceOptimization/JustRight.png" alt="Node" width="70%" />
]

???

- Pods have enough resources to complete the task
- Kubernetes allocates a nodes resources efficiently

---

class: segue

# Kubernetes Monitoring

---

class: center

<img src="{{baseurl}}/images/KubernetesResourceOptimization/monitoring-architecture.png" alt="monitoring-architecture" width="80%" />

---

class: fifty-fifty

.left-panel[
# cAdvisor
]

.right-panel[
.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/cadvisor.png" alt="cAdvisor" width="40%" />]
]

???

- container resource monitoring agent
- auto discovers containers in the node
- collects CPU, memory, filesystem and network usage

---

class: fifty-fifty

.left-panel[
# Kubelet
]

.right-panel[
.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/kubelet.png" alt="kubelet" width="40%" />]
]

???

- manages pods and containers
- fetches container usage statistics from cAdvisor

---

class: fifty-fifty

.left-panel[
# Heapster
]

.right-panel[
.center[<img src="{{baseurl}}/images/KubernetesResourceOptimization/heapster.png" alt="heapster" width="40%" />]
]

???

- aggregates cluster wide monitoring and event data
- queries information from Kubelets
- pushes data to a configurable storage backend
  - InfluxDB and Google Cloud Monitoring

---

# Setting Limits

- Goal: Understand what **one pod** can handle
- Start with a very conservative set of limits
- Only change one thing at time and observe changes

```yaml
# limits might look something like
replicas: 1
...
cpu: 100m # 1/10th of a core
memory: 50Mi # 50 Mebibytes
```
---

class: segue

# Testing Strategies

---

class: fifty-fifty

.left-panel[
# Ramp Up Test
]

.right-panel[
<img src="{{baseurl}}/images/KubernetesResourceOptimization/ramp-up-test.png" alt="ramp up test" width="80%" />
]

???

- Ramp up test helps us determine where the breaking point is
- this is the where you make order of magnitude adjustments to limits

---

class: fifty-fifty

.left-panel[
# Duration Test
]

.right-panel[
<img src="{{baseurl}}/images/KubernetesResourceOptimization/duration-test.png" alt="duration test" width="80%" />
]

???

- Duration test helps us determine how the pod performs near breaking point
- This is where you make fine tune adjustments to limits

---

class: segue

# Demo
## Setting Limits For etcd


???

Will probably want to use cAdvisor directly to view container utilization

- create deployment
- create service
- add data to etcd
- curl data to show format
- do ramp up test
  - increase memory (re-run test)
  - increase cpu (re-run test)
  - decrese memory (re-run test)
- do duration test
  - make any fine tune adjustments

Show a quick view of Graphana data to show that data was being collected

---

class: segue

# Keep A Fail Log

???

- Someday the qualitative information will save you
- Helps share the burden of maintenance

---

class: fifty-fifty

.left-panel[
# Some Observed Failure Modes
]

.right-panel[
- Memory is slowly increasing
- CPU is pegged at 100%
- 500s
- High response times
- Large variance in response times
- Dropped Requests
]

---

class: segue

# Case Study: Links Service
## Lessons Learned

???

- Scaling up replicas will not fix all scaling problems
- Almost every service behaves differently when near breaking point
- One requirement for production ready means appropriate resource allocation

---

class: segue

# It's About Increasing Predictability
## And Getting More Sleep

---

class: fifty-fifty

.left-panel[
# Looking Ahead: Kubernetes
]

.right-panel[
- Huge step forward for ops and cluster wide operations
- There's pretty big opportunity to help dev
]

???

- Current monitoring solutions help us monitor resource trends over time
- Not easy to get immediate fine grain feedback
  - cAdvisor or exec and run top etc.
- Both matter!
  - macro is more for ops
  - micro is more for developers

---

class: segue

# KubeScope 🔬
## https://github.com/hharnisc/kubescope

---

class: segue, center

# Questions?

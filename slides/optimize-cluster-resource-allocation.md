
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
- Scale up replicas (4x - 20 pods)
- Helped, but pods still repeatedly dying
]

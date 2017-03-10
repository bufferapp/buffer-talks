
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

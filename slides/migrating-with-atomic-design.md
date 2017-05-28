class: title

# Atomic Design As A Migration Strategy

.footnote[Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]

---

class: segue

# Buffer Web
## **53,677** Commits
## **59** Contributors
## **6.5** Year Lifespan

---

class: segue

## Codebase In Human Years
# **~103 Years Old**
Avg. Startup Lifespan: ~5 Years  
Avg. Human Lifespan: ~79 Years

---

class: segue

# Should I Rewrite?

---

class: fifty-fifty

.left-panel[
# Rewrite?
- ⬇️ Individual Commits / Month
- ⬆️ Commit Size
- ⬇️ Individual Output
]

.right-panel[
<img src="{{baseurl}}/images/MigrateWithAtomicDesign/commits-per-author.png" alt="commits per author" width="100%" />
]

---

class: fifty-fifty

.left-panel[
# Rewrite?
]

.right-panel[
- Simple tasks require large changes
- Small changes have unintended side effects
]

---

class: segue

# Should I Rewrite?

---

class: middle, center

# Sync vs. Async Rewrite

???

- Sync Rewrite
  - sometimes called a complete rewrite
  - blocks new features
- Async Rewrite
  - sometimes called a migration or a re-factor
  - rewritten code can be shipped alongside new features

---

class: segue

# Complete Rewrites Aren't Bad _Sync Rewrites_ Are

---

class: title

# Atomic Design As A Migration Strategy

.footnote[Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]

---

class: title

# Atomic Design As A ~~Migration~~ Rewrite Strategy
## Joel Spolsky Was Wrong

.footnote[Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/things-you-should-never-do.png" alt="things you should never do part 1" width="100%" />

---

class: segue

# That's not exactly true but it gets _less true_ over time

???

- Codebases grow unwieldy over time.
- Maybe you keep ahead of your tech debt and you push that back.
- Maybe you pile it up and you get into a situation like this:

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/marginal-productivity.png" alt="marginal productivity" width="100%" />

???

- This is what happened to the Buffer codebase as we added more engineers over a period of 5 years.
- The commits per person decreased.
- As each person joined, everyone else became less productive.
- This happens because of good old fashioned tech debt.
- It also happens because as you increase team size, you increase complexity and overhead as everyone's work is tangled up in everyone elses.
- If you recognize this kind of a graph, this talk is for you.

---

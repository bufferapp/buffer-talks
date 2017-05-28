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
TODO: ^ wording

---

class: segue

# **Atomic Design** Can Help Us With An Async Rewrite

---

# Atomic Design

- Atom
- Molecule
- Organism

---

class: quote

> Build complexity out of simple elements stitched together

---

class: fifty-fifty

.left-panel[
# Atom
<img src="{{baseurl}}/images/AtomicDesign/atoms.png" alt="atom" width="35%" />
]

.right-panel[
- Building block of an application
- Work in a number of contexts
- Often not useful on their own
]

---

# Atom

```html
<label for="text-input">Search This Site</label>
```

<label for="text-input">Search This Site</label>

```html
<input type="text" placeholder="Enter Keyword" id="text-input"/>
```

<input type="text" placeholder="Enter Keyword" id="text-input"/>

```html
<button>Search</button>
```

<button>Search</button>

---

class: fifty-fifty

.left-panel[
# Molecule
<img src="{{baseurl}}/images/AtomicDesign/molecules.png" alt="molecule" width="35%" />
]

.right-panel[
- Groups of atoms bonded together
- Usually simple and do one thing well
- Built for re-use
]

---

# Molecule

**Search Component**

```html
<div>
  <div>
    <label for="text-input">Search This Site</label>
  </div>
  <input type="text" placeholder="Enter Keyword" id="text-input"/>
  <button>Search</button>
</div>
```

<div>
  <div>
    <label for="text-input">Search This Site</label>
  </div>
  <input type="text" placeholder="Enter Keyword" id="text-input"/>
  <button>Search</button>
</div>

---

class: fifty-fifty

.left-panel[
# Organism
<img src="{{baseurl}}/images/AtomicDesign/page-web.png" alt="organism" width="35%" />
]

.right-panel[
- Groups of Molecules
- Relatively complex
- Enough context defined to perform a task
]

---

# Organism

# TODO: show buffer web image

---

# TODO: Address why Template and Page are left out

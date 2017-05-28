class: title

# Atomic Design As A Migration Strategy

.footnote[Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]

---

# Buffer Web
## **53,677** Commits
## **59** Contributors
## **6.5** Year Lifespan

---

## Codebase In Human Years
# **~103 Years Old**
Avg. Startup Lifespan: ~5 Years  
Avg. Human Lifespan: ~79 Years

---

# Should I Rewrite?

---

# Rewrite?
- ⬇️ Individual Commits / Month
- ⬆️ Commit Size
- ⬇️ Individual Output
<img src="{{baseurl}}/images/MigrateWithAtomicDesign/commits-per-author.png" alt="commits per author" width="100%" />

---

# Rewrite?
- Simple tasks require large changes
- Small changes have unintended side effects

---

# Should I Rewrite?

---

# Sync vs. Async Rewrite

???

- Sync Rewrite
  - sometimes called a complete rewrite
  - blocks new features
- Async Rewrite
  - sometimes called a migration or a re-factor
  - rewritten code can be shipped alongside new features

---

# Complete Rewrite !== _Sync Rewrite_

---

# **Atomic Design** Can Help Us With An Async Rewrite

---

# Atomic Design

- Atom
- Molecule
- Organism

---

# Complexity built out of simple elements stitched together

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

TODO: show buffer web image

---

# How Can **Atomic Design** Be Used To Do An Async Rewrite?

---

# Start Small With An Atom

**Examples**

- Replace a `Label` on a form field
- Replace the company `Image`
- Replace some `Text` in a description

???

- Build the atoms free of any context
- best to start with things that don't require user interaction (buttons, inputs, etc.)
  - allows you to focus on logistical problems first
    - How do I get atoms in the existing app?

---

class: center, middle

<iframe src="https://bufferapp.github.io/buffer-components/?selectedKind=Text&selectedStory=default&full=0&down=1&left=1&panelRight=0&downPanel=kadirahq%2Fstorybook-addon-actions%2Factions-panel" height="90%" width="90%" frameBorder="0"/>

---

# Increase Scope To A Molecule


**Example: Replacing A Form**

- Use the `Label` to create a `Field`
- Use the `Field` to create a `Form`

---

class: center, middle

<iframe src="https://bufferapp.github.io/buffer-web-components/?selectedKind=TextPost&selectedStory=default.%20All%20approval%20view.&full=0&down=1&left=1&panelRight=0&downPanel=kadirahq%2Fstorybook-addon-actions%2Factions-panel" height="90%" width="90%" frameBorder="0" />

---

# For Buffer, this meant creating 2 new repositories

---

![marginal productivity]({{baseurl}}/images/MigrateWithAtomicDesign/marginal-productivity.png)

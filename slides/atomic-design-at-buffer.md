class: title

# Atomic Design

.footnote[Marcus Wermuth ([@mwermuth](https://twitter.com/mwermuth)) <small>and</small> Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]

---

class: quote

> Atomic Design is methodology for creating design systems.

\- Brad Frost

---

# Atomic Design

- Atoms
- Molecules
- Organisms
- Templates
- Pages

---

class: fifty-fifty

.left-panel[
# Atoms
<img src="/images/AtomicDesign/atoms.png" alt="atoms" width="35%" />
]

.right-panel[
- Building block of an application
- Work in a number of contexts
- Often not useful on their own
]

---

# Atoms

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
# Molecules
<img src="/images/AtomicDesign/molecules.png" alt="molecules" width="35%" />
]

.right-panel[
- Groups of atoms bonded together
- Usually simple and do one thing well
- Built for re-use
]

---

# Molecules

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
# Organisms
<img src="/images/AtomicDesign/molecules.png" alt="organisms" width="35%" />
]

.right-panel[
- Groups of Molecules
- Relatively complex
- Often perform a specific task, i.e. Navigation
]

---

# Organisms

**Nav Component**

```html
<Nav>
  <Image src="logo.png" />
  <NavLinks links=["Home", "About", "Contact"] />
  <Search />
</Nav>
```

<nav style="display: flex; background: #eee; align-items: center; padding: 1em;">
  <svg height="64" width="64">
    <circle cx="32" cy="32" r="28" stroke="#2ecc71" stroke-width="4" fill="none"></circle>
    <circle cx="32" cy="32" r="20" stroke="#08BCD0" stroke-width="4" fill="none" />
  </svg>
  <ul style="display: flex; list-style: none; padding: 0; margin: 0; flex-grow: 1; font-size: 2.5rem">
    <li style="margin-left: 1.5rem;"><a href="#">Home</a></li>
    <li style="margin-left: 1.5rem;"><a href="#">About</a></li>
    <li style="margin-left: 1.5rem;"><a href="#">Contact</a></li>
  </ul>
  <div>
    <div>
      <label for="text-input">Search This Site</label>
    </div>
    <input type="text" placeholder="Enter Keyword" id="text-input"/>
    <button>Search</button>
  </div>
</nav>

---

class: fifty-fifty

.left-panel[
# Templates
<img src="/images/AtomicDesign/template-app.png" alt="template" width="35%" />
]

.right-panel[
- Provide scaffolding with placeholder content
- Provides context to Molecules and Organisms
- High or low fidelity
]

???
- This is the design
- [Sketch](https://sketchapp.com/)
- [Figma](https://figma.com)

---

# Templates

.center[<img src="/images/AtomicDesign/TemplateExample.png" alt="Template Example" width="60%" />]

---

class: fifty-fifty

.left-panel[
# Page
<img src="/images/AtomicDesign/page-app.png" alt="page" width="35%" />
]

.right-panel[
- A template populated with real content
- All Atoms and Molecules can be viewed in context
- Variations of inputs can be tested here
]

---

# Page

.center[<img src="/images/AtomicDesign/PageExample.png" alt="Page Example" width="60%" />]

---

class: segue

# Atomic Design At Buffer

---

class: segue

# Mobile

---
class: fifty-fifty

.left-panel[
# Why?
- there was no structure
- no dedicated Mobile Design Position
- making switch between products seamless
]

.right-panel[
<img src="/images/AtomicDesign/history.gif" alt="Buffer Android History" width="50%" />
]

---

class: segue

# Demo

???

Sketch Demo Mobile

---

# Benefits for Mobile

- quickly shift between abstract and concrete
- easily scalable
- A/B testing becomes easier

---

# How to do this?

---

class: segue

# Web

---

# Atomic Design For The Web

- React components
- We conform to the concepts around atoms, molecules and pages
- Templates are a fuzzy area

???

- everything is technically a template with React

---

class: fifty-fifty

.left-panel[
# Atoms
<img src="/images/AtomicDesign/atoms.png" alt="atoms" width="35%" />
]

.right-panel[
- Work in many different contexts
- Buffer Components
]

???

- the atoms
- stateless and functional
- show a quick demo of buffer components

---

class: fifty-fifty

.left-panel[
# Molecules
<img src="/images/AtomicDesign/molecules.png" alt="molecules" width="35%" />
]

.right-panel[
- Made up of Buffer Components
- Buffer Web Components Repository
]

???

- the molecules
- stateless and functional
- show a quick demo of buffer web components

---

class: fifty-fifty

.left-panel[
# Page
<img src="/images/AtomicDesign/page-web.png" alt="page" width="35%" />
]

.right-panel[
- Made up of Molecules
- Sometimes need to use an Atom directly (labels are common)
]

???
- state is managed at this level
- data is applied to templates at this level
- show a quick demo of the colab tool (or TODO: screenshot)

---

# Atom / Molecule / Page Flow

<img src="/images/AtomicDesign/AtomsMoleculesPages.png" alt="Buffer Pages" width="60%" />

???

- page is where we manage state
- page is where we compose molecules and atoms
- do a quick demo of changing button color (if time)

---

class: title

# Questions?

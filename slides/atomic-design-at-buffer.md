# Atomic Design At Buffer

.footnote[Marcus Wermuth ([@mwermuth](https://twitter.com/mwermuth)) and Harrison Harnisch ([@hjharnis](https://twitter.com/hjharnis))]
---

# What Is Atomic Design?

> Atomic design is methodology for creating design systems [of components]. - Brad Frost

---

# What Is Atomic Design?

**The Five Levels**

- Atoms
- Molecules
- Organisms
- Templates
- Pages

---

# Atoms

- Building block of an application
- Work in a number of contexts
- Often not useful on their own

---

# Atoms

**Label Component**

```html
<label for="text-input">Search This Site</label>
```

<label for="text-input">Search This Site</label>

**Input Component**

```html
<input type="text" placeholder="Enter Keyword" id="text-input"/>
```

<input type="text" placeholder="Enter Keyword" id="text-input"/>

**Button Component**

```html
<button>Search</button>
```

<button>Search</button>

---

# Molecules

- Groups of atoms bonded together
- Usually simple and do one thing well
- Built for re-use

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

# Organisms

- Groups of Molecules
- Relatively complex
- Often perform a specific task, i.e. Navigation

---

# Organisms

**Nav Component**

```html
<Nav>
  <Image src="awesome.png" />
  <NavLinks links=["Home", "About", "Contact"] />
  <Search />
</Nav>
```

<nav style="display: flex; background: #eee; align-items: bottom; align-items: flex-end; padding: 1em;">
  <img src="/images/AtomicDesign/AwesomeFace.png" style="height: 2em; width: 2em;" />
  <ul style="display: flex; list-style: none; padding: 0; margin: 0; flex-grow: 1;">
    <li style="margin-left: 2em;"><a href="#">Home</a></li>
    <li style="margin-left: 0.5em;"><a href="#">About</a></li>
    <li style="margin-left: 0.5em;"><a href="#">Contact</a></li>
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

# Templates

- Provide scaffolding with placeholder content
- Provides context to Molecules and Organisms
- High or low fidelity

???
- This is the design
- [Sketch](https://sketchapp.com/)
- [Figma](https://figma.com)

---

# Templates

<img src="/images/AtomicDesign/TemplateExample.png" alt="Template Example" width="60%" />

---

# Page

- A Template populated with real content
- All Atoms and Molecules can be viewed in context
- Variations of inputs can be tested here

---

# Page

<img src="/images/AtomicDesign/PageExample.png" alt="Page Example" width="60%" />

---

# Atomic Design At Buffer

---

# Demo (Android)

---

# Atomic Design For The Web

???

invert colors on this slide

---

# Atomic Design For The Web

- React components
- We conform to the concepts around atoms, molecules and pages
- Templates are a fuzzy area

???

- everything is technically a template with React

---

# Buffer Web - Atoms

- Buffer Components
- Work in many different contexts

<img src="/images/AtomicDesign/BufferComponents.png" alt="Buffer Components" width="20%" />

???

- the atoms
- stateless and functional

---

# Buffer Web - Atoms

<img src="/images/AtomicDesign/BufferComponentsStory.png" alt="Buffer Components" width="60%" />

---

# Buffer Web - Molecules

- Buffer Web Components
- Made up of Buffer Components

<img src="/images/AtomicDesign/BufferWebComponents.png" alt="Buffer Web Components" width="40%" />

???

- the molecules
- stateless and functional

---

# Buffer Web - Molecules

<img src="/images/AtomicDesign/BufferWebComponentsStory.png" alt="Buffer Web Components" width="60%" />

---

# Buffer Web - Pages

- Made up of Molecules
- Sometimes need to use an Atom directly (labels are common)

---

# Buffer Web - Pages

<img src="/images/AtomicDesign/BufferWeb.png" alt="Buffer Pages" width="60%" />

---

# Atom / Molecule / Page Flow

<img src="/images/AtomicDesign/AtomsMoleculesPages.png" alt="Buffer Pages" width="60%" />

???

- page is where we manage state
- page is where we compose molecules and atoms

---

# Demo

<img src="/images/AtomicDesign/demo.gif" alt="Demo.gif" width="40%" />

???

- show Buffer Components in the storybook
- do a quick change of the button color

---

# Questions

# Atom Design At Buffer

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

# Demo (Web)

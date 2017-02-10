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

**Label**

```html
<label for="text-input">Search This Page</label>
```

<label for="text-input">Search This Page</label>

**Input**

```html
<input type="text" placeholder="Enter Keyword" id="text-input"/>
```

<input type="text" placeholder="Enter Keyword" id="text-input"/>

**Button**

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

**Search**

```html
<div>
  <div>
    <label for="text-input">Search This Page</label>
  </div>
  <input type="text" placeholder="Enter Keyword" id="text-input"/>
  <button>Search</button>
</div>
```

<div>
  <div>
    <label for="text-input">Search This Page</label>
  </div>
  <input type="text" placeholder="Enter Keyword" id="text-input"/>
  <button>Search</button>
</div>

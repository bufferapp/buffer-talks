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

```html
<label for="text-input">Search This Page</label>
```

<label for="text-input">Search This Page</label>

```html
<input type="text" placeholder="Enter Keyword" id="text-input"/>
```

<input type="text" placeholder="Enter Keyword" id="text-input"/>

```html
<button>Search</button>
```

<button>Search</button>

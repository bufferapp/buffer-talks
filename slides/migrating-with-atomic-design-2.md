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

# That's not exactly true but it gets _more true_ over time

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
- It also happens because as you increase team size, you increase complexity and overhead as everyone's work is tangled up in everyone else's.
- If you recognize this kind of a graph, this talk is for you.

---

class: segue

# The Mythical Rewrite

???

- This is the point where companies face The Death Choice.
- Stop and rewrite, knowing that you'll freeze feature development (or have to build things twice).
- Many are familiar with the Basecamp rewite story
- Few know the stories of the companies that never came out the other side of the mythical rewrite unless you go to failcon a lot.
- That leaves the other option: keep hacking away, making small adjustments, and walking down that declining marginal productivity curve, adding more engineers and complexity as you try stagger along some development.
- This looks a lot like a slow death - all those “didn’t stay agile” “couldn’t keep up” “stopped innovating” companies.
- Many of us have been there.
- We got into this spot because our stack is not very amenable to change, and most importantly we didn't write code to handle change.
- now the only options feel like bad options.

---

class: segue

# There's a _third_ option

???

- There's a third option here: the asynchronous rewrite, to move to an architecture that is better at handling change
- This is where Atomic Design helps us out

---

class: segue

# Atomic Design

---

class: quote

> Build complexity by stitching simple things together

---

class: segue

# Atom»Molecule»Organism

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

# Organism

<img src="{{baseurl}}/images/AtomicDesign/page-web.png" alt="organism" width="50%" />

---

class: segue

# Buffer Migration Process

---

# Create Atom Library

<iframe src="https://bufferapp.github.io/buffer-components/" height="70%" width="100%" frameBorder="0"/>

???

- [Buffer Components](https://github.com/bufferapp/buffer-components)
- Useful in almost any context

---

# Create Molecule Library

<iframe src="https://bufferapp.github.io/buffer-web-components/" height="70%" width="100%" frameBorder="0" />

???

- [Buffer Web Components](https://github.com/bufferapp/buffer-web-components)
- Some Buffer specific context set

---

# Migrate An Atom

- Pick something small like `Text`
- Build `Text` in the Atom Library
- Replace one `Text` element with the new Atom

???

- text component is nice because it doesn't require user interaction
- focus on the logistics of bringing an atom into the application, ex. NPM

---

class: segue

# Build A New Feature As A Molecule

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/post-breakdown.png" alt="post breakdown" width="80%" />

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/post-breakdown-implementation.png" alt="post breakdown" width="65%" />

---

# Some Assembly Required
.center[
<iframe src="https://giphy.com/embed/AYLNzUe39OSgE" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
]

---

class: segue

# Approach 1: IFrames

???

- Excellent for guarding CSS
- Lots of usage of postMessage
  - Showing and hiding overlays or tooltips
  - Triggering UI updates in the parent frame
  - Difficult to utilize existing resources (like websockets)

---

class: segue

# Approach 2: Inline Styles + Unset CSS

???

- Requires resetting specific rules set in global scope
  - call out specificity here
- New overlays can be implemented in atoms and molecules
- Easily use existing websockets
- Can utilize existing codebase

---

class: center, middle

# Build New Application Shell

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/migrate.png" alt="migrate" width="65%" />

???

- New features are shipped in existing application then assembled in new application
- things like navigation for new application will need to be built at this stage
- Iterate until all customers can be moved to new application

---

class: segue

# What does development look like?

---

class: segue

# Build UI in most the productive environment

???

- right now that's using tools like storybook and jest snapshots
  - these things will likely change
- things that won't change
  - isolated environment
  - think about component API first
  - state last (if at all)
- Development across projects should feel the same

---

# Build For A Constantly Changing Future

- Rewrite while continuously shipping features
- Should be easy to rebuild something if needed (modular)
- Dev environment should be most productive environment

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

class: center, middle

.left.inline-block[
```diff
Author: Joel Gascoigne
Date:   Thu Oct 21 18:46:38 2010 +0100

    First commit

diff --git a/README b/README
new file mode 100644
index 0000000..ee05327
--- /dev/null
+++ b/README
@@ -0,0 +1 @@
+This is my new project
```
]

---

class: center, middle

.left.inline-block[
```diff
Author: Emily
Date:   Tue May 23 07:24:38 2017 -0700

    update tests

diff --git a/tests/fixtures/update.yml b/tests/fixtures/update.yml
index 3393f30..e5708ce 100644
--- a/tests/fixtures/update.yml
+++ b/tests/fixtures/update.yml
@@ -120,4 +120,4 @@ update_with_media_and_alt_text:
   media:
     photo: photo_media_url
     thumbnail: thumbnail_media_url
-    description: 'alt text'
+    alt_text: 'alt text'
diff --git a/tests/libs/UpdatePatcher.php b/tests/libs/UpdatePatcher.php
index e1e2f0f..64809b9 100644
--- a/tests/libs/UpdatePatcher.php
+++ b/tests/libs/UpdatePatcher.php
@@ -214,7 +214,7 @@ class UpdatePatcherTest extends CIUnit_TestCase
         $this->assertEquals([
             'thumbnail' => 'new_thumbnail_url',
             'photo' => 'new_photo_url',
-            'description' => 'alt text'
+            'alt_text' => 'alt text'
         ], $patched_update->media);

```
]

---

class: segue

## Codebase In Human Years
# **~103 Years Old**
Avg. Startup Lifespan: ~5 Years  
Avg. Human Lifespan: ~79 Years

---

class: quote

> I feel like I'm Moving Slower

\- Developers

---

class: fifty-fifty

.left-panel[
<img src="{{baseurl}}/images/MigrateWithAtomicDesign/commits-per-author.png" alt="commits per author" width="100%" />
]

.right-panel[
- Individuals Are Committing Less Often
- Commit Size Are Increasing
- Individuals Are Writing Less Code
]

---

class: segue

# Commit Data Alone Doesn't Mean Much
## Pair It With Qualitative Observations

???

- Have to touch lots of code to get simple tasks done
- Small changes have ability to break other parts of the codebase

---

class: fifty-fifty

.left-panel[
<img src="{{baseurl}}/images/MigrateWithAtomicDesign/marginal-productivity.png" alt="commits per author"/>
]

.right-panel[
- Adding more team members slows down individuals
- Individuals get more done in small teams
]

---

class: segue

# What Is Atomic Design?

---

class: center, middle

# Atom

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/atom.jpg" alt="atom"/>

---

class: center, middle

# Molecule

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/molecule.jpg" alt="molecule" width="40%"/>

---

class: center, middle

# Organism

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/organism.jpg" alt="organism" width="50%"/>

---

class: title

# Atom&raquo;Molecule&raquo;Organism

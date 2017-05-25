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
Author: Emily <eplummer26@gmail.com>
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

class: quote

> I feel like I'm Moving Slower

\- Developers

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/commits-per-author.png" alt="commits per author"/>

---

- TODO: Individual commits per month graph
- TODO: Individual lines per month graph

---

- Individuals Are Committing Less Often
- Commit Size Increasing
- Individuals Are Writing Less Code

---

class: center, middle

<img src="{{baseurl}}/images/MigrateWithAtomicDesign/marginal-productivity.png" alt="commits per author"/>

---

class: segue

## In Smaller Partitioned Teams, Individuals Are More Productive

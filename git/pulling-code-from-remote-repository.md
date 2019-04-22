# Pulling Code from a Remote Repository

Sometimes, the code in your remote repository will contain commits absent in your local repository. You will thus need to **pull** these commits into your local repository. 

## 1. git fetch

The first thing to do is **fetch** the repository, which will download the commit data for each branch that the remote repository contains.

```bash
$ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/jsiny/LS-1
   8ffe20f..fb477f6  master     -> origin/master
```

## 2. git diff <your local repo> <remote repo>

Look at what has changed by using the **diff** command:

```bash
# Compare the local master branch to the master branch in the remote repository aliased origin
$ git diff master origin/master
diff --git a/README.md b/README.md
index 679c481..6f242ce 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,7 @@
-# README #
\ No newline at end of file
+# README #
+
+Hello, world!
+I'm Juliette.
+
+* Female
+* Paris, FR
```

## 3. git pull origin master

Then **pull** the changes into your local repository:

```bash
$ git pull
Updating 8ffe20f..fb477f6
Fast-forward
 README.md | 8 +++++++-
 1 file changed, 7 insertions(+), 1 deletion(-)
```

---
TIL #2 - 22/04/2019

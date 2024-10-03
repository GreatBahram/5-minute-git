# Git apply

`git apply` takes a diff stored in a patch file and applies those changes to your working directory. This feature enables you to integrate updates received from non-Git sources, like chat messages.

## Applying Patch Files in Git

In Git, the `git apply` command is used to apply patch files to your current working directory. Patch files store changes made to a codebase, and `git apply` allows you to incorporate these changes into your project.

## Basic Commands

### Apply Patch

```shell
git diff -c core.pager less main... > changes.patch
git apply -v changes.patch
```

This command generates a patch file called `changes.patch` using `git diff`, which compares changes from the `main` branch and writes them to the file.

`git apply -v changes.patch` then applies the changes from the patch file with verbose output to display what is happening.

### 🎯 Reverse a Patch

```shell
git apply -v -R changes.patch
```

Use the `-R` or `--reverse` option to undo the changes in a patch file, reverting your code back to its previous state.

### ✅ Check a Patch

```
git apply -v --check changes.patch
```

The `--check` option ensures that the patch can be applied cleanly before making any changes. This is useful for verifying whether a patch will apply without conflicts.

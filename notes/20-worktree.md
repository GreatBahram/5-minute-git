# Worktree

With the help of worktree, you can simplify the following tasks:

- Making a quick fix **without committing or stashing work in progress**.
- Comparing different versions of your repository for regressions.
- Testing a change that requires rebuilding your project environment, such as a new
- version of your chosen programming language.
- and more ...

## Create a worktree

```shell
git worktree add ../hotfix-login-problem
```

By default git will use the directory name, for the branch name, if you want to change that you can use the `-b` to specify a different branch name.

To start at a different commit, use -b and also provide a reference, like a SHA or a branch name:

```shell
git worktree add ../hotfix-login-problem main asdfad
```

How to get there?

```shell
cd ../hotfix-login-problem
```

## List worktree and remove

```shell
git worktree list
```

```shell
git worktree remove ....
```


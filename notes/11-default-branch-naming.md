# Default branch naming

## Objectives

- configure the default branch name
- rename an existing repository
- alias master as main

## Configure the default branch name

Git [default branch](https://sfconservancy.org/news/2020/jun/23/gitbranchname/) name is hurtful to some people; you can easily change this:

```shell
git config --global init.defaultBranch main
```

>  [!TIP]
> Now, every time you create a git repository, the default branch name is going to be 'main'.

## Renaming an exiting repository master branch to main

Search for "master" in your repository using `ripgrep` and fix them all:

```
rg master
```

All copies of the repository will also need to update the local branch name:

```shell
# rename the master branch to main
git branch -m master main

# get the latest changes
git fetch origin

# set branch main to track origin/main
git branch -u origin/main main

# change the head to where origin/heads points at
git remote set-head origin -a
```

## Alias master as main in the legacy repositories

Some legacy repositories will require serious effort to rename their “master” branch. Until that happens, you might find it annoying to remember to use “master” when you work on such repositories.

```shell
git switch main # this will fail
```

Luckily, Git offers a solution: “symbolic references”,

```shell
git symbolic-ref refs/heads/main refs/heads/master

git symbolic-ref refs/remotes/origin/main refs/remotes/origin/master

# in case you want to delete them use -d for instance
git symbolic-ref -d refs/heads/main refs/heads/master
git symbolic-ref -d refs/remotes/origin/main refs/remotes/origin/master
```

Let's look at the `git log`

Let's define an alias for this :heart_eyes:

```shell
git config --global alias.alias-master-as-main '!git symbolic-ref refs/heads/main refs/heads/master && git symbolic-ref refs/remotes/origin/main refs/remotes/origin/master && git switch main'
```

You can run this alias with ease:

```shell
git alias-master-as-main
```

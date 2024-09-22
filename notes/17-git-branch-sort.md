# Git branch list

Git by default sorts the list of branch names alphabetically, let's check it together:

```shell
git branch
```

It would have been nicer to sort them by recency, the good news is, that is possible:

```shell
git sort --sort=-commiterdate
```

However, running this command always is a bit cumbersome, what we can do is to configure git to act like this by default:

```shell
git config --global branch.sort -commiterdate
```

and run `git branch` and enjoy this :rocket:
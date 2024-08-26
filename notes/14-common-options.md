# Common options

Here, we look at some options and data types common to all or many Git commands.

## How to ask for help

`git config -h`

`git config --help` long format using a pager

`man git-config`

`git help -w config`

## Override configuration with -c

override the configuration with `-c`

```shell
git -c 'user.name=John' commit -m "commit msg"
git -c core.pager=less diff
```

## Commit SHAs

Git identifies commits with hexadecimal signatures like:

```shell
3da3de5e2ad8fe715659b2abc184791752ce0193
```

### SHA abbreviation

```shell
git log
git log --oneline
```

you can see the SHA of the current git commit

```shell
git rev-parse @ # @ refers to HEAD or the latest commit

git rev-parse --short @
git rev-parse main
```

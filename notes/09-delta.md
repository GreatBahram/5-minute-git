# Delta

Code evolves, and we all spend time studying diffs. [Delta](https://dandavison.github.io/delta/) aims to make this both <u>efficient</u> and <u>enjoyable</u>.

**Objectives**

- Configure git to utilise delta
- Explore key Git sub-commands that benefit from this enhancement
- Learn how to temporarily disable Delta when needed for specific tasks

## new git configuration for delta

`git config --global -e`

```ini
[core]
    pager = delta

[delta]
    # https://dandavison.github.io/delta/configuration.html
    hyperlinks = true
    hyperlinks-file-link-format = "vscode://file/{path}:{line}"
    line-numbers = true
    navigate = true
    syntax-theme = Monokai Extended

[diff]
    colorMoved = default

[interactive]
    diffFilter = delta --color-only

[merge]
    conflictStyle = zdiff3
```

`interactive.diffFilter`: a second way that Git can call delta. Git calls the
diffFilter to show diffs during interactive commands like git add --patch.

`merge.conflictStyle`: configures how Git displays merge conflicts. Git’s default style, merge, shows the two sides of a conflict. The zdiff3 style also shows the
original version of the conflicted area

## A few affected sub-commands

```shell
git add --patch
git log --patch/-p
git blame readme.md
```

## Temporarily disable delta

```shell
git -c core.pager=less diff
```

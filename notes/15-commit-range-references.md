# Commit references

you might see **revision parameters** in git documentation (git-log), this is an old name for **commit reference**.

## Commit range references

- `<a>..<b>` (two dots) - commits in B but not A
- `<a>...<b>` (three dots) - commits in A and B (excluding their common base), i.e. difference

> [!TIP]
> Omit one of `<a> or <b>` and it will default to HEAD (the latest commit).

> [!NOTE]
> Such commit ranges work with `git log`, the lower-level `git rev-list`, and a few other commands.

> [!CAUTION]
> `git diff` accepts identical syntaxes with opposite meaning

> [!TIP]
> Best to stick to three dots with git diff or two-dots with log, since it makes sense: :woman_shrugging:

|    cmd     | `<a>..<b>`  | `<a>...<b>` |
| :--------: | :---------: | :---------: |
| `git log`  | B but not A |   A and B   |
| `git diff` |   A and B   |  B but not  |

Time for some examples:

```shell
git log --oneline main..candy_kingdom
```

That is like asking: “<u>Which commits</u> have been added to `candy_kingdom` since it branched from `main`?”.

If `candy_kingdom` is the current branch, you can skip writing it:

```
git log --oneline main..
```

The reverse:

```shell
git log --oneline candy_kingdom..main
```

Like asking: “<u>Which commits</u> have been added to `main` since `candy_kingdom` branched from it?”.

Again, when `candy_kingdom` is the current branch, you can skip writing it:

```shell
git log ..main
```

`git diff` with three-dot ranges

```shell
git diff main...candy_kingdom
```

That is like asking: “<u>Which changes</u> have been added to candy_kingdom since it branched from main?”.

This is what we call merge request/pull request on git hosts.

```shell
git diff ...main
```

Like asking: “<u>Which changes</u> have been added to main since candy_kingdom branched from it?”.



**Question:** When we open a Pull Request on GitHub, which command produces the result that we see?
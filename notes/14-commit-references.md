# Commit references

you might see **revision parameters** in git documentation (git-log), this is an old name for **commit reference**.

## Single commit references

- SHA

- `@` is the short alias for HEAD, preferable for rapid commandlining.

- `~` and `~<n>` operators

  - `@~` - the previous commit.
  - `@~~` - the previous previous commit.
    - you can chain it but it is annoying, so use ~ with a number to select how many commits to traverse backwards.
  - `HEAD~3` - three commits before the current one on the main branch.

- `-` and `@{-<n>}`, examples:

  - `-`: the previously checked out branch.

    ```shell
    git switch main
    git switch -
    ```

    ```shell
    git switch @{-2} # the previous previously checkout out branch.
    # in other words: git switch - == git switch @{-1}
    ```
    

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
git log --oneline main..feature_a
```

That is like asking: “Which commits have been added to candy_kingdom since it branched
from main?”.

If candy_kingdom is the current branch, you can skip writing it:

```
git log --oneline main..
```

The reverse:

```shell
git log --oneline feature_a..main
```

Like asking: “Which commits have been added to main since candy_kingdom branched from it?”.

Again, when candy_kingdom is the current branch, you can skip writing it:

```shell
git log ..main
```

`git diff` with three-dot ranges

```shell
git diff main...candy_kingdom
```

That is like asking: “Which changes have been added to candy_kingdom since it branched from main?”.

This is what we call merge request/pull request on git hosts.

```shell
git diff ...main
```

Like asking: “Which changes have been added to main since candy_kingdom branched from it?”.
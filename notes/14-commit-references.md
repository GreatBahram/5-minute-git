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
    

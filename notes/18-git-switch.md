Stop using `git checkout` 😡, instead opt for git switch.

The reason for this is `git checkout` does two jobs:

- switching between branches
- restoring old file version (now possible with git restore which will be covered later).
- and, checkout as a word is super confusing for newbies :man_shrugging:.

Let's figure out how we can use git switch :rocket:

## Switching between branches

Switching is easy:

```shell
git switch branch_name
```

## Creating branches

```shell
git switch -c new_branch_name

# or create it from specific commit/branch

git switch -c new_branch_name feature_a
```

## Detached HEAD

Sometimes you want to switch to an old commit or tag, such as when investigating a
problem:

```shell
git switch -d/--detach ir1979fa
```

## oh-my-zsh-aliases

| alias  |             command             |
| ------ | :-----------------------------: |
| `gsw`  |           `git swich`           |
| `gswc` |      `git switch --create`      |
| `gswm` | `git switch $(git main_branch)` |

 	
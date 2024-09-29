## Git Restore

Stop using `git checkout` 😡, instead opt for `git switch`. You can use git restore to undo changes.

Let's figure out how we can use git restore :rocket:

## undo unstaged changes

One can undo unstaged changes by using `git restore` or by providing `-W` by it is provided by default:

```shell
git restore .
```

## undo staged changes

using `-S/--staged`

```shell
git restore -S .
```

## Restore a file from a specific commit or branch

In addition, you can also use `git restore` to retrieve a file from a specific commit, let's see an example:

- `git restore -s revision filename`  

> [!TIP]
>
> Revision in git can be a tag, branch, or a commit.

## Bonus

Last but not least, I use the following command to discard any changes, both staged and unstaged onnes, in my directory. One can also use `git reset --hard @`, but this one feels safer :man_shrugging::

- `git restore -SW .`

## oh-my-zsh-aliases

| alias  |        command         |
| ------ | :--------------------: |
| `grs`  |     `git restore`      |
| `grst` | `git restore --staged` |

 	
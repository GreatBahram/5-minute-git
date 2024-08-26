## Hooks and the pre-commit framework

> [!NOTE]
>
> What are git hooks? Some customs programs/scripts within a repository that Git runs during certain actions.

You can find the git hooks in the following path:

```shell
ls .git/hooks
```

What you see here are a starting point.

> [!IMPORTANT]
>
> Git hooks have some drawbacks:
>
> - Since they live in the `.git` directory, hooks are not committed to the repository, i.e. they are not tracked.
> - For maximum value, you’d want hooks to run on all your team members’ environments and CI.
> - You can only have one of each hook.

[pre-commit](https://pre-commit.com/) is here to address this issue.

```shell
pipx install pre-commit
```

In order to benefit from `pre-commit` you need to install it in your repository:

```shell
pre-commit install
```

> [!NOTE]
> Every team member needs to install `pre-commit`!

Let's try to commit something

```shell
git commit -m 'test pre-commit'
```

This will fail since you've not configured `pre-commit`. This tool comes with a sample configuration.

```shell
pre-commit sample-config
```

```shell
pre-commit sample-config > .pre-commit-config.yaml
git add .pre-commit-config.yaml
```

Let's review some basic commands of `pre-commit`:

```shell
pre-commit run --all-files
```

```shell
pre-commit autoupdate
```

Here you can find a list of [common hooks](https://github.com/pre-commit/pre-commit-hooks):

-  check-case-conflict
-  check-merge-conflict
-  no-commit-to-branch
-  ripsecrets

> [!TIP]
>
> In case you want to run all hooks on CI, you can put this command in your configuration file:
>
> ```shell
> pre-commit run --all-files
> ```
## Skip hooks temporarily

There are times that you need to skip the hooks temporarily, this can be done through two approaches:

First approach, is use to use `--no-verify` option from git sub-command:

```shell
git commit --no-verify -m 'blah blah blah'

git commit -nm 'blah blah blah'
```

Or you can selectively skip with the **SKIP** environment variable

```shell
SKIP=no-commit-to-branch git commit -m "Hotfix auth system"
```

## oh-my-zsh plugin

Let's activate the plugin in oh-my-zsh for this tool.

Get a list of aliases for pre-commit:

```shell
alias | grep pre-commit
```

| Alias   | Command                      |
| ------- | ---------------------------- |
| `prc`   | `pre-commit`                 |
| `prcau` | `pre-commit autoupdate`      |
| `prcr`  | `pre-commit run`             |
| `prcra` | `pre-commit run --all-files` |
| `prcrf` | `pre-commit run --files`     |

# Shell Aliases

Q: What is an alias?

A: With the help of an alias you can define <u>a short name</u> that runs <u>a longer command</u>
or series of commands.

> [!NOTE]
>
> **Pro Tip**: Aim to run ~80% of your Git commands via shell aliases

## How does shell alias work? :nerd_face:

```shell
# Listing All Aliases
alias

# viewing aliases with a pager
alias | less

# searching for a specific alias
alias | grep 'pattern'
```
## Defining an alias like a dude :sunglasses: 

To create an alias, use the following syntax:

`alias <name>=<command>`

```shell
alias g=git
g diff
alias gd='git diff'
```

## Bypass aliases with `\` :punch:

If you need to bypass an alias and run the original command, prefix the command with a backslash `\`.

```shell
alias gs='git status'
type -a gs

\gs
```


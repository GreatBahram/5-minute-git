# 02 - auto fix & colourful git output :rainbow:

**Objectives**

- Auto Correct
- Colourful git output

## Auto Correct

How to enable it:

```shell
git config --global help.autoCorrect prompt/immediate/a_number_in_deciseconds
```

## Colourful git output

```shell
[color "branch"]
        current = yellow reverse
        local = yellow
        remote = green

[color "diff"]
        meta = yellow bold
        frag = magenta bold
        new = green bold
        old = red bold
        whitespace = red reverse

[color "status"]
        added = yellow
        changed = green
        untracked = cyan
```
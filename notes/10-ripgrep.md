# ripgrep

You’re likely familiar with `grep` for searching files using regex, and `git grep` for focusing on tracked files. But there’s a third tool you should know about: **`ripgrep`**. Why? Let's find out! 

- **Blazingly fast** performance.

- Automatically respects `.gitignore` files.

- Seamless integration with tools like **Delta** and **Less**.

## Basic options

- `-i` `--ignore-case`
- `-S`, `--smart-case`
- `--hyprelink-format`

## Customisation

Everyone is expecting an environment variable, `ripgrep` is no exception

`export RIPGREP_CONFIG_PATH=~/.config/ripgreprc`

```shell
# Enable file path hyperlinks
--hyperlink-format
default

# Case insensitive unless pattern contains uppercase characters
--smart-case

# Search hidden files by default, but not Git data directories
--hidden
--glob
!.git
```

## Get a lovely formatting rg + delta

```shell
rg --json <options> | delta
```

```
#.zshrc
function rg() {
	command rg --json $@ | delta;
}
```
# Centralise git configuration

**Objectives**

- move git configuration from the legacy one to a better structured one.
- how to read/update git configuration (briefly)
- where git configuration is coming from :thinking:

## Intro

As you might know git has three different configuration:

- `system`: applied to all users on your computer
- `global`: applied to all repositories for a single user
- `local`: applied to a single repository

## Migration :hatched_chick:

Migrate the main configuration file

```shell
mkdir -p ~/.config/git
mv ~/.gitconfig ~/.config/git/config

# let's test it together
git config --global user.name
```

Migrate the global ignore file

```shell
# let's check where it is located now
git config --global core.excludesFile
mv $(git config --global core.excludesFile)  ~/.config/git/ignore

git config --global --unset core.excludesFile
```

```shell
# ~/.config/git/config (sample .gitignore)
.vscode/*

*.pyc
.venv
```

Migrate global attributes file: how git interprets files :information_source:

```shell
git config --global core.attributesFile
mv ~/.gitattributes ~/.config/git/attributes
git config --global --unset core.excludesFile
```

## Interactions with git config :martial_arts_uniform:

```shell
git config --global user.name # for reading
git config --global user.name 'GreatBahram' # setting/updating
git config --global -e # edit it
```

## Where are you coming from :open_mouth:

```shell
git config --list --show-scope # to see the scope of the system/global/local
git config --list --show-origin # from which file this value has been set
```

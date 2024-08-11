# 03 - Backup Git Configuration

**Objectives**

- How to backup your git configuration :eyes:
- Restore it like a charm :muscle:

## Backup

  ```shell
  mkdir config
  mv ~/.config/git config/git
  
  touch setup.sh
  chmod u+x setup.sh
  ```

  ```shell
  #!/bin/sh
  # Enable shell script strictness
  set -eu
  # Enable command tracing
  set -x
  # Ensure config directory exists
  mkdir -p ~/.config
  # Link Git config if it doesn’t exist
  [ ! -e ~/.config/git ] && ln -s "$PWD/config/git" ~/.config/git
  ```

  ```shell
  git add *
  git commit 'Init commit'
  
  git push
  ```

## Restore

```shell
./setup.sh
```


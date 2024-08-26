# Ignore File

Let's review some patterns with git ignore file:

- Lines starting with `#` are comments which also have no effect.

- The directory separator is always `/`

- Patterns that end with `/` match only directories. All other patterns match both files and directories.

- <u>Patterns that start with `/`</u>, or use / in the middle, are relative to the location of the `.gitignore` file.

- `*` matches zero or more characters, for instance:

  - `*.pyc` ignores all files.

- A `!` prefix negates a pattern.

  ```shell
  *.json
  !config.json
  ```

> [!NOTE]
>
> If you need a template for starting your git ignore file [a good starting point](https://github.com/github/gitignore/blob/main/Python.gitignore) 

## Track an empty directory:

There are two approaches to track an empty directories

First, using `.gitignore` file:

```shell
mkdir scratch
echo '*\n!.gitignore' > scratch/.gitignore
git add scratch
git commit -m "Add scratch directory"
```
Other approach, utilises the `.gitkeep`:
```shell
mkdir scratch
touch scratch/.gitkeep
```

> [!NOTE]
>
> You'll see the first approach more often!

## Debugging ignore files

In case you're looking for all ignored files, you can use the following command:

```shell
git status --ignored=matching
```

In case you want to check whether a file is ignored, use the following command:

```shell
git check-ignore .venv another_file

git check-ignore .venv -v
```

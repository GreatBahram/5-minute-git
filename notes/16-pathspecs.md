### Pathspecs

Many Git commands can work on only selected files, such as `git add`, `git diff`, and `git 
restore`. To pick which files to act on, pass such commands one or more pathspecs (path specifications).

Let's look at a few of them:

- `.` current directory
- `..` the parent directory

- `*.py`
- `*feature*`

- `:/`: "from root", tells Git to interpret the pathspec relative to the repository root.

  ```shell
  git add :/main.txt
  ```

- `:!`: to exclude, inverts a pathspec, so it will ignore matched paths. Great for filtering out files that you don’t care about right now.

  ```shell
  git add . :!picture.png :!translation.mo
  ```


#### Using pathspecs

Deploy the double-dash separator to avoid ambiguity. Sometimes arguments could be interpreted as either pathspecs or another type, like a branch name.

To diff the file, put a `--` before its pathspec:

```shell
git diff -- backend
```

To diff the branch, put a -- after the branch name:

```shell
git diff backend --
```
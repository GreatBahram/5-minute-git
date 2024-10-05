# Reflog

reflog is short for reference log, and it keeps track of all the commits you've made. It records every change to the commit history, such as commits, branch switches, rebases, and more.

Even if a commit becomes unreachable, like those from deleted branches, reflog can help you find them.

You can say "this is your 'oops' button in Git."

## How to use it

```shell
git reflog [branch-name]
git reflog --date=relative
```

Example output

```shell
59ab125 (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: commit: swarp 23 and 24 ;)
4be16fa HEAD@{1}: commit: create new
43ca319 HEAD@{2}: reset: moving to @~
592dade HEAD@{3}: reset: moving to 592dade3a736a621185ba3bdbb7231e
592dade HEAD@{4}: pull: Fast-forward
43ca319 HEAD@{5}: commit: add notes for the git restore
751a24d (feature-d) HEAD@{22}: commit: add bahram file
```

Each line in the reflog represents an entry with <u>three key parts</u>:

- A short SHA for the corresponding commit.
  - If a branch or tag currently points to that commit, it’s displayed in parentheses, like (feature-d).
- `HEAD@{<n>}` references, which serve as alternate names for the commits.
- A descriptive text explaining what change occurred.



> [!NOTE]
>
> You can also search for a specific commit message using `git reflog --grep 'bahram'`, or use the `-S` option to search within the content of the files.

> [!warning]
>
> `reflog` entries have an expiry date, which by default is set to 90 days

## Let's dive in and get our hands dirty! 😍

### restore a deleted branch

```shell
git switch --create alaki
git branch -D alaki 
```

OMG! What can we do now🙀🙀🙀

```shell
git reflog # find the commit of the branch
git branch alaki commit_goes_here
```

### undo a commit amendment

```shell
touch bahram
git add bahram
git commit -m 'add bahram file'
```

```shell
echo 'content' > bahram
# amend the previous commit and append the content to it 🤷‍
git add . && git commit --amend --no-edit
```

how to get back to the commit that we introduced the bahram file, not the content? You got it right, using reflog!

```shell
git reflog # find the sha of the commit
git reset --hard commit_goes_here
```

In case you want to have the content, easy easy tamam tamam

```shell
git restore -s commit_goes_here bahram
```

### undo a rebase

- add bahram file
- add content to it in a separate commit
- then use interactive rebase to squash them together
- now, let's get back to the point before the rebase operation
- I'll leave this to you!




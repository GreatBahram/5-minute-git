# Tidy up your local repository 🧹

Github/Gitlab will remove remote branches after being merged with the main brach. But you need to do this for your local repository.

There are two areas that we need to fix them:

- First, after a branch merges with main branch, our local copy still refers to the remote branch, while there is no branch not anymore!
- Secondly, as we said the git host, will remove these branches, but who is going to remove ours? no one :disappointed:. Since git removes no data by default.

## Addressing the first issue

This is easy, if we just pass `-p/--prune` to git fetch, everything will be fixed:

```shell
git fetch -p
```

There must be a better way, right :wink:

```shell
git config --global fetch.prune true
```

## Fixing the second problem

We first need to gather a list of all of these branches:

```shell
git branch --format '%(refname:short) %(upstream:track)'
```

In you case in you're in a big repo, you might be lucky and see a line like this

```
...
kaizen-update-restore-truncate-sub-commands [gone]
....
```

any lines contain "gone", should be deleted from our local repository. Let's filter the output:

```shell
git branch --format '%(refname:short) %(upstream:track)' | awk '$2 == "[gone]" {print $1}'
```

Now, all is left is to remove them

```shell
git branch --format '%(refname:short) %(upstream:track)' | awk '$2 == "[gone]" {print $1}' | xargs -r git branch -D 
```

Let's create an alias for this:

```ini
[alias]
...
    rm-merged = !git branch --format '%(refname:short) %(upstream:track)' | awk '$2 == \"[gone]\" {print $1}' | xargs -r git branch -D
```

## A new workflow

In addition, let's introduce a new alias

```ini
[alias]
...
	sync = git switch main && git pull & git rm-merged
```

From now on, you should use `git sync` to keep you repository in sync, no need to run git fetch or pull :tada:

This command will put the latest changes and remove the branches that have been merged with the main branch for us.




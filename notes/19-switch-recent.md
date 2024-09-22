# Switch between branches easily using fzf

Previously we learnt how to order the list of git branches by utilising the `--sort` option, however, we can enhance that a bit more :heart_eyes:.

Imagine there was a tool we could have throw our list of branches in it and then it shows us a nice UI in the terminal and after search for it, it would have run the `git switch` on the selected branch for us, sounds cool, doesn't it?

## fzf

There is this tool call `fzf` that takes a list of items, shows a small terminal UI for selecting an item, and outputs the selection.

Let's test it together:

```shell
echo "1 2 3" | tr ' ' '\n' | fzf
```

What we want to do is throw list of branches into fzf, but git by default shows '*' next to the current branch, so we need to remove:

```shell
git branch --sort -commiterdate --format '%(refname:short)' | fzf
```

We can make this looks even nicer, using a feature fzf called preview, to show what has changed in that branches in comparison to master/main branch:

```shell
git branch --sort -commiterdate --format '%(refname:short)' | fzf --preview='git log --color --date relative main..{}'
```



Finally, we just need to switch to that branch :man_shrugging:

```shell
git branch --sort -commiterdate --format '%(refname:short)' | fzf --preview='git log --color --date relative main..{}' | xargs git switch
```

Don't forget to save this as an alias in git:

```ini
[alias]
....
   switch-recent = !git branch --sort=-committerdate --format='%(refname:short)' | fzf --preview='git log --date=relative --color main..{}' | xargs git switch

```


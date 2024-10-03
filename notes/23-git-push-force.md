# Safer Force Pushing with Git

The `git push` command allows you to send local commits to a remote repository. However, when using `--force`, you risk overwriting others' changes on the remote branch. Git offers safer alternatives like `--force-with-lease` and `--force-if-includes` to mitigate this risk.

- What is `--force-with-lease`? The `--force-with-lease` option checks whether someone has updated the remote branch since your last fetch. If new commits have been added, your force-push will be rejected to avoid overwriting them.

- What is `--force-if-includes`? The `--force-if-includes` option adds an extra layer of protection. It ensures that you have fetched and **checked out the latest commit** from the remote branch, typically via a `git pull`, before you can force-push.

```bash
git push --force-with-lease --force-if-includes
gpf

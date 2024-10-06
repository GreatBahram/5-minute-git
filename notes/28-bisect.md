# Bisect

`git bisect` is an efficient tool for identifying the commit responsible for introducing a specific issue or behavior change.

When tracking down commits that caused a previously working feature to break, `git bisect` excels by significantly reducing the number of commits you need to check manually.

The term "bisect" comes from the binary search algorithm, which is the foundation of this tool. The search process repeatedly divides the commit history in half, or "bisects," until it identifies the problematic commit.

As you may know, binary search is much faster than linear search, which involves checking each commit one by one.

| History length | Tested by binary search |
| -------------- | ----------------------- |
| 10             | 4                       |
| 100            | 7                       |
| 1000           | 10                      |
| 10000          | 14                      |

## Let's dive in

This is the list of all commands you need to know about them:

| Subcommand         | Purpose                                        |
| ------------------ | ---------------------------------------------- |
| `git bisect start` | Initialize a bisect session.                   |
| `git bisect old`   | Mark a commit as exhibiting the old behaviour. |
| `git bisect new`   | Mark a commit as exhibiting the new behaviour. |
| `git bisect reset` | End the bisect session.                        |

### How to Begin?

Typically, you start the process by running `git bisect start` without any arguments, indicating that the current (latest) commit contains the issue you're investigating.

Next, Git will prompt you to specify a commit where the issue was not present, or where the desired behavior (referred to as the "old behavior") was observed. This can be done with the command: `git bisect old <commit-id>`.

At this point, Git will begin its binary search, checking out a commit halfway between the known good (old) and known bad (new) commits.

Git will then prompt you to determine if the current commit exhibits the "**old**" or "**new**" behavior:

- New behavior refers to the undesired behavior you're trying to isolate.
- Old behavior is the functioning, correct state.

Once the issue has been narrowed down to a specific commit, you can end the bisect session by running `git bisect reset`, which returns the repository to its original state.
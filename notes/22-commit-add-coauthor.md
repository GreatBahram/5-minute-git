# Git Commit Add Co-Author

When collaborating on a commit with a team member, it’s important to acknowledge their contributions. Git offers a way to do this in commit messages through the `co-authored-by` trailer.

These trailers are structured metadata placed at the end of a commit message.

They follow the `<key>: <value>` format and should be included as the last lines of the commit message.

## Steps to Add a Co-Author in Git

1. **Get your colleague’s name and email:**

   - Use the following command to find it:

     ```shell
     git log --author Bahram
     ```

2. **Add the co-author to your commit:**

   - Run this command with your colleague’s details:

     ```shell
     git commit -m 'commit message' --trailer 'Co-authored-by: Bahram Aghaei <aghaee.bahram@gmail.com>'
     ```

     
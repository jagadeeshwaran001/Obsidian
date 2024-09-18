
The `git checkout` command is used in [[git]] to switch between different branches or to restore files in your working directory.

`git checkout <branch-name>` to ==switch the branch==

`git checkout -b new-branch` to create a ==new branch==.

`git checkout <commit-hash> -- <file-path>` to restore specific files to the previous state for specific commit or branch.

### Important Notes

- **Detached HEAD State**: If you check out a commit that isn’t the tip of a branch, you’ll enter a "detached HEAD" state, meaning you're no longer on any branch.
- **Replacement**: As of Git 2.23, `git switch` and `git restore` were introduced as more user-friendly alternatives for switching branches and restoring files, respectively.
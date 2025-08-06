# LazyGit Features: A 15-Minute Overview

This video demonstrates 15 useful features of the LazyGit program, aiming to improve users' Git workflow efficiency.  The presenter showcases various functionalities within the application, highlighting keyboard shortcuts and practical applications.

## Staging Files and Lines

* **[00:00:18]** Staging multiple files quickly:  Use arrow keys to select modified files and press `Space` to stage them.  Alternatively, press `a` to stage all modified files.
* **[00:00:44]** Staging individual lines: Press `Enter` on a file, then use `Space` to stage individual lines within that file.  Use `v` to select a range of lines, `d` to unstage lines, or `D` to delete lines.


## Branching and Cherry-Picking

* **[00:01:26]** Cherry-picking commits: Use `c` to cherry-pick a commit from one branch to another.
* **[00:01:41]** Moving commits between branches: Press `b` to move cherry-picked commits to a different branch.


## Discarding Changes

* **[00:01:52]** Discarding file changes: Press `d` to discard changes in a specific file.
* **[00:02:04]** Discarding all changes: Press `Shift + d` for options including `reset`, `hard reset`, and nuking the working tree to remove all changes.


## Interactive Rebasing

* **[00:02:20]** Starting interactive rebase: Navigate to the commits panel and press `e` to initiate an interactive rebase.
* **[00:02:36]**  Modifying commits during interactive rebase: Change commit actions (e.g., `pick`, `squash`, `edit`, `fixup`) using the corresponding keys. Use `m` to save changes and continue the rebase.
* **[00:03:03]** Moving commits: Use `Ctrl + j` and `Ctrl + k` to reorder commits during interactive rebase.
* **[00:03:14]** Amending commits: Use `Shift + a` to amend a commit with changes from the working tree.
* **[00:03:37]** Fixing up commits: Use `Shift + f` to fix up one commit on top of another.
* **[00:04:00]** Squashing commits: Use `Shift + s` to squash multiple commits together.


## Pull Requests and Reverts

* **[00:04:16]** Opening pull requests: Press `o` to open a pull request in your browser.
* **[00:04:35]** Reverting commits: Press `t` to revert a commit.


## Stashing Changes

* **[00:04:49]** Selective stashing: Press `Shift + s` to stash only staged changes.


## Patching and Editing Old Commits

* **[00:05:07]**  Creating and moving patches: Press `Enter` to view commit files, select lines to create a patch, and use `Ctrl + p` to move the patch to a different commit.
* **[00:05:52]** Resolving merge conflicts during patch application:  LazyGit handles merge conflicts when applying patches that modify the same lines in different commits.


## Rebasing onto Origin/Master

* **[00:06:16]** Easy rebasing: Press `f` to fetch changes from `origin/master`, then press `r` to rebase onto it.


## Switching Branches without Stashing

* **[00:06:46]**  Switching branches with uncommitted changes: LazyGit automatically handles potential merge conflicts when switching branches, eliminating the need to stash changes.


## Changing the Color Theme

* **[00:07:17]**  Customizing the color theme:  The video briefly shows how to modify the color theme in LazyGit's settings.

## Conclusion

* **[00:07:36]** The video concludes by summarizing the demonstrated features and encouraging viewers to use them in their workflows.  The presenter also invites questions in the comments.

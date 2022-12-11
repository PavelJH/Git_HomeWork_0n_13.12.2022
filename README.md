1.	Undo operations = $ git commit --amend 
for example
$ git commit -m 'Initial commit'
$ git add forgotten_file
$ git commit –amend

Cancel file indexing
$ git add *
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
    modified:   CONTRIBUTING.md
$ git reset HEAD CONTRIBUTING.md
Unstaged changes after reset:
M	CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
Отмена изменений в файле
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
$ git checkout -- CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
Undoing actions with git restore
$ git add *
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   CONTRIBUTING.md
	renamed:    README.md -> README
$ git restore --staged CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   CONTRIBUTING.md
2.	For example, name of commit = 3f25701874aa5a2c16cc6275fa30baa5b6e477a6
You need give a command = git checkout 3f25701874aa5a2c16cc6275fa30baa5b6e477a6 <name_file>
You need chose previous commit, HEAD-1
Example = git checkout 3f25701874aa5a2c16cc6275fa30baa5b6e477a6 doc/text.html
3.	git commit --amend
git reset HEAD~ # remove only the commit
git reset --hard HEAD~ # remove the commit and changes

and to undo the changes made in the last commit, you can:
git revert aa600a43cb164408e4ad87d216bc679d097f1a6c
# we need to pass it the hash of the commit we are reverting
4.	git checkout -b mybranch
5.	Git merge allows us to perform fast-forward and no fast-forward branch merging.
The --no-ff option is useful when you want to have a clear notion of your feature branch. So even if in the meantime no commits were made, FF is possible - you still want sometimes to have each commit in the mainline correspond to one feature. So you treat a feature branch with a bunch of commits as a single unit, and merge them as a single unit. 
5.1. A conflict during a merge can occur at two separate points - at startup and during the merge process.
Git breaks at the very beginning of a merge
The merge command is aborted at the very beginning if Git detects changes in the current project's working directory or indexed files section. Git cannot merge because these pending changes will be overwritten by new commits. This happens because of conflicts not with other developers, but with pending local changes. The local state must be stabilized using the git stash, git checkout, git commit, or git reset commands. If the merge command is aborted at the very beginning, the following error message is issued:
error: Entry '<fileName>' not uptodate. Cannot merge. (Changes in working directory)

Git breaks during a merge
A failure IN THE Merge indicates that there is a conflict between the current local branch and the branch being merged from. This indicates a conflict with another developer's code. Git will do its best to merge files, but will leave conflicting areas for you to manually resolve. If the merge fails, the following error message is issued:
error: Entry '<fileName>' would be overwritten by merge. Cannot merge. (Changes in staging area)
6.	Yes. 
Deleting a local GIT branch
We have two way how delete:
git branch -d branch_name
or
git branch -D branch_name
The -d option means --delete, which will only delete the local branch if you merged it from one of the branches.
The -D option stands for --delete --force which deletes the branch regardless of its push or merge status.

Deleting a remote GIT branch
git push <remote_repository_name> --delete <branch_name>




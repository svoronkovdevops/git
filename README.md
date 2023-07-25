# Git

## Content

[Git help](#git-help)

[Git objects](#git-objects)

[Git config](#git-config)

[A new project](#a-new-project)

[Git branch](#git-branch)

[Git merge](#git-merge)

[Repo info](#repo-info)

[Git diff](#git-diff)

[Git blame](#git-blame)

[Git commit](#git-commit)

[Git reset](#git-reset)

[Git merge](#git-merge)

[Working with commits](#working-with-commitsmaking-changes)

[Restore deleted changes](#restore-deleted-changes)

[Git bisect](#git-bisect)

[Git stash](#git-stash)

[Git ignore](#git-ignore)

[Git tags](#git-tags)

[Git patch](#git-patch)

[Git show](#git-show)

[Git remove](#git-remove)

[Git move](#git-move)

## Git help

`git help command` show info 
`git help add` show info  about `add` command

[Content](#content)

## Git objects

- blob
- tree
- commit
- tag

[Content](#content)

## Git config

`git config --global` for current user

`git config --system` for all users

`git config --global user.name "username surname"` 
`git config --global user.email "@mail"`

`git config --list ` show current config

[Content](#content)

## A new project

`git init` init git in project folder

`git remote add name "https://github.com/name/project_name"` add remote repo

`git add --all` add all files to index

`git add --all`

`git add -p` show all changes(show the change being added and ask us if we want to stage it or not)

`git commit -m "Initial commit of the project"` commit changes

`git push name branch_name` push to remote `git push name master`

`git clone https://github.com/name/project_name` clone remote repo

`git mv company/Technology.java company/Skill.java` rename or move

[Content](#content)

## Git branch

`git branch <name>` create branch `git branch test` 

`git branch` show all branches in project
`*` show active branch (where we are now)

`git checkout test` switch to test branch

`git checkout -b new_branch` create new_branch and swich to it

` git branch -D new_branch ` remove new_branch

[Content](#content)

## Git merge
`git checkout master ` switch to master branch

`git merge new_branch ` merge new_branch to branch where we are

[Content](#content)


## Repo info

`git status` status

`git log` log info

`git show commit_number ` show info about commit_number `git show 11f75b`

`git remote` show remote repositories

`git remote add username https://github.com/username/repo_name` add remote repo

[Content](#content)

## Git diff

`git diff` show changes between commits work area and index(unstaged)

`git diff --staged` show changes between commits work area and index(staged)

`git diff master commit_hash`

[Content](#content)

## Git blame

`git blame <filename>` add annotation with strings changes

`git blame Main.java` 

[Content](#content)


## Git commit

- `git commit -a` ignore index
-  `git commit -a -m "added...` we can use without `git add` command when files already added to make faster commit without adding to stage
- `git commit -m "added style"` create commit without opening redactor(nano, wordpad and etc)
- `git commit --amend` (--no-edit) reset commit throught `reset`and create a new commit


[Content](#content)


## Git reset

- `git reset` move brunch where cursor HEAD
- `git reset --soft HEAD-1` reset a commit but save changes
- `git reset --hard HEAD-1` reset the last commit and changes
`git reset --hard ` remove all changes

[Content](#content)

## Git merge

- `git cherry-pick commit_hash` move info from commit

- `git cherry-pick --continue` when conflict we fix then `git add .` and use `continue` option

- `git merge branch_name` merge branch into current branch

- `git merge --continue` when conflict we fix then `git add .` and use `continue` option
- `git rebase master` replace master branch by current

- `git rebase--continue` when conflict we fix then `git add .` and use `continue` option

- danger option `force`

[Content](#content)

## Working with commits(making changes)

1. Connect two commmits

 `git rebase -i HEAD~2` make from 2 latest commits one
(change second `pick` to `squash`(delete commit marked as squash and save the message from the commit wich market as pick) or `fixup`(delete commit marked as fixup and save the message which you'll write or choose in redactor))

`git rebase --continue` to end operation

2. make changes to the old commit

`git rebase -i HEAD~3` using edit option and chose commit then write `edit` then making changes in file -> then `git add .` -> then `git rebase --continue`

3. undo changes from 2 last commits

`git revert HEAD~2..`

`git revert commit_hash`

[Content](#content)


## Restore deleted changes 

1. `git reflog` or `git log -g`
find changes
2. `git reset --hard master@{"15 minutes ago"}`
return changes 15 min before
3. `git fsck --full` 
check inner base

[Content](#content)

## Git bisect

- `git bisect start HEAD 46f2bf` run binary search bad commit between points 
`git bisect start first_commit last_commit` first_commit and last_commit are our points

-> then we check our build and mark as good or bad or stop when end check
- `git bisect good` mark commit as normal

- `git bisect bad` mark commit as potentially bad
- `git bisect reset` end check and returns head

[Content](#content)

## Git stash

- `git stash` save changes in independ storage
`git stash save “some message”` we can also add message

- `git stash list`
- `git stash pop (stash@{2})` apply earlier changes and remove them from temp storage

- `git stash apply (stash@{2})` apply earlier changes without removing them from temp storage

- `git stash drop stash@{1}`
- `git stash clear`

[Content](#content)

## Git ignore

```
*.class  ===compiled classes
#mobile tools
.mtj.tmp/
#package files
*.jar
*.war
*.ear
#virtual mashine crash logs
hs err pid*
*.iml  
.idea /*  

# Folders
.idea/*
out/*

# Files
*.class

```
[Content](#content)

## Git tags

`git tag -a 'Version1.0' -m "Initial valid version of the project"` create tag `Version1.0` with commit "Initial valid version of the project"

`git push  repo_name Version1.0` - push `Version1.0`

`git show Version1.0 ` show tag `Version1.0`

`git tag -d 'Version1.0'` delete tag

[Content](#content)

## Git patch

`git add --all`
`git commit -m "Adding methods to class Developer"`

`git format-patch -1` create patch
 
`git apply 0001-Adding-methods-to-class-Develope.patch`

```sh
~$ cat hello_world.txt 
Hello World
~$ cat hello_world_long.txt 
Hello World

It's a wonderful day!
~$ diff -u hello_world.txt hello_world_long.txt 
--- hello_world.txt     2019-12-16 19:24:12.556102821 +0900
+++ hello_world_long.txt        2019-12-16 19:24:38.944207773 +0900
@@ -1 +1,3 @@
 Hello World
+
+It's a wonderful day!
~$ diff -u hello_world.txt hello_world_long.txt > hello_world.diff
~$ patch < hello_world.diff 
patching file hello_world.txt
~$ cat hello_world.txt 
Hello World

It's a wonderful day!
```
[Content](#content)

## Git show

`git show <commint_hash>` - show info

[Content](#content)

## Git remove

`git rm <filename>` - remove file

[Content](#content)

## Git move

`git mv <filename> <new_filename>` rename as in linux system

[Content](#content)

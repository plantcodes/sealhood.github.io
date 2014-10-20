---
#Git basic
1. local working directory
2. stage area
3. local repository
4. remote repository

From `1` to `2` execute `git add`

From `2` to `3` execute `git commit -m`

From `3` to `4` execute `git push`

From `4` to `1` execute `git clone | git fetch`

From `1` to `3` execute `git commit -a -m`

---
#Firt-Time git setup
    git config --global user.name sealhood
    git config --global user.name sealhood@gmail.com
---
#Getting up git repository
##Initializing a repository in an existing directory
    git init
    git add a.c
    git commit -m "hello"
    
##Cloning an existing repository
`git clone https://github.com/sealhood/sealhood.github.io.git`

---
#Recording changes to repository
##File status lifecycle
* untracked `git add / git rm`
* unmodified `after git commit `
* modified 
* staged `git add`

Using `git status` to checking  status of files

Using `git add` to tracking a file

Using `git add` to stage a modified file

##Ignoring files
File `.gitignore` list file not want git automatically add 
or not showed being untracked
* `Blank lines` or lines starting with` # `are ignored.
* Standard global patterns work.`*`
* You can end patterns with a` forward slash (/) `to specify a directory
* You can negate a pattern by starting it with an` exclamation point (!)`

##Skipping staging area files
`git commit -a -m 'message'` this command automatically stage every tracked file
##Removing files
Using `rm file` to remove file form working directory
Using `git rm` to update removing operation to stage area
Using `git commit` to remove file from local repository
`git rm -cached file` remove file from stage area not working directory

##Renaming files
`git mv file.old file.new`

##Undoing things
###Changing last commit
`git commit -amend` 
modifications in last commit and after last commit is merge as a new commit
###Unstaging a staged file
`git reset HEAD file`
###Unmodify an modified file
`git checkout -- file`

---
#Working with Remote (repository)
`git remote` shows all remote repositories

`git remote -v` shows all remote repositories with URL

`git remote add remote-repository-name-in-local URL`

eg.`git remote add pb git://github.com/pualboone/ticgit.git`

`git fetch pb` fetch all information pb have but you don't have in your local repository

`git push remote-name branch-name` eg. `git push origin mater`

`git remote show remote-name` 

`git remote rename rep-name.old rep-name.new`

`git remote rm rep-name`

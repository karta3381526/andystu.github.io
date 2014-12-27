---
layout: post
title: "git usage notes"
date: 2014-12-23 16:11:10 +0800
comments: true
categories: git
---
## Install git via homebrew
$ brew install git # If we want to use gitk (git GUI), this way is very convinient. (however, I think SourceTree is better.)

## Git work processes
- sign up a github account
- create a repos (repository) with a "name"
- then git it
``` bash
# rails project
$ rails new app
$ cd app
$ git init
$ git add .
$ git commit -m 'first commit'  

$ git commit -am 'xxxx' # == git add . + git commit -m 'xxxx'

$ git checkout -b branch_name

# do some changes under this branch ...  

$ git add .
$ git commit -am 'some thing in this brach'

# go back to master and merge it

$ git checkout master
$ git merge branch_name

# push to github 

$ git remote add origin repos_git_ssh_url
$ git push --all # both master and branches
$ git push origin master # you also can push master to remote only

# reset or revert to HEAD version (HEAD refers to latest commit stage)

$ git reset HEAD --hard # --hard is dangerous (delete unstaged files)
$ git reset HEAD --soft # --soft will go back and keep files staged 
$ git reset HEAD # will go back without tracking unstaged files
$ git revert HEAD # make HEAD stage as new stage

# reset one file

$ git checkout -- <file>

# conflick of rebase (merge is the same)

$ git rebase master # under second branch
# conflick ...
# modify conflick <file>
# then 
$ git add <file>
$ git rebase --continue
# done.
```


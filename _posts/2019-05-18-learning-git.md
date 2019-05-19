---
layout: post
title: Learning git
date: 2019-05-18 23:58 -0400
---
Version control is very important and usefull tool for developers.
In this post, I will talk about  important git commands that are used most of the time.
# 1) git config
Use --> To set your user name and email in the main configuration file.

Command : type in git config --global user.name "username" and git config --global user.email youremail@example.com

# 2) git init
Use --> To initialise a git repository for a new or existing project.

Command : git init in the root of your project directory.

# 3) git clone
Use --> To copy a git repository from remote source, also sets the remote to original source so that you can pull again.

Command : git clone <:clone git url:>

# 4) git status
Use --> To check the status of files you’ve changed in your working directory, i.e, what all has changed since your last commit.

Command : git status in your working directory. lists out all the files that have been changed.

# 5) git add
Use -->  adds changes to stage/index in your working directory.

Command : git add .

# 6) git commit
Use -->  commits your changes and sets it to new commit object for your remote.

Command : git commit -m”sweet little commit message”

# 7) git push/git pull
Use -->  Push or Pull your changes to remote. If you have added and committed your changes and you want to push them. Or if your remote has updated and you want those latest changes.

Command : git pull <:remote:> <:branch:> and git push <:remote:> <:branch:>

# 8) git branch
Use --> Lists out all the branches. 

Command : git branch or git branch -a to list all the remote branches as well.

# 9) git checkout
Use --> Switch to different branches.

Command : git checkout <:branch:> or **_git checkout -b <:branch:> if you want to create and switch to a new branch.

# 10) git stash
Use --> Save changes that you don’t want to commit immediately.

Command : git stash in your working directory. git stash apply if you want to bring your saved changes back.

# 11) git merge
Use --> Merge two branches you were working on.

Command : Switch to branch you want to merge everything in. git merge <:branch_you_want_to_merge:>

# 12) git reset
Use --> You know when you commit changes that are not complete, this sets your index to the latest commit that you want to work on with.

Command  : git reset <:mode:> <:COMMIT:>

# 13) git remote
Use-->  To check what remote/source you have or add a new remote.

Command : git remote  to check and list. And git remote add <:remote_url:>

These are the most essential git commands. 
---
layout: post
current: post
cover: assets/images/git-n-github.png
navigation: True
title: Getting Started With Git And GitHub 🐙
date: 2020-05-06 12:00:00
tags: guide
class: post-template
subclass: 'post tag-guide'
logo: assets/images/logo.png
author: majordwarf
---

# Introduction To Git and GitHub

Git is the most popular software to maintain multiple versions of your code and is one of the tools essential for software development in the industry. On the other hand, GitHub is a code hosting platform for collaboration and version control. This is a tool without which you don't want to be.

---
## What is Git?

Considering you are a complete outsider, imagine you and your friends are working on a research paper. You start writing the introduction in a word file, now one of your friends enters the room and says, "Hey, I got some new research data that could improve our paper!" So, now he continues writing on the same document on the same laptop. Now after weeks of such collaboration and multiple changes by friends, you find some inconsistencies in the paper, and you don't remember who made which changes.

Collaborating in such an environment can cause issues to imagine the same case in the world of software development, where multiple files are being changed continuously by different programmers and that too simultaneously! This is where a Version Control System (VCS) comes into the play it provides features such as collaboration between different users, managing different versions of the source code, keeping track of all the changes, who did it, when, and why.

Git isn't the only VCS out there but is one of the widely used and is a distributed version control system. The "distributed" part refers to the section that allows users to collaborate on the same project on the different system remotely irrespective of their operating system.

---
## Installing Git

Git comes installed by default on many systems. If you don’t already have it:

- You can download the Git Command Line Interface (CLI) from their [official website](https://git-scm.com/downloads), which is one of the recommended ways for both new and advance users.
- You can also download the GUI Client from their [official website](https://desktop.github.com/) too, but currently, it's only available for Windows and macOS.
- [Git Kraken](https://www.gitkraken.com/git-client) is one of the third-party GUI Client that is recommended widely.

---
## Setting Up Git

Once git is installed on your system, you need to check if it's working correctly. That can be done typing the following command in the Git Bash(Windows) or inside the Terminal (UNIX/Linux): 
```console
$ git --version
git version 2.20.1 // Latest version during the time of writing this article.
``` 
If the above command doesn't return a version number probably git isn't installed correctly on your system.

After git is set-up properly, it's time to set-up your username and email id for git to use system-wide. Remember how git keeps the log of who made the changes? This username and email you'll provide now will be used to sign every commit made by you. These need to be the same as your GitHub username and email id to keep track of all the contributions you do on GitHub. You can set-up your username and email as follow:
```console
$ git config --global user.name <username>
$ git config --global user.email <email>
```
Did you notice the `--global` argument above? That states that you want that username and email to be used for any future commit you made on any git repository on the system.

If you want to override the following information for a particular repository, just `cd` used into that repository and perform the same command eliminating the `--global` argument, and you're good to go!

---
## Commands
Now let's learn a few commands that we'll be using throughout our _WHOLE LIVES!_ 

> Make your repository

```
Command: git init
```

The following folder will create a hidden .git folder inside the current working directory that will track all the changes made to any file inside this folder -this is the "repository" (or repo) where git stores all of its internal tracking data. You neither will interact with the following folder nor will delete it. Any existing project or even an empty project can be turned into a git repository.

> Forking someone's repository

You don't have write access to someone's repository on GitHub. Forks are the way of getting a copy of the latest code under your GitHub id so you can write new changes to it and modify it as you need.

> Clone a repository

```
Command: git clone <url>
```

That will download the latest git repository from the specified URL on your local system. A folder with the same name as the repository will be created, and all the data will be fetched inside this directory.

When you clone a repository, the source from where you got the repository will be added as the remote origin. We'll look into what remotes are soon!

> Check status of your project

```
Command: git status
```

This will show the current status of the project, like how many commits we are ahead of remotes, which files are modified, which files are tracked and other basic information. If you are confused at some point in whether you changed something by mistake, you can always check the status of the project.

> Branching out stuff!

```
Commands: 
git branch // To list all the branches in current repo
git branch <branch_name> // Creates a branch with the specified name
git branch -d <branch_name> // Deletes the branch specified if it exists
git checkout <branch_name> // Switch to the branch specified

git checkout -b <branch_name> // Creates a new branch and switches to it automatically
```
Branches, as the name suggests, creates a new branch of your code that is separate from your master branch, so you can write and test all the experimental features you need in your app with messing with the stable version of your code. Once everything seems working fine, you can merge these new features into the master branch avoiding all the paths in which your user would have faced some app crash.

Branches are generally used to fix bugs, add new features, test something experimental. So, even if anything goes wrong, you can delete the branch or reset it to the old working version, i.e.- master branch. When you list all the branches using the `git branch` command, the branch with `*` (asterisk) in front of its name states the current branch.

> Stage your changes

```
Commands:
git add <filename> // To track a particular file
git add * // To track all the new and modified files
```
Git doesn't know which files you want to include in the next version/commit of your code. So after making the changes and before telling git to make a new checkpoint, you need to tell it which files you want to include in the "stagging" area (or "ready to be committed").

After stagging some changes, if you go and make new changes even to the same files, the new changes won't be tracked. This is useful to make sure what you're committing and not including. If confused, which files are tracked and which aren't you can check the status of the repository. Files to be committed will be displayed in "green" and files which aren't being tracked will be displayed in "red" color.

> Committing your staged changes

```
Commands:
git commit // To write a commit with a multiline message
git commit -m "<message>" // To write a small commit message
```
So once you've made changes to the project you need, you'll need to make sure that changes are stored permanently as a checkpoint. The following is done by committing the staged changes using the commit command. You'll also need to pass a message along with the commit so you or someone else collaborating on the project can come to know what changes were made and why.

Each commits automatically stores data like the username and email of the person who made the changes, timestamp, and message of the commit and assigns it a unique hashed string. 

> Remotes

```
Commands:
git remote -v // Lists all remote with their endpoint url
git remote add <remote_name> <url> // Adds the URL as a new remote with the specified name to that repository
```

So remotes are the place where you want to pull the changes or even push your latest changes. So whenever you make some change to someone else's repository using a branch and that changes are merged in his master branch, your local master branch is not in sync with the latest update. You can update your local code by pulling the changes from the master branch of that remote.

Remotes are also used to test changes from someone's changes. Suppose someone made a fork of your code and is working on some new feature, in case you want to experiment that changes, you add that repository as a new remote and pull the changes or branch locally to test them. In short, remotes can be explained as endpoints to keeping code in sync.

If you make a new repository and want to upload the code to GitHub, create an empty repository on GitHub, add the URL of that repository as a remote, and then push the changes. 

> Pushing the changes somewhere

```
Command: git push <remote_name> <branch_name>
```

Pushing changes uploads your changes of a branch to the remote you specified to keep your code on the server/GitHub up-to-date.

After pushing the changes successfully, your team members will be able to pull the latest changes locally on their system.

> Getting the latest changes

```
Commands:
git fetch --all // Fetches all the latest changes and branches from all the remotes
git pull <remote_name> <branch_name> // Fetches the latest changes from the branch of specified remote
```

The `git fetch` command fetches all the changes from remotes that are specified and store all the updates in `.git` folder but you'll still be on the checkpoint you were earlier. You'll need to merge all the latest changes or the branch you need manually.

To avoid this, use the `git pull` command that fetches and merges the changes all in one step. So `git pull origin master` will pull the changes that exist in the "master" branch of the remote "origin" and merge it into the current local branch you're on.

> Conflicts!

Suppose you try to pull some changes from a remote and there are some changes made by someone on the same line as you on the same file this will cause a merge conflict as git isn't that smart to know what changes are right for the code. In this case, git asks you to choose what is right and make a new commit. Once there is a conflict, the conflict causing file modified by git and waits for a commit.

Content of conflicting file looks like this:
```cpp
>>>>>>> HEAD
int a = 5;
int b = 10;
=======
int a = 10
int b = 5;
<<<<<<< 384dcc1ac63b820c34684354896737ed1ae3f7f6
cout<<a+b;
```

Here everything between `>>>>>>> HEAD` and `=======` are the changes made by you and everything between `=======` and `<<<<<<< 384dcc1ac63b820c34684354896737ed1ae3f7f6` (the random string is the commit id of the remote change) is the change that existed on the remote. Suppose you want your local change to be the final change then you'll erase the other content that was generated by git, the final file will look like this,
```cpp
int a = 5;
int b = 10;
cout<<a+b;
```

Now you'll track the file you just changed and make a new commit stating a suitable message, e.g.-
```
git add *
git commit -m "Fix merge conflict"
```
---

Now you know everything you'll ever need to begin and contribute to open-source or even start working on your next big project and maintaining it's code! There are some other small things that we'll be covering in future workshops. If you want to practice what you have learned today, we've made three small tasks - [here](https://github.com/devclub-workshops/Git-Workshop-Tasks)

Hope you had fun and learnt something cool!

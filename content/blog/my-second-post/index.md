---
title: Introduction To Git, Basics Commands, And Terminology
date: "2022-03-12"
description: A simple introduction to Git and basic commands using the CLI.
---

## Introduction

If you are just getting started on your programming journey, you will soon realize that you will constantly find yourself cloning, adding files, committing changes, and much more. You also might be asking yourself, "what do those words mean!?", no worries! I'll be giving an short introduction to what they mean what's possible with Git!

## What's the difference?

You might be asking yourself, "wait, this doesn't look like GitHub!", and you're right. Git is a version control system. GitHub is a cloud-based hosting service.

A **version control system** is software that helps you control (or manage) the different versions of something, in our it's source code.

A **cloud-based hosting service** is a platform that hosts infrastructures, platforms, or software by third-party providers. GitHub is a code hosting platform for version control and collaboration.

Git is a version control tool.

GitHub is a service that hosts Git projects.

A source code manager (abbreviated as SCM) is another name for a version control system.

Git is a SCM, and therefore a version control system (abbreviated as VCS)! You can check out Git's website [here](https://git-scm.com/).
Notice how it has SCM directly in its domain.

## Version Control Systems

The main point of a version control system is to **help maintain a detailed history of the project as well as the ability to work on different version of it**. Having a detailed history of a project is important because it lets you see the progress of the project over time. If needed, you can also jump back to any point in the project to recover data or files. This is helpful because you can revert files back to a previous state, revert the entire project back to a previous state, review changes made over time, see who last modified something that might be causing a problem, who introduced an issue and when, and much more!

Since we are focusing on Git, we will go into version control systems. There are two types of version control system models:

- **The centralized model**:

  - All users connect to a central, master repository

- **The distributed model**:
  - Each user has the entire repository on their computer.

Git is a distributed version control system.

You actually use version control in your everyday life, kind of, and no I'm not talking about Git. When you're working with documents, like a Google Doc, you're sort of maintaining different versions of a document as you write it. You're not _actively_ maintaining the document, but you're computer is keeping track of the different version for you. Back to the Google Doc, have you ever noticed the small gray text at the top that tells you about the status of the document? Ever noticed that as you type, it's actively saving the document? Then, when you're finished typing, it tells you that the document has been saved. That's revision history, it's sort of like version control but it's not powerful enough.

What make version control a better option?

- The ability to label a change.
- The ability to give a detailed explanation of why a change was made.
- The ability to move between different versions of the same document.
- The ability to undo a change **A**, make edit **B**, then get back change **A** without affecting edit **B**.

## Installation

You can install Git on for the following systems:

- macOS
- Linux / Unix
- Windows

You can download Git [here](https://git-scm.com/downloads).

## Basic Git Commands

Once installed we will move to the command line interface (CLI). You can quickly access the CLI on the following systems:

- Terminal on macOS
- Terminal on Linux / Unix
- Command Prompt Windows

Let's verify that you've successfully installed Git with the following command.

```js
git --version
```

If successfully installed, Git will return the following message:

> git version **version_number**

If you don't receive this message, you try following the installation guide [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### Set your user name and email address.

```js
git config --global user.name "USERNAME"
git config --global user.email "EMAIL@EXAMPLE.COM"
```

#### To start a new local repository.

```js
git init
```

#### To add a file and to add more than one file.

```js
git add <filename or directory name>
git add .
```

#### Record the changes made to the files to a local repository with a message.

```js
git commit -m "Commit message in quotes."
```

#### Return the current state of the repository.

```js
git status
```

#### Create a local working copy of an existing remote repository.

```js
git clone <remote_URL>
```

#### Fetch and merge changes on the remote server to your working directory.

```js
git pull
```

#### Send changes to the master branch of your repository.

```js
git push origin master
```

#### Connect to a remote repository.

```js
git remote add origin <server>
```

#### List all currently configured repositories.

```js
git remote -v
```

#### Create a new branch and switch to it.

```js
git checkout -b <branchname>
```

#### Switch to another branch.

```js
git checkout <branchname>
```

#### Replace the changes in your working tree with the last content in head.

```js
git checkout -- <filename>
```

#### List the current branch you're in and the others in your repository.

```js
git branch
```

#### Delete a branch.

```js
git branch -d <branchname>
```

#### Merge a different branch into your active branch.

```js
git merge <branchname>
```

#### Push the branch to your remote repository so others can use it.

```js
git push origin <branchname>
```

#### Save changes made when they're not in a state to commit.

```js
git stash -u
```

## Terminology

**Commit**: Git thinks of its data like a set of snapshots. Every time you commit, it takes a 'picture' of what all your files look like at that moment and stores a reference to that snapshot. Each commit has a unique ID.

**Repository / Repo**: A repository is a directory which contains your project work, as well as a few files which are used to communicate with Git. Repositories can exist either locally on your computer or as a remote copy on another computer. A repository is made up of commits.

**Working Directory**: The working directory are the files that you see in your computer's file system. When you open your project files up on a code editor, you're working with files in the working directory.

**Checkout**: A checkout is when content in the repository has been copied to the working directory.

**Staging Area / Staging Index / Index**: A file in the Git directory that stores information about what will go into your next commit. You can think of the staging area as a prep table where Git will take the next commit. Files on the staging index are poised to be added to the repository.

**SHA**: SHA is short for "Secure Hash Algorithm". A SHA is a basically an ID number for each commit. Here's what a commit's SHA might look like:
`e2adf8ae3e2e4ed40add75cc44cf9d0a869afeb6`.
It is a 40 character string compose of characters (0-9 and a-f) and calculated based on the of a file or directory structure in Git.

**Branch**: A branch is when a new line of development is created that diverges from the main line of development can continue without altering the main line.

## Conclusion

Git is a very powerful tool for any developer, junior or senior. It helps maintain track of the progress you've made and even lets you go back to a specific point if any mistakes were made. Being able to use Git in your command line allows you to make significant changes to your remote repository with just a couple lines. Understanding what changes you're making also helps avoid making any mistakes that might not be necessary. Hopefully this short blog helps you along your development journey. Feel free to connect with me on [LinkedIn](https://www.linkedin.com/in/vnestor/) if you ever want to get in touch!

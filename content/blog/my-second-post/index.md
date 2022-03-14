---
title: Introduction To Git, Basics Commands, And Terminology
date: "2022-03-12"
description: A simple introduction to Git and basic commands using the CLI.
---

## Introduction

If you are just getting started on your programming journey, you will soon realize that you will constantly find yourself cloning, adding files, commiting changes, and much more. You also might be asking yourself, "what do those words mean!?", no worries! I'll be giving an short introduction to what they mean what's possible with Git!

You can check out Git's website [here](https://git-scm.com/).

## What's the difference?

You might be asking yourself, "wait, this doesn't look like GitHub!", and you're right. Git is a version control system. GitHub is a cloud-based hosting service.

A **version control system** is software that helps you control (or manage) the different versions of something, in our it's source code.

A **cloud-based hosting service** is a platform that hosts infrastructures, platforms, or software by third-party providers. GitHub is a code hosting platform for version control and collaboration.

Git is a version control tool.

GitHub is a service that hosts Git projects.

## Version Control Systems

The main point of a version control system is to **help maintain a detailed history of the project as well as the ability to work on different version of it**. Having a detailed history of a project is important because it lets you see the progress of the project over time. If needed, you can also jump back to any point in the project to recover data or files.

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

## Basic Git Commands And Terminology

Once installed we will move to the command line interface (CLI). You can quickly access the CLI on the following systems:

- Terminal on macOS
- Terminal on Linux / Unix
- Command Prompt Windows

Let's verify that you've successfully installed Git with the following command.

```js
git --version
```

If successfully installed, Git will return the following message:

> git version **version_number**\

If you don't receive this message, you try following the installation guide [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### Now we want to let know Git who you are.

```js
git config --global user.name "USERNAME"
git config --global user.email "EMAIL@EXAMPLE.COM"
```

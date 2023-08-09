---
title: "The Beginner's Guide to Git & GitHub"
datePublished: Thu Jul 20 2023 20:22:43 GMT+0000 (Coordinated Universal Time)
cuid: clkblmy0p000409l9d2yc3hjr
slug: git-github-beginner-advanced-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691545993464/c5a04a0d-0e22-41f0-8aab-90049f877068.jpeg
tags: repository, github, version-control, git, collaboration

---

## What is Git?

Imagine working on a project in which you aren’t able to keep track of file changes, or revert to previous versions of your source code. Or even worse, you are working remotely with a team of developers and you cannot collaborate and organize your code as one, to version it for an application. Fortunately, Git was created to solve this problem.

Git is a fast, open-source distributed version control system that is widely used by developers. It is used for tracking changes and maintaining versions of the source code during development. Git was designed with performance, speed, scalability and security in mind.

Having a distributed architecture, Git enables all developers working on a project to have their local working copy of the source code that contains a full history of all changes made to the source code. A copy of the source code managed by Git is called a repository.

Other examples of version control systems include:

* SourceSafe
    
* CVS
    
* SVN
    
* Mercurial
    

Most of the aforementioned version control systems have either been discontinued or are rarely seen due to their inability to handle core features needed in a modern version control system.

## What is GitHub?

GitHub is a code hosting platform used for collaboration and version control. GitHub helps us store our code on the internet so that other developers can access it from anywhere.

GitHub is one of many services that provide:

* an online git repository to push your code to
    
* a web interface to view and manage your repositories, its files and their commits.
    

GitHub has many competitors, two of the main ones being **GitLab** and **BitBucket** (which provide very similar services). However, GitHub is the most popular and has become the industry standard. Being familiar with it is important because that way, you’ll be able to interact with other open-source projects on GitHub. It’s also where tech recruiters typically go to check out what projects you’ve been working on.

## Git vs GitHub?

The following are the core differences between Git and GitHub:

| GIT | GITHUB |
| --- | --- |
| Git is a version control system that lets you manage a Git repository on your local system. | GitHub is a code hosting service that lets you store a Git repository on the internet. |
| Git provides a command-line tool for managing a repository. | GitHub provides a web interface for managing and accessing a repository. |
| Git is maintained by Linux. | GitHub is maintained by Microsoft. |

Now that you know what Git and GitHub are, as well as their differences, let’s proceed to the main purpose of this article. The purpose of this article is to help you become well versed in the use of Git and GitHub regardless of your current competency level (be it beginner or intermediate). This article can also serve as a refresher or reference for advanced users.

In this article, you are going to learn:

* How to create a repository
    
* How to clone and pull your code from GitHub
    
* How to commit and push your code to GitHub
    
* How to create and merge Git branches
    
* What are README and .gitignore files?
    

## Create a repository on GitHub

To create a repository on GitHub, follow the steps below:

1. **Create an account on GitHub**
    
    To create a repository on GitHub, you will need a GitHub account (if you don’t already have one). To create an account, go to [github.com](http://github.com) and click **Sign up**.
    
2. **Create a Personal access token on GitHub**
    
    A personal access token is GitHub’s more secure alternative to passwords. To authenticate yourself and access your repository, you need a personal access token. You are to treat this token as your password. To create a personal access token, follow the following steps:
    
    1. Click your profile photo in the upper right corner and click **settings**. Make sure you’re logged in.
        
    2. Click **Developer settings** located at the left sidebar.
        
    3. Click **Personal access tokens** and select **Tokens (classic)**.
        
    4. Click **Generate new token**, then select **Generate new token (classic)**.
        
    5. Give your token a name, in the `note` field.
        
    6. Give your token an expiration. You can leave it at 30 days.
        
    7. Under scopes, click on **repo** to select it.
        
    8. Click **Generate token**.
        
    9. Save this token somewhere secure because when you leave this page, you won’t see it again. You might have to create a new one.
        
3. **Create your repository**
    
    1. Go back to GitHub’s homepage and click **New**.
        
    2. Enter a repository name. You can use `git-delight` for the purpose of this article.
        
    3. Enter a repository description.
        
    4. Ensure **public** is selected.
        
    5. Do not add **README**, .**gitignore** or **licence**.
        
    6. Click **Create repository**.
        

Congratulations, you have successfully created your first repository on GitHub.

## Clone a GitHub repository

Now that we have created a repository on GitHub, our next step is to clone this repository onto our local computer. Cloning involves creating a copy of the repository on our local computer so that we can make changes to it.

To clone a repository, you need to have Git installed on your computer. On Linux and Mac, Git comes pre-installed but on Windows, you need to install it. To install Git, go to [https://git-scm.com/downloads](https://git-scm.com/downloads) and download the appropriate software for your computer.

To confirm if Git is installed, open your terminal or command prompt and use the `git` command with the `--version` flag:

```bash
$ git --version
git version 2.34.1
```

To clone your github repository, use the git clone command:

```bash
$ git clone https://ghp_hGNpn4B3tvSGXfg85CJDd486fc@github.com/Dheelyte/git-delight.git
Cloning into 'git-delight'...
warning: You appear to have cloned an empty repository.
```

If you received the message above, you have successfully cloned your GitHub repository onto your computer.

Note: In the command above, make sure you:

* Replace `ghp_hGNpn4B3tvSGXfg85CJDd486fc` with the personal access token which you had previously created.
    
* Replace `Dheelyte` with your GitHub username.
    
* Replace `git-delight` with your repository name, in case you used another name.
    

## Pull a GitHub repository

To pull updates from your remote repository (the one on GitHub) to your local repository (the one on your computer), use the `git pull` command. Make sure you are in the Git repository:

```bash
$ cd git-delight
~/git-delight$ git pull
```

## Commit to a Git repository

The next step is to add files to your repository. Add a `README` file that describes your project. Follow the steps below:

1. Create a README file with the `.md` extension and write a text into the file:
    
    ```bash
    ~/git-delight$ echo "This is my project's README file" > README.md
    ```
    
2. Add the newly created file to the staging area using the `git add` command, so Git can track it:
    
    ```bash
    ~/git-delight$ git add README.md
    ```
    
    You can confirm if it has been added with the `git status` command.
    
3. If this is your first time using git on your computer, you will need to tell git who you are. Enter the following command in your terminal, adding your email and name appropriately:
    
    ```bash
    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"
    ```
    
4. Commit your new file to your git repository using the `git commit` command and the `-m` flag:
    
    ```bash
    ~/git-delight$ git commit -m "This is my first commit"
    ```
    
    **Note**: If you want to write a detailed commit message, omit the `–m` flag and the commit message. Git will open a file in which you can write a detailed commit message.
    

## Push your repository to GitHub

After committing your new file to your Git repository, your next step is to push your changes to GitHub. You can do this using the `git push` command:

```bash
~/git-delight$ git push
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 265 bytes | 88.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Dheelyte/git-delight.git
 * [new branch]      main -> main
```

## Create a Git Branch

A branch is a separate version of the main Git repository. If you want to make changes to a repository and you do not want those changes to affect the main repository, create a branch and make those changes on the newly created branch. Then merge it to the main branch when you are done. For instance, a branch can be meant for a given feature, or a given bug fix. You can create however many branches you need.

To create a branch named `new_feature`, use the `git branch` command:

```bash
$ git branch new_feature
```

Switch to the new branch with the `git checkout` command:

```bash
~/git-delight$ git checkout new_feature
Switched to branch 'new_feature'
```

## Merge a Git Branch

When you’re done with the feature and want to merge it to the `main` branch, use the `git merge` command. Ensure you switch to the main branch first.

```bash
~/git-delight$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

~/git-delight$ git merge new_feature
Already up to date.
```

## Delete a Git Branch

When you have merged the `new_feature` branch with the `main` branch, delete it with the following command:

```bash
~/git-delight$ git branch -d new_feature
Deleted branch new_feature (was 87c5aea).
```

## What is a README?

A `README` is a text file that contains the details of your project. It contains information that allow other developers to understand what your project is all about. The following are pieces of information that could be included in your README file:

* Project Title
    
* Project description
    
* Installation and usage guide for your project
    
* How to contribute to your project
    

## What is a .gitignore?

A `.gitignore` is a text file that tells Git which files or folders to ignore when pushing your code to GitHub. These could include files that contain sensitive information such as private keys or access tokens. Git will not track files listed in the `.gitignore` file. It is placed in the root directory of your repository (not in any directory).

To create a `.gitignore` file on Linux, use the `touch` command:

```bash
~/git-delight$ touch .gitignore

echo "" > .gitignore    # On Windows
```

Open this file with a file editor and add the following lines:

```bash
# Ignore all text files
*.txt
# ignore ALL .log files
*.log
# ignore ALL files in ANY directory named temp
temp/
# Ignore a directory called secret_folder
secret_folder/
# Ignore a file called secret
secret
```

Note that the `.gitignore` file begins with a period **(.)**

---

## Conclusion

Mastering Git and GitHub can seem like a daunting task at first, but understanding basic development workflows – add, commit, push – can help you understand how Git and GitHub work in general. Also, contributing to open-source projects on GitHub can help in sharpening your GitHub skills. Remember, *true mastery can only be achieved through practice*.

Thanks for reading.

Connect with me on [GitHub](https://github.com/Dheelyte), [LinkedIn](https://www.linkedin.com/in/delight-olagbuji), and [Twitter](https://twitter.com/DelightGbolahan).
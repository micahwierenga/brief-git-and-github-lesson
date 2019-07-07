<!--
Market: SF
Adapted for: DEN
-->

<!-- If you can get through this faster, do so, so students have more time on their website. -->

<!--1:30 5 minutes -->

<!-- Hook: Raise your hand if you've ever had a group essay project. How did you share your essay?

...

One of the big problems with team projects is this exact problem.  How do you know which is the latest version? What happens if somebody accidentally deletes everything? What if Jack has been on fire, but he made one change that ruined our essay, and we just want to get rid of that one? Welcome to version control. -->

<img src="https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png">

# Brief Intro to Git and GitHub

## Why is this important?
*This workshop is important because:*
- Local and cloud based version control are **fundamental** tools of **every** developer
- Git and GitHub are the most popular version control solution for open-source projects
- Proficient use of Git and GitHub allows collaboration on projects from small teams to hundreds or thousands of developers.

## What are the objectives?
*After this lesson, students will be able to:*

- **Explain** basic git commands like init, add, commit, push, pull and clone
- **Create** a git repo
- **Keep** a local git repo in sync with a remote repo on GitHub

## Where should we be now?
*Before this lesson, students should already be able to:*

- **Use** the command line
- **Use** a text editor

<!--1:35 5 minutes -->

## Git vs GitHub and Version Control
<details>
  <summary>What is the difference between Git and GitHub?</summary>
  <p>Git is a software version control tool that works on your local machine. It allows you to `init`, `add`, `commit`, and `fork` project 'repos'. It also has methods `push`, `pull`, and `fetch` which are designed to interact with a git server or cloud based service like GitHub.
  <br>
  GitHub is a cloud based git server and social network which uses Git under the hood for its version control system.
  </p>
</details>


### What is version control? A closer look:

Version control is a kind of software used to track changes to files so that a comprehensive history of the file content can be reviewed.

There are two main types of version control:

- Centralized: All changes are kept on a single server
- Distributed: Changes can be tracked on individual computers, and synched using the cloud

- Git and GitHub together form a distributed version control system

![Centralized vs Distributed Version Control Systems](https://www.researchgate.net/profile/Sofia_Feist/publication/316553817/figure/fig2/AS:669480740982806@1536628055836/Centralized-Version-Control-vs-Distributed-Version-Control.ppm)

<!--CFU: Think-pair share, difference between Git/GitHub and Centralized vs Distributed -->
<!-- Catch-up -->
<!--1:40 20 minutes -->

## Let's use Git

As an initial note, there are many commands you can use in git. You can take a look at a list of the available commands by running:

```bash
$ git help -a
```

Even though there are lots of commands, in this course we will really only need about 10.

First, create a directory on your Desktop:

```bash
$ cd ~/Desktop
$ mkdir hello-world
```

Go into this directory. **Hint: how do you change directory?**

You can place this directory under Git revision control using the command:

```bash
$ git init
```

Git will reply:

```bash
Initialized empty Git repository in <location>
```

You've now initialized the working directory.

#### The .git folder

If we look at the contents of this empty folder using:

```bash
ls -A
```

We should see that there is now a hidden folder called `.git`. This is where all of the information about your repository is stored. Any changes made to this folder will be made through `git` commands.

#### Add a file

Let's create a new file:

```bash
$ touch file.txt
```

If we run `git status` we should get:

```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

This means that there is a new **untracked** file. Next, tell Git to take a snapshot of the contents of all files under the current directory (note the .).

```bash
$ git add . (or git add -A)
```
What is the difference?

This snapshot is now stored in a temporary staging area which Git calls the "index".

![](git-staging-area.png)

#### Commit

To permanently store the contents of the index in the repository, (commit these changes to the HEAD), you need to run:

```bash
$ git commit -m "Adds file.txt"
```

You should now get (the commit number will vary):

```bash
[master (root-commit) b4faebd] Adds file.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file.txt
```

#### Checking the log

If we want to view the commit history, we can run:

```bash
git log
```

You should see (again, the commit number will vary):

```bash
commit 5d5bbac15ab228f1b96015c6031cb8f8a1dfd92d
Author: [GitHub_username] <[GitHub_email]>
Date:   Sun Dec 23 23:28:50 2018 -0700

    Adds file.txt
```

<!--2:00 10 minutes -->
<!--Catch-up -->

#### Make changes to the file

Now let's open file.txt in Sublime:

```bash
$ subl file.txt
```

Inside the file, write something.

Running `git status` again will show you that file.txt has been **modified**.

## Questions

Use the internet and what you've learned today to answer the following questions with a partner:

* How do I send changes to the staging area?
* How do I check what is going to be committed?

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

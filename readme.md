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
- Local- and cloud-based version control are **fundamental** tools of **every** developer.
- Git and GitHub are the most popular **version control solution** for open-source projects.
- Proficient use of Git and GitHub allows **collaboration** on projects from small teams to hundreds or thousands of developers.

<!-- We won't get too deep into GitHub today, but we should have a better idea of what role it plays in the process. -->

## What are the objectives?
*After this lesson, students will be able to:*

- **Explain** basic git commands like init, add, commit, and status.
- **Create** a local git repo on their computers.

## Where should we be now?
*Before this lesson, students should already be able to:*

- **Use** the command line.
- **Use** a text editor.

<!--1:35 5 minutes -->

## Git vs GitHub and Version Control

### What is the difference between Git and GitHub?

- Git is a software version control tool that works on your local machine. It allows you to `init`, `add`, `commit`, and `fork` project 'repos'. It also has methods `push`, `pull`, and `fetch` which are designed to interact with a git server or cloud based service like GitHub.

- GitHub is a cloud-based git server and social network which uses Git under the hood for its version control system.

<!-- It's social in that developers can share their code with other developers by sharing the link to those repos. You can also follow developers to see what they're up to, as well as watch specific repos that you might be interested. -->

### What is version control? A closer look:

Version control is a kind of software used to track changes to files so that a comprehensive history of the file content can be reviewed.

<!-- What this means is that, as you're creating and changing code, you get to keep a history of those changes because of software like git, as well as your notes about those changes and creations. -->

There are two main types of version control:

- **Centralized:** All changes are kept on a single server.
- **Distributed:** Changes can be tracked on individual computers, and synched using the cloud.

- Git and GitHub together form a distributed version control system.

![Centralized vs Distributed Version Control Systems](https://www.researchgate.net/profile/Sofia_Feist/publication/316553817/figure/fig2/AS:669480740982806@1536628055836/Centralized-Version-Control-vs-Distributed-Version-Control.ppm)

<!-- For centralized systems, this means that the code lives on the server, so you typically need to be connected to that server because each developer's copy of that code also lives on the server. Then, each dev will push their changes to that repo on the server. Finally, a designated dev will push these changes to the live server or servers. -->

<!-- For distributed systems, however, a complete copy of the code and the code history lives on each person's computer, so the devs don't need to be connected to the server where the source-of-truth code lives all the time. They can make their changes. Then, they can connect to the server and push their changes, which can then be pulled down to each developer's computer if they wish. -->

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

<!-- In other words, you've created that local repo on your machine. And, this local repo serves many purposes, but two of the main ones are that it's a backup of your committed code. So, if you're consistently putting your changes in that local repo, if you accidentally delete changes or files, you have a backup. Secondly, it serves as the connection point between the code on your computer and the code on GitHub, or wherever your remote repo lives. -->

#### The .git folder

If we look at the contents of this empty folder using:

<!-- Show students that no files appear when just running ls. -->

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

<!-- This command tells us stuff like, have we made changes to any files? If we have, have we put those changes in our local repo? -->

```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

<!-- So this status is telling us that our local repo doesn't know about our file.txt yet, so let's tell that repo about our new file. -->

This means that there is a new **untracked** file. Next, tell Git to take a snapshot of the contents of all files under the current directory (note the ., which means add all changes).

```bash
$ git add .
```

This snapshot is now stored in a temporary staging area which Git calls the "index".

![](git-staging-area.png)

<!-- So now we've moved our changes from the code that we're working on to the staging area. -->

#### Commit

To permanently store the contents of the index in the repository, we need to run:

```bash
$ git commit -m "Adds file.txt"
```

You should now get a message like:

```bash
[master (root-commit) b4faebd] Adds file.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file.txt
```

<!-- And now our changes are in our local repo! They are officially backed up and ready to push up to GitHub if we wanted. -->

#### Make changes to the file

Now let's just a little bit of text:

```bash
$ printf "Hello\n" >> file.txt
```

(You can run `cat file.txt` to see your new content!)

Running `git status` again will show you that file.txt has been **modified**.

Now let's make sure that our local repo knows about these changes.

```bash
$ git add .
```

```bash
$ git commit -m "Added text to file"
```

We won't be pushing these changes to GitHub today, but normally that would be the next step. But, now we know how to create that local repository on our own computers.

## Questions

Take a minute to answer the following questions with a partner. Use the internet and what you've learned today to form your answers:

* How do I send changes to the staging area?
* How do I check what is going to be committed?

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

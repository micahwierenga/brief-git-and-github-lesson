<!--
Market: SF
Adapted for: DEN
-->

<!-- If you can get through this faster, do so, so students have more time on their website. -->

<!--1:30 5 minutes -->

<!-- Hook: Raise your hand if you've ever had a group essay project. How did you share your essay?

...

One of the big problems with team projects is this exact problem.  How do you know which is the latest version? What happens if somebody accidentally deletes everything? What if Jack has been on fire, but he made one change that ruined our essay, and we just want to get rid of that one? Welcome to version control. -->

# Git and Github

## Why is this important?
*This workshop is important because:*
- Local and cloud based version control are **fundamental** tools of **every** developer
- Git and Github are the most popular version control solution for open-source projects
- Proficient use of Git and Github allows collaboration on projects from small teams to hundreds or thousands of developers.

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
  Github is a cloud based git server and social network which uses Git under the hood for its version control system.
  </p>
</details>


### What is version control? A closer look:

Version control is a kind of software used to track changes to files so that a comprehensive history of the file content can be reviewed.

There are two main types of version control:

- Centralized: All changes are kept on a single server
- Distributed: Changes can be tracked on individual computers, and synched using the cloud

- Git and GitHub together form a distributed version control system

<!--CFU: Think-pair share, difference between Git/GitHub and Centralized vs Distributed -->

#### So many commands?!

There are also a lot of commands you can use in git. You can take a look at a list of the available commands by running:

```bash
$ git help -a
```

Even though there are lots of commands, in this course we will really only need about 10.

<!-- Catch-up -->
<!--1:40 20 minutes -->

## Let's use Git

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

We should see that there is now a hidden folder called `.git`. This is where all of the information about your repository is stored. There is no need for you to make any changes to this folder. You can control all the git flow using `git` commands.

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

This means that there is a new **untracked** file. Next, tell Git to take a snapshot of the contents of all files under the current directory (note the .)

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

You should now get:

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

You should see:

```bash
commit 5d5bbac15ab228f1b96015c6031cb8f8a1dfd92d
Author: [GitHub username] <[GitHub email]>
Date:   Sun Dec 23 23:28:50 2018 -0700

    Adds file.txt
```

#### A good commit message
A good commit message is:
  - in present tense
  - describes what the commit contributes

Good | Bad
-----|----
"Adds signup and login" | "Added logout stuff"
"Creates upvote counter" | "Upvotes!"
"Fixes merge conflict" | "conflict"
"Fixes typo"| "stupid f***ing typos"
"Fixes issue #347" | [commit logs from last night](http://www.commitlogsfromlastnight.com/)


![](https://explainxkcd.com/wiki/images/d/de/git_commit.png)


<!--2:00 10 minutes -->
<!--Catch-up -->

#### Make changes to the file

Now let's open file.txt in Sublime:

```bash
$ subl file.txt
```

Inside the file, write something.

If you press `return` in the terminal, you will now see that you have untracked changes.

Running `git status` again will show you that file.txt has been **modified**.

#### Revert to a previous commit

Let's now make a second commit.

```bash
$ git add .
$ git commit -m "Adds content to file.txt"
```

Checking `git log` will show you 2 commits with different ids:

```bash
* 6e78569 (HEAD, master) Adds content to file.txt
* b4faebd Adds file.txt
```

We can revert the file back to the first commit using its specific commit id with:

```bash
$ git reset --soft b4faebd
```

This will do a soft reset, where the changes in the file we made are still there - the changes are staged but not committed anymore.

If we want to revert the file back and disregard any changes (dangerous!), ~~we can use~~ almost definitely do **not** use:

```bash
$ git reset --hard b4faebd
```

<!--2:10 10 minutes -->

### GitHub

#### Making and cloning repositories

<!--Catch-up-->

1. Go to your Github account
2. In the top left, hit the + button and select `New repository`
![](https://help.github.com/assets/images/help/repository/repo-create.png)
3. Name your repository `hello-world`
![](https://help.github.com/assets/images/help/repository/repo-create-name.png)
4. **Initialize this repository with a README** (So that we can `git pull`)
4. Click the big green Create Repository button

We now need to connect our local Git repo with our remote repository on GitHub. We have to add a "remote" repository, an address where we can send our local files to be stored.

```bash
git remote add origin git@github.com:github-name/hello-world.git
```

<!--2:20 10 minutes -->
#### Pushing to Github

In order to send files from our local machine to our remote repository on Github, we need to use the command `git push`. However, you also need to add the name of the remote, in this case we called it `origin` and the name of the branch, in this case `master`.

```bash
git push origin master
```

This should fail due to new files on the remote repo.

#### Pulling from Github

As we added the README.md in our repo, we need to first `pull` that file to our local repository to check that we haven't got a 'conflict'.

```bash
git pull origin master
```

Once we have done this, you should see the README file on your computer. Now you can push your changes:

```bash
git push origin master
```

Refresh your GitHub webpage, and the files should be there.

<!--2:30 10 minutes -->

#### Cloning

Cloning allows you to get a local copy of a remote repository.

Navigate back to your Desktop and **delete your hello-world repository**:

```bash
cd ~/Desktop
rm -rf hello-world
```

Now ask the person sitting next to you for their github name and navigate to their repository on github:

```bash
https://www.github.com/<github-username>/hello-world
```

On the right hand side you will see:

![clone](https://cloud.githubusercontent.com/assets/40461/8228838/dfdc57a0-15a9-11e5-90a7-6c4fa8641ae6.jpg)

Ensure that you have SSH checked and copy this url.

#### Clone their repo!

To retrieve the contents of their repo, all you need to do is:

```bash
$ git clone git@github.com:alexpchin/hello-world.git
```

Git should reply:

```bash
Cloning into 'hello-world'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
Checking connectivity... done.
```

You now have cloned your first repository!

<!--2:40 10 minutes -->

## Forking

The `fork` & `pull` model lets anyone fork an existing repository and push changes to their personal fork without requiring access be granted to the source repository.

Most commonly, forks are used to either propose changes to someone else's project or to use someone else's project as a starting point for your own idea.

#### Cloning vs Forking

When you fork a repository, you make a new **remote** repository that is exactly the same as the original, except you are the owner. You can then `clone` your new fork and `push` and `pull` to it without needing any special permissions.

When you clone a repository, unless you have been added as a contributor, you will not be able to push your changes to the original remote repository.

#### Pull requests

When you want to propose a change to a repository (the original project) that you have forked, you can issue a pull request. This basically is you saying:

_"I've made some changes to your repository, if you want to include them in your original one then you can pull them from my fork!"_

<!--2:50 5 minutes -->

## Questions

Use the internet and what you've learned today to answer the following questions with a partner:

* How do I send changes to the staging area?
* How do I check what is going to be committed?
* How do I send the commits to Github?
* How do I go back to the previous commit?
* How do I check the configuration on a specific machine?
* How does github know that I am allowed to push to a specific repo?

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.

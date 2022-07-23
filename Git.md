Required Commands
Heads up! We'll be using the following terminal commands in this lesson:

ls - used to list files and directories
mkdir - used to create a new directory
cd - used to change directories
rm - used to remove files and directories
If you're not sure how to use them, check out our course Shell Workshop!

We'll also be using the idea of the current working directory, the directory that your shell is "looking at" right now. Using cd changes your working directory, and using ls (by itself) lists the files in the working directory. If you lose track of what your shell's working directory is, you can print its name with the pwd command (which stands for "print working directory").

.Git Directory Contents
We're about to take a look at the .git directory...it's not vital for this course, though, so don't worry about memorizing anything, it's here if you want to dig a little deeper into how Git works under the hood.

Here's a brief synopsis on each of the items in the .git directory:

config file - where all project specific configuration settings are stored.
From the Git Book:

Git looks for configuration values in the configuration file in the Git directory (.git/config) of whatever repository you’re currently using. These values are specific to that single repository.

For example, let's say you set that the global configuration for Git uses your personal email address. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

description file - this file is only used by the GitWeb program, so we can ignore it
hooks directory - this is where we could place client-side or server-side scripts that we can use to hook into Git's different lifecycle events
info directory - contains the global excludes file
objects directory - this directory will store all of the commits we make
refs directory - this directory holds pointers to commits (basically the "branches" and "tags")
Remember, other than the "hooks" directory, you shouldn't mess with pretty much any of the content in here. The "hooks" directory can be used to hook into different parts or events of Git's workflow, but that's a more advanced topic that we won't be getting into in this course.

Further Research
Git Internals - Plumbing and Porcelain (advanced - bookmark this and check it out later)
Customizing Git - Git Hooks
Git Init Recap
Use the git init command to create a new, empty repository in the current directory.

$ git init
Running this command creates a hidden .git directory. This .git directory is the brain/storage center for the repository. It holds all of the configuration files and directories and is where all of the commits are stored.
Git Status Explanation
As you can see in the GIF above, running git status in the course-git-blog-project project produces the following output:

On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
The output tells us two things:

On branch master – this tells us that Git is on the master branch. You've got a description of a branch on your terms sheet so this is the "master" branch (which is the default branch). We'll be looking more at branches in lesson 5
Your branch is up-to-date with 'origin/master'. – Because git clone was used to copy this repository from another computer, this is telling us if our project is in sync with the one we copied from. We won't be dealing with the project on the other computer, so this line can be ignored.
nothing to commit, working directory clean – this is saying that there are no pending changes.
Think of this output as the "resting state" (that's not an official description - it's how I like to describe it!). This is the resting state because there are no new files, no changes have been made in files, nothing is in the staging area about to be committed...no change or action is pending, so that's why I like to call it the resting state.

So this is what it looks like when running git status in a repository that already has commits.

Git Log Recap
Fantastic job! Do you feel your Git-power growing?

Let's do a quick recap of the git log command. The git log command is used to display all of the commits of a repository.

$ git log
By default, this command displays:

the SHA
the author
the date
and the message
...of every commit in the repository. I stress the "By default" part of what Git displays because the git log command can display a lot more information than just this.

Git uses the command line pager, Less, to page through all of the information. The important keys for Less are:

to scroll down by a line, use j or ↓
to scroll up by a line, use k or ↑
to scroll down by a page, use the spacebar or the Page Down button
to scroll up by a page, use b or the Page Up button
to quit, use q

git log --oneline Recap
To recap, the --oneline flag is used to alter how git log displays information:

$ git log --oneline
This command:

lists one commit per line
shows the first 7 characters of the commit's SHA
shows the commit's message

git log --stat Recap
To recap, the --stat flag is used to alter how git log displays information:

$ git log --stat
This command:

displays the file(s) that have been modified
displays the number of lines that have been added/removed
displays a summary line with the total number of modified files and lines that have been added/removed

git log -p Recap
To recap, the -p flag (which is the same as the --patch flag) is used to alter how git log displays information:

$ git log -p
This command adds the following to the default output:

displays the files that have been modified
displays the location of the lines that have been added/removed
displays the actual changes that have been made

Git Add Recap
The git add command is used to move files from the Working Directory to the Staging Index.

$ git add <file1> <file2> … <fileN>
This command:

takes a space-separated list of file names
alternatively, the period . can be used in place of a list of files to tell Git to add the current directory (and all nested files)

Git Commit Recap
The git commit command takes files from the Staging Index and saves them in the repository.

$ git commit
This command:

will open the code editor that is specified in your configuration
(check out the Git configuration step from the first lesson to configure your editor)
Inside the code editor:

a commit message must be supplied
lines that start with a # are comments and will not be recorded
save the file after adding a commit message
close the editor to make the commit
Then, use git log to review the commit you just made!
## Explain the Why
If you need to explain why a commit needs to be made, you can!

When you're writing the commit message, the first line is the message itself. After the message, leave a blank line, and then type out the body or explanation including details about why the commit is needed (e.g. URL links).
This details section of a commit message _is_ included in the git log.
Git Diff Recap
To recap, the git diff command is used to see changes that have been made but haven't been committed, yet:

$ git diff
This command displays:

the files that have been modified
the location of the lines that have been added/removed
the actual changes that have been made

Git Ignore Recap
To recap, the .gitignore file is used to tell Git about the files that Git should not track. This file should be placed in the same directory that the .git directory is in.

Git Tag Recap
To recap, the git tag command is used to add a marker on a specific commit. The tag does not move around as new commits are added.

$ git tag -a beta
This command will:

add a tag to the most recent commit
add a tag to a specific commit if a SHA is passed

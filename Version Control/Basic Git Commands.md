At its core, the Git version control system is a content addressable filesystem. It uses the **SHA-1** hash function to name content.

https://towardsdatascience.com/understanding-the-fundamentals-of-git-25b5b7ded3c4

https://initialcommit.com/blog/Learn-Git-Object-Database

https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

- git show 

## How do you create a New Repository?

A git repository is simply a directory containing a special `.git` directory. Simply run `git init` in the directory which contains the files you wish to track. This creates a `.git` (hidden) folder in the current directory.

To make a new project, run `git init` with an additional argument (the name of the directory to be created):

```
git init project002

(This is equivalent to: mkdir project002 && cd project002 && git init)
```

To check if the current current path is within a git repository, simply run `git status` - if it's not a repository, it will report "fatal: Not a git repository"

You could also list the `.git` directory, and check it contains files/directories similar to the following:

```
$ ls .git
HEAD         config       hooks/       objects/
branches/    description  info/        refs/
```

If for whatever reason you wish to "de-git" a repository (you wish to stop using git to track that project). Simply remove the `.git` directory at the base level of the repository.

```
cd ~/code/project001/
rm -rf .git/
```

**Caution:** This will destroy _all_ revision history, _all_ your tags, _everything_ git has done. It will not touch the "current" files (the files you can currently see), but previous changes, deleted files and so on will be unrecoverable!

SOURCE :: https://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide

## What is HEAD?

When working with Git, only _one_ branch can be checked out at a time - and this is what's called the "HEAD" branch. Often, this is also referred to as the "active" or "current" branch.

Git makes note of this current branch in a file located inside the Git repository, in `.git/HEAD`. (This is an internal file, so it should not be manually manipulated!)

## Detached HEAD

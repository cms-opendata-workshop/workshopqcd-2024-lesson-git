---
title: "Exercises"
teaching: 10
exercises: 20
---

:::::::::::::::::::::::::::::::::::::: questions 

- How to create a repository?
- What is local, what is remote?
- How to push your updates?
- How to use branches?
- And many more...

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Have Git installed
- Configure Git user name
- Create a GitHub account
- Create an ssh key to authenticate to GitHub

::::::::::::::::::::::::::::::::::::::::::::::::

## Create a Git repository from terminal

Create a new directory, e.g. `git-example`

```bash
mkdir git-example
cd git-example
```

You can turn it to a Git repository with

```bash
git init
```

If you have not configured the default branch name, you will get this:

```output
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
```

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 1

If you got the output above, follow this advice and change the branch name to `main` and configue your default initial branch name to `main`. 

:::::::::::::::: solution


```bash
git config --global init.defaultBranch main
git branch -m main
```

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


Check the status of the repository with

```bash
git status
```

```output
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Add a new file to the directory. You can use the following :

```bash
echo sometext > newfile.txt
```

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 2

Check the status again and **add** the file to be committed as instructed in the Git messages. 

:::::::::::::::: solution

Check the status:

```bash
git status
```

```output
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        newfile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Add the current status of the file to the "staging" area with

```bash
git add newfile.txt
```

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

Make a version of the repository, i.e. **commit** the new file with

```bash
git commit -m "First version of newfile.txt"
```

Flag `-m` is follow by a commit message. When things go wrong, you will learn to appreciate clear and descriptive commit message.

```output
[main (root-commit) 0a0951c] First version of newfile.txt
 1 file changed, 1 insertion(+)
 create mode 100644 newfile.txt
```

### Exercise 3

Find the git command to check the version history. Use e.g. [Git cheat sheet](https://training.github.com/downloads/github-git-cheat-sheet/).

:::::::::::::::: solution


Won't show it, find it yourself!


:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


## Create a Git repository from GitHub WUI









::::::::::::::::::::::::::::::::::::: keypoints 

- You can turn any directory to a versioned code repository with Git.
- You can upload the content of a local repository to a remote repository such as GitHub. 

::::::::::::::::::::::::::::::::::::::::::::::::

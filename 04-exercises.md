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

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 3

Find the git command to check the version history. Use e.g. [Git cheat sheet](https://training.github.com/downloads/github-git-cheat-sheet/).

:::::::::::::::: solution


Won't show it, find it yourself!


:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


Modify the file, e.g.

```bash
echo somenewtext >> newfile.txt
```

Now you can check the differences against the previous version:

```bash
git diff
```

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 4

Add and commit your changes as before.

:::::::::::::::: solution

```bash
git add .
git commit -m "Update of newfile.txt"
```

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

## Upload an existing local repository to GitHub

Go to your GitHub area (https://github.com/[yourgithubname], choose the "Repositories" tab and click on New.

Choose `git-example` as the repository and leave other options as they are. This will generate an instruction page, and you can copy the commands under the title **"…or push an existing repository from the command line"**.

Note that GitHub provides the command to change the branch name to `main` which we did already.

The `git remote add...` command

```bash
git remote add origin git@github.com:[yourgithubname]/git-example.git
```

defines your new GitHub repository as the remote repository and names it as `origin`. This is a common choice and is used when pushing the code in the repository:

```bash
git push -u origin main
```

The option `-u` links your local main to the remote main. Therefore you only need to do this once.

You can now check the remote repository location with:

```bash
git remote -v
```

```output
origin  git@github.com:[yourgithubname]/git-example.git (fetch)
origin  git@github.com:[yourgithubname]/git-example.git (push)
```

Check also that the code has appeared in the GitHub. If you still have the instruction page open, click on `<> Code` top-left to see the repository contents.



::::::::::::::::::::::::::::::::::::: challenge

### Exercise 5

Create a another GitHub repository following the instructions under the title **"…or create a new repository on the command line"**.

**Note**: create a new local directory first, do not nest Git repositories.

:::::::::::::::: solution

Go to your GitHub area (https://github.com/[yourgithubname], choose the "Repositories" tab and click on New.

Choose `git-example-web` as the repository and leave other options as they are. This will generate an instruction page, and you can copy the commands under the title **"…or create a new repository on the command line"**.

You will notice that the commands are the same what we have done above. You can use it if you start from an empty directory.

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

## Clone an existing repository from GitHub

Ask an another participant to provide you their GitHub repository address and clone it locally. As we all used the same name, plain cloning will fail with

```bash
git clone git@github.com:[someoneelse]/git-example.git
```

```output
fatal: destination path 'git-example' already exists and is not an empty directory.
```

Give it another name, e.g. `git-example-friend`

```bash
git clone git@github.com:[someoneelse]/git-example.git git-example-friend
```

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 6

What is the remote for this local repository?

:::::::::::::::: solution

Git has created a new directory with the chosen name. Move to it and check the remote.

```bash
cd git-example-friend/
git remote -v
```

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

## Using branches

If you are using GitHub as a remote storage for your code and you are the only contributor, you will most likely push your changes to the `main` branch.

However, when you contribute to other remote repositories, you would always use a branch of your own which can then be merged to the remote repo `main` branch.

In the `git-example-friend` repository, create a new branch:

```
git checkout -b [yourname]-new-feature
```

You are free to choose a name, but it is useful agree on some rules or practices in a project with several contributors. A common choice is something with your name and something that indicates what this branch is for.

You can check the branch with

```
git branch
```

The star indicates in which branch you are in.

::::::::::::::::::::::::::::::::::::: challenge

### Exercise 7

Create a new file in the repository, add and commit it locally and then push it to the remote repository.

**Note**: instead of `main` in `git push origin main`, you will now use your new branch name.

:::::::::::::::: solution

Create a file

```bash
echo sometext > yourname-file.txt
```

Check the status, add, commit and push:

```bash
git status
git add .
git commit -m "[yourname]: some descriptive message"
git push origin [yourname]-new-feature
```


:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

### Optional exercise

Try this for fun:
- create a Git repository on your university account (or lxplus at CERN if you have an account), add and commit some files in it.
- clone the repository to your laptop: instead of `git@github.com:/<repository>.git`, use `youraccount@domain:/full/directory/path` in `git clone`
- check the remote repository address on your laptop
- try if you can push changes from your laptop to the remote on your university account.

:::::::::::::::: solution

Note that this not necessarily what you would ever do, but it illustrates that Git is completely independent from GitHub or GitLab.

Note also that Git does not allow to push to a branch that is checked out in the remote repository. You will have to push in another branch.

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- You can turn any directory to a versioned code repository with Git.
- You can upload the content of a local repository to a remote repository such as GitHub. 

::::::::::::::::::::::::::::::::::::::::::::::::

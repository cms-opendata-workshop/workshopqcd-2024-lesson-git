---
title: "Exercises"
teaching: 10
exercises: 30
---

:::::::::::::::::::::::::::::::::::::: questions 

- How to upload your code to GitHub?
- What information to add to make the code reusable?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Upload a Pythia example to a GitHub repository
- Make sure that it contains all necessary information for its use
- Test someone's else code and give feedback

::::::::::::::::::::::::::::::::::::::::::::::::

## Create a GitHub repository for your Pythia code

During the Pythia sessions, you have exercised with different examples.

::::::::::::::::::::::::::::::::::::: challenge

### Prepare a local repository

Create a local Git repository under your work directory for one of the examples. 

:::::::::::::::: solution

Make sure that the directory has all necessary files to run the example.
In general, it is a good practice to structure it so that it has subdirectoris for code, inputs and outputs:

```
$ tree example_dir/
example_dir/
├── code
├── inputs
└── outputs
```

However, for the Pythia examples, the Makefile is written so that it expects the code files to be at the same level with it.
Move to the directory and initialize it with

```bash
git init
```

Move all necessary files to this directory and test that everything works, i.e compile and run the code.

Remember to compile and run the code in the Pythia container. Start it from the working repository with

```bash
docker run -v $PWD:/host -w /host -it --rm hepstore/rivet-pythia
```


:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

### Exclude files with .gitignore

Before committing files to the repository, think what files you would like to exclude. Create a `.gitignore` file with the names of the files that you do not intend to upload.

:::::::::::::::: solution

See `.gitignore` example files in https://github.com/github/gitignore
In our case, you will probably leave out the executable file. If it is called `main01` , the contents of the `.gitignore` file would be

```
main01
```

Note that the file starting with dot (.) are not visible with the usual `ls` commands, use `ls -a` to see them.

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::: challenge

### Commit the files

**Add** the files you want to version and **commit** them. 

:::::::::::::::: solution

Check the status:

```bash
git status
```

Note that the executable file defined in the `.gitignore` file does not appear in the list. However, always make sure to add only the files that you want to commit and in case some unwanted file appear in the list of `Untracked files`, add them to `.gitignore` (or remove if you do not need them).

Add and commit:

```bash
git add .
git commit -m "First commit"
```

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

### Upload the local repository to GitHub

Create a GitHub repository and push your files there.

:::::::::::::::: solution

Go to your GitHub area (`https://github.com/[yourgithubname]`), choose the "Repositories" tab and click on New.

Choose a repository name, select Public and leave other options as they are. This will create the repository and generate an instruction page, and you can copy the commands under the title **"…or push an existing repository from the command line"**.

```bash
git remote add origin git@github.com:[yourgithubname]/[yourreponame].git
git branch -M main
git push -u origin main
```

Note that your the SSH key connected to GitHub is in your local file system, and it is not in the directory that is shared with the container. Therefore, you will not be able to push to your GitHub repository from the container. Do it from your local shell.

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

### Add instructions

Add instructions to your repository so that other people know what your code does and how to use it. Write them in `README.md` and push them to the GitHub repository.

:::::::::::::::: solution

Good instructions should contain

a brief description of the code
description of the running environment
description of the input parameters
instructions to compile and run
description of the expected output

Write them in a new file called `README.md`. 

Check status:

```bash
git status
```

Add and commit:

```bash
git add .
git commit -m "Add README"
```

Push to the remote repository:

```bash
git push origin main
```



:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::: challenge

### Clone a repository of someone else and run their code

Ask other participants the address of their GitHub repository and clone it locally. 

**Note**: first move up from your Git repository. Do not nest Git repositories.

Follow their instructions to run the code.

:::::::::::::::: solution

Move to your working area, and use `git clone`. Copy the repository address from the green `Code` dropdown menu (ssh tab).

If their repository name is same as yours, give it another name locally:

```bash
git clone git@github.com:[someoneelse]/[repositoryname].git [localrepositoryname]
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

The star indicates in which branch you are.

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

Did you get an error? Ask your friend to invite you as a collaborator in the repository from Settings -> Collaborators and teams -> Add people.

:::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::::::::::

In the GitHub Web UI of the repository, a message about recent pushes has now appeared. You can now open a pull request from the new branch to the main branch.

Click on Compare and pull.

Describe the pull request in the text field.

Then click on Pull.

You can then explore the changes, and add some discussion.

There is an option to review changes and approve them. It can be set as obligatory in the repository settings.

Usually, the owner of the project merges the pull request.

Once the pull request is merged, remember to update your local repository.
Do the following:

```bash 
git checkout master
git pull
```





::::::::::::::::::::::::::::::::::::: keypoints 

- It is easy to store and share your code throug a GitHub.
- Clear instructions make it possible for other people to run your code. 

::::::::::::::::::::::::::::::::::::::::::::::::

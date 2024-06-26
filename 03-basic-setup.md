---
title: "Basic setup"
teaching: 10
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions 

- Do you have Git installed?
- How to configure Git?
- Do you have 

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Have Git installed
- Configure Git user name
- Create a GitHub account
- Create an ssh key to authenticate to GitHub

::::::::::::::::::::::::::::::::::::::::::::::::

## Installing Git

Check if you have Git installed with:

```bash
git --version
```

If not found, go to the offical [Git download instructions](https://git-scm.com/downloads) and install Git. If you working on WSL2 Ubuntu, choose Linux/Unix, not Windows.


## Configuring Git

You might have used Git without user configuration, e.g. when you just clone a repository from GitHub with `git clone https://github.com/<XXX>/<YYY>.git`.
To be able to add code ("push") in repositories, you will need to to configure user information.

Check if you have it already with:

```bash
git config --list
```

If `user.name` and `user.email` appear in the list, you are all set.

If not configure user information for with

```bash
git config --global user.name "[name]"
git config --global user.email "[email address]"
```

Replace `[...]` with your input, and keep the quotes around your name if there are spaces.

You can read more about configuring Git in https://coderefinery.github.io/git-intro/configuration/#configuring-git-command-line-and-editor

## GitHub

### Create a GitHub account

In this workshop, we will use GitHub as a "remote" repository. If you do not have a GitHub account yet, create one by following "Sign up" from the [GitHub homepage](https://github.com/). Note that the email address should match the one that you configured for local Git.

TODO: check if user.github= is needed in git config.

### Generate an SSH key and add it to GitHub for authentication 

To be able to push code to GitHub from your terminal, you will need to authenticate.
SSH is the recommended method. 

Check if you already have set it up:

```bash
ssh -T git@github.com
```

It is already done, if you get:

```output
Hi yourusername! You've successfully authenticated, but GitHub does not provide shell access.
```

If not, follow these instructions: 

- [generate a SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
- [add the key to a ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)
- [add the key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui#adding-a-new-ssh-key-to-your-account)



::::::::::::::::::::::::::::::::::::: keypoints 

- You need to configure Git user information for your local repository.
- You can use an SSH key to authenticate your connection to GitHub from terminal. 

::::::::::::::::::::::::::::::::::::::::::::::::

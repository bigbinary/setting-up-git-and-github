
### Introduction to Git

Git is a version control system that helps developers track and manage changes to their code. Here's a brief overview of what Git can do:

1. Track Changes: Git keeps a record of every modification to the code. If you make a mistake, you can revert to a previous version.
2. Collaboration: Multiple developers can work on the same project simultaneously. Git manages changes from different sources efficiently.
3. Branching: You can create branches in Git, allowing you to work on new features or bug fixes without affecting the main codebase. Once you're done, you can merge your changes back.

For example, imagine you're writing a story and decide to take it in two different directions. With Git, you can create two branches (one for each direction) and work on them separately. When you decide which one to go with, you can merge it into your main story.

In essence, Git is like a time machine and collaboration tool for your code, making it an essential tool for developers.

### Workflow of Git

Git manages our project files through three main states: modified, staged, and committed, which correspond to the workflow steps:

- **Modified**: We've made changes to our files, but these changes are only on our computer. For example, we edit a file called index.html.
- **Staged**: We select the changes we want to save (commit). For example, we stage the index.html file using `git add index.html`. Now, Git knows we want these changes in the next snapshot but hasn't saved them yet.
- **Committed**: By running the `git commit` command, we save the staged changes to Git's database on our computer. This means our changes are securely stored.

These states are part of three sections in a Git project:

1. Working Tree: Our current project files that we can edit.
2. Staging Area (Index): A file that tracks what will be in the next commit.
3. Git Directory: Where Git stores our project's history and metadata.

<image alt="Git basic workflow">git-basic-workflow.png</image>

The workflow is simple: modify files in our working tree, stage the ones we want to commit, and then commit them. This process ensures our project's history is well organized and our changes are safely recorded.


### Installing Git on Mac

Installing Git on a Mac is pretty straightforward. We will explore two ways to install Git on a Mac.

## Using Xcode Command Line Tools

Xcode Command Line Tools is a set of tools provided by Apple for developing software on macOS. We can check if Git is already installed on our Mac by running the following command in the Terminal.

```bash
git --version
```

This command will prompt us to install Xcode Command Line Tools if it is not already installed. We follow the on-screen instructions to install it, which includes Git.

## Using Homebrew

Homebrew is a package manager for macOS and we can use it to install Git. We can install git using Homebrew by running the following command in the Terminal.

```bash
brew install git
```

## Verifying the Installation

To verify that Git has been installed successfully, we can run the following command in the Terminal.

```bash
git --version
```

This command will display the version of Git installed on our Mac.


### Installing Git on Windows

Installing Git on Windows can be done with or without WSL. Let's explore both ways.

## Installing Git with WSL

WSL is a compatibility layer for running Linux binary executables natively on Windows. We have a separate guide on how to install WSL on Windows. You can check it out [here](https://courses.bigbinaryacademy.com/learn-rubyonrails/installing-ruby-on-rails-on-windows/#installing-wsl). You can install Git on your Windows using WSL by following these steps:

_Step 1_: Open your WSL terminal.

_Step 2_: Update the package list using the following command.

```bash
sudo apt update
```

_Step 3_: Install Git using the following command.

```bash
sudo apt install git
```

_Step 4_: Verify the installation by running the following command.

```bash
git --version
```

This command will display the version of Git installed on your system.

## Installing Git without WSL

To install Git on Windows without WSL, we can download the installer from the [official Git website](https://git-scm.com/download/win). The installer will download the latest version of Git for Windows and provide us with an installation wizard. Follow the on-screen instructions to install Git on your Windows system. You can check out [this](https://phoenixnap.com/kb/how-to-install-git-windows) link for navigating through the installation process. BigBinary academy doesn't recommend anyone to use git without WSL.


### Installing Git on Linux

To get the basic Git tools on your Linux system, you can install it using the package manager that comes with your distribution. Let's see how we can install Git on some popular Linux distributions. Please open your terminal and follow the instructions below.

## Installing Git on Debian-based distribution

To install Git on Ubuntu, or any other Debian-based distribution, we can use the `apt` package manager. We can install Git on Ubuntu by running the following command in the Terminal.

```bash
sudo apt install git-all
```

## Installing Git on RPM-based distribution

To install Git on Fedora, CentOS, or any other RPM-based distribution, we can use the `dnf` package manager. We can install Git on Fedora by running the following command in the Terminal.

```bash
sudo dnf install git-all
```

## Verifying the Installation

We can verify the installation by running the following command.

```bash
git --version
```

This command will display the version of Git installed on our system.

If you're looking for more ways to install Git on different types of Linux systems, the Git website has easy-to-follow instructions for many Linux versions. Just visit the [official Git website](https://git-scm.com/download/linux) to find them.


### Introduction to the init command

The `git init` is a command we use to initialize git on a directory. Think of it as setting up a new directory that Git will watch over, keeping track of all the changes we make to the files inside it. We can use the `git init` command to initialize a new project or track the changes on an existing project. To do this,

1. Open the terminal. (Git Bash application if you are using git natively in Windows)
2. Create a new directory if you are starting with a new project: `mkdir directory-name`. You can skip this step if you want to initialize git on an existing project/directory.
3. Navigate inside the directory where you want to initialize Git: `cd directory-name`.
4. Initialize Git: `git init`.

By running the `git init` command, Git creates a hidden directory called .git in our project directory. This `.git` directory is where Git stores all the information about our project's history and changes. We will work with this directory only in rare cases, but it's important that it stays there.

Now Git has been initialized inside our project directory and it will start tracking all the changes we make within the directory.



### Add SSH key to Github account

When working with a GitHub repository, you will often need to identify yourself to GitHub using your username and password. An **SSH key** is an alternate way to identify yourself that doesn't require you to enter you username and password every time.

SSH keys come in pairs, a public key that gets shared with services like GitHub, and a private key that is stored only on your computer. If the keys match, you are granted access.

The cryptography behind SSH keys ensures that no one can reverse engineer your private key from the public one.

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

## Checking for existing SSH keys

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

1. Open terminal

2. Enter `ls -al ~/.ssh` to see if existing SSH keys are present. This command lists the files in your `.ssh` directory, if they exist

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.

```console
id_rsa.pub
id_ecdsa.pub
id_ed25519.pub
```

## No existing SSH keys

If you don't already have an SSH key, you must generate a new SSH key to use for authentication.

First of all we need to create the directory where the key can be stored, if not already existing.

```bash
mkdir "$HOME/.ssh"
```

Then generate the ssh key.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

If you are using a legacy system that doesn't support the Ed25519 algorithm, use this instead.

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

So in the above commands, `your_email@example.com` should be replaced with the primary email that you had used to create your Github account.

This creates a new SSH key, using the provided email as a label.


## Generating public/private algorithm key pair.

```console
> Enter a file in which to save the key (/Users/you/.ssh/id_algorithm): [Press enter]
```

When you are prompted to **Enter a file in which to save the key** press Enter. This accepts the default file location.


```console
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

At the prompt, type a secure passphrase. For more information, refer to [Working with SSH key passphrases](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases).

## Add your SSH key to the ssh-agent

`ssh-agent` is a program that stores your private keys. It starts when you log in. We will add a copy of our private key to this SSH agent.

Follow [this detailed article by Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) to add ssh key to `ssh-agent`.

## Add your public SSH key to GitHub

This is the final step. We will add the generated ssh key to Github.

Follow [this detailed article by Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to add ssh key to your Github account.

## Verifying

As to verify everything is working as intended, we can run the following in the terminal.


```bash
ssh -T git@github.com
```


And it should ideally output something like this.

```console
Hi "your-name"! You've successfully authenticated, but GitHub does not provide shell access.
```

### BigBinary Git Best Practices - Staging and Aliases

**Enforcing `git add --patch`** 

At BigBinary, we enforce using `git add --patch` to review and stage changes selectively. This helps maintain clarity in commits and avoids unrelated changes being grouped together.

**Using Aliases Consistently**

Aliases can significantly simplify repetitive git commands. To maintain consistency across teams, we encourage setting up standard git aliases for common commands. 

For example:

- `git add --patch` can be shortened to `gapa`.
- `git commit --message` can be shortened to `gcmsg`.

For a more comprehensive list of useful Git aliases, refer to the [Oh My Zsh Git Plugin documentation](https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/README.md). This resource provides a curated set of aliases to optimize your git experience.



### Introduction to Git

Git is a version control system. Git acts like a time machine because it allows us to track every change we make and it allows us to go to the previous version. It's not exactly like Undo in google doc but it's pretty close. After making the code change we need to commit the code. Commiting the code means in the future if I want then I can come back to this point.

Besides tracking code change Git allows us to do "branching" and "merging". "Branching" allows us to duplicate the source code for yourself but in a diferent branch. So that we can make code change fearlessly.

Once we are happy with our change then we can "merge" the branch.

Git does all this locally on your computer. However the danger is that if the laptop fails then the source code would be lost. That's where GitHub comes in the picture. We can push our code to GitHub to do two things. The first one is that our code is protected even if the laptop is lost. Secondly other team members can pull down the code written by other team members and this facilitates collaboration.

### Workflow of Git

Let's look at this picture.

![git-basic-workflow](https://github.com/user-attachments/assets/2ab70d33-6a4d-4e04-917b-967e9c49ebd4)

Here "Local" means your laptop and Remote means GitHub.

As the diagram suggests most of the time we are in our "working directory". We can use "git add" to put our changed code in "staging area". This is a temporary area. This changes made and put in "staging area" are not permanent and we can't revert back to those changes. To go back to a change first we need to make the code go from "staging area" to "localrepo" and that's done using "git commit".

Once the commit has been made and we want to share that code with our team members then we can push that change to GitHub.

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

We should see output something like this.

```console
Hi "your-name"! You've successfully authenticated, but GitHub does not provide shell access.
```

### BigBinary Git Best Practices

Given below are two aliases. Both of these aliases are part of
[Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/README.md).

#### Using aliase gapa for `git add --patch`

At BigBinary we don't want anyone to be using `git add .`. That should be reserved for special occassions. Similarly we don't want anyone to be using any GUI to see the diff and then to stage the diff. The BigBinary recommended way is to use `git add -patch` and the alias for that is `gapa`.

### Using shortcut gcmsg for `git commit --message`

In our lifetime we'll be writing a lot of git commit messages. Writing `git commit --message` could be tedious. `gcmsg` is a good alias.
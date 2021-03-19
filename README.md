# git-newbie-playground
This is a repository for Git newbies to fork and play with. 

# Setup Git and GitHub

## Create GitHub account
- Create a GitHub account if you have not already: https://github.com/join
- Create a **private** repository called `my-private-repo`: https://github.com/new . Make sure to tick the "Add a README file" box.

## Install Git

### Windows
- install Git: https://git-scm.com/download/win
- If you have Git installed already, please make sure that you have at **least version 2.29** (required for storing credentials securely): 
```
git version 
```
If you do not have at least version `2.29`, please update Git: 

```
git update-git-for-windows
```

### Mac
- install Git, see [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### Linux
- Git should already be installed on your machine. To check, please run: 
```
git version
```
If not, please google "install git {your distro}" and you should find out how to install it.

## Introduce yourself to Git

Open a terminal (Mac / Linux) or Git Bash (Windows).

Copy each of the following commands, adapt the name and email address (the email address should be the address you used for your GitHub account), and hit enter.

```
git config --global user.name 'Jane Doe'
git config --global user.email 'jane@example.com'
git config --global alias.graph 'log --graph --oneline'
git config --global --list
```

## Authentication

### Create a Personal Access Token
- https://github.com/settings/tokens
- give it a name like "personal laptop" 
- copy the token somewhere temporary - but don't save it!

Now, we have to store the Personal Access Token on our Laptop and tell Git to use it when communicating with GitHub. In order to do so, we need a Git "credential helper".

### Windows and Mac

**Mac**: On Mac, install [Git Credential Manager Core](https://github.com/microsoft/Git-Credential-Manager-Core/releases/tag/v2.0.394-beta) by downloading and executing the `pkg` installer. 

Open Git Bash (on Windows) or the Terminal (on Mac)

Copy+paste the following command and hit enter: 

```
git credential-manager-core configure
```

this tells git to use the [credential-manager-core](https://github.com/microsoft/Git-Credential-Manager-Core) as the _credential store_.


we need to _trigger_ the credential store, so let's clone ("download") your private repository `my-private-repo` that you created before:

```
git clone https://github.com/{your_github_username}/my-private-repo
```

It will look something like this. Make sure to select option 2 by typing in "2" and hitting enter. Then paste your PAT:

![](images/core-cred-manager.png)

Hit enter. Git should clone your repository. You can confirm it is there by running `ls` - `my-private-repo` should be in the list.

### Linux 

You should use the `libsecret` package, see [this article](https://www.softwaredeveloper.blog/git-credential-storage-libsecret)

If this is not an option on your Linux distro, you can: 
- install [Git Credential Manager Core](https://github.com/microsoft/Git-Credential-Manager-Core#linux-debian-package-deb)  and then follow the instructions for Mac/Windows above
- use SSH authentication: 

1. Check for pre-existing keys: open a terminal, enter `ls ~/.ssh`
2. create key if none exists:
`ssh-keygen -t rsa -C "your_email@example.com"`  (replace with email you used for GitHub registration!), accept defaults (default location, no password)
3. copy to GitHub 
- copy the public key from `id_rsa.pub`
  - Linux: `cat ~/.ssh/id_rsa.pub` -> copy the output 
- add to GitHub
  - go to the [SSH keys](https://github.com/settings/keys) section of the GitHub settings and copy your key into the box. Give a meaningful name and click "add key"
  

# Markdown syntax

- **bold**
- _italic_
- ~~strike~~
### subheader

> this is a quote

this links an image from the images folder

![description](images/xkcd_comic.png)

image from the web

![description](https://imgs.xkcd.com/comics/correlation.png)

Source: https://imgs.xkcd.com/comics/correlation.png

merge conflicts might be a bit frightening but you can do it! :) 


---
creation date: 2021-06-04 11:48
modification date: Friday 4th June 2021 11:48:16
tags: ["#note"]
author: Jimmy Briggs
---

# WSL

## Setup SSH and Git

- Install and Configure Git:

```bash
sudo apt-get install git
git config --global user.name "Jimmy Briggs"
git config --global user.email "jimbrig2011@outlook.com"
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager-core.exe"
```

- Link Windows `~/.ssh` to Linux `~/.ssh` :

```bash
cp -r /mnt/c/Users/Admin/.ssh ~/.ssh
chmod 600 ~/.ssh/id_rsa
```


## Github-CLI

```bash
VERSION=`curl  "https://api.github.com/repos/cli/cli/releases/latest" | grep '"tag_name"' | sed -E 's/.*"([^"]+)".*/\1/' | cut -c2-`

wget https://github.com/cli/cli/releases/download/v${VERSION}/gh_${VERSION}_linux_amd64.tar.gz
 
tar xvf gh_${VERSION}_linux_amd64.tar.gz

sudo cp gh_${VERSION}_linux_amd64/bin/gh /usr/local/bin/

ls gh_${VERSION}_linux_amd64/share/man/man1/

gh auth login
```

## Homebrew

https://docs.brew.sh 

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- Add Homebrew to your PATH: 


```bash
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/jimbrig/.profile

eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

brew help

sudo apt-get install build-essential
brew install gcc

```
- `/home/jimbrig/.profile`                                                     echo 'eval " $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/jimbrig/.profile                eval "$ (/home/linuxbrew/. Linuxbrew/bin/brew shellenv)"                                             - Run ` brew help ` to get started                                                                       - Further documentation:                                                                                   https://docs.brew.sh                                                                               - Install the Homebrew dependencies if you have sudo access:                                               sudo apt-get install build-essential                                                                   See https://docs.brew.sh/linux for more information                                                - We recommend that you install GCC:                                                                       brew install gcc                 

## GPG

```bash
brew install gpg
```

## Keybase

```bash
brew install --cask keybase
```

```bash
curl --remote-name https://prerelease.keybase.io/keybase_amd64.deb


sudo apt install ./keybase_amd64.deb

run_keybase
```

```bash
keybase login
keybase pgp gen --multi

gpg --list-secret-keys --keyid-format LONG

git config --global user.signingkey E870EE00
git config --global commit.gpgsign true
```
***
Links: 
Source:


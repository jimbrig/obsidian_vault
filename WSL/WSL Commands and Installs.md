---
creation date: 2021-05-01 20:04
modification date: Saturday 1st May 2021 20:04:32
tags: ["#dev"]
author: Jimmy Briggs
---

# WSL Commands and Installs

## Initial WSL Installations

- Update, upgrade, and cleanup  `apt` packages library
- Install `build-essential`, `autoconf`, and `libtool`
- Install `python`, `gcloud sdk`, and `github-cli` (Python, Git, and Bash should already be included with installation and upgraded in step 1 above)

```
sudp apt update && sudo apt upgrade && sudo apt autoclean 
sudo apt-get install build-essential autoconf libtool
```

## Install gcloud sdk

Follow the instruction below to install the Cloud SDK:

1.  Add the Cloud SDK distribution URI as a package source:
    
```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

sudo apt-get install apt-transport-https ca-certificates
    
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
```
    
2.  Update and install the Cloud SDK:
    
```bash
sudo apt-get update && sudo apt-get install google-cloud-sdk
```

3. Run `gcloud init` to initialize the SDK:

```bash
gcloud init
```

## Install Python

## Install Node.js

## Install Github-CLI

## Install Git



## New WSLg GUI Applications

- Install Edge with new [WSLg](https://github.com/windows/wslg) version of WSL that supports GUI applications natively.

```bash
sudo apt update && sudo apt upgrade
sudo curl https://packages.microsoft.com/repos/edge/pool/main/m/microsoft-edge-dev/microsoft-edge-dev_91.0.852.0-1_amd64.deb -o /tmp/edge.deb
sudo apt install /tmp/edge.deb \-y
```

- Install RStudio:

```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/"
sudo apt update
sudo apt install r-base
sudo apt-get install gdebi-core
wget https://download1.rstudio.org/desktop/bionic/amd64/rstudio-1.2.5042-amd64.deb
sudo gdebi rstudio-1.2.5042-amd64.deb
```

***
Links: 
Source:


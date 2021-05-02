---
creation date: 2021-05-01 20:04
modification date: Saturday 1st May 2021 20:04:32
tags: ["#dev"]
author: Jimmy Briggs
---

# WSL Commands and Installs

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


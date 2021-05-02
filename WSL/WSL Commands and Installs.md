---
creation date: 2021-05-01 20:04
modification date: Saturday 1st May 2021 20:04:32
tags: ["#dev"]
author: Jimmy Briggs
---

# WSL Commands and Installs

- Install Edge with new [WSLg](https://github.com/windows/wslg) version of WSL that supports GUI applications natively.

```bash
sudo apt update && sudo apt upgrade
sudo curl https://packages.microsoft.com/repos/edge/pool/main/m/microsoft-edge-dev/microsoft-edge-dev_91.0.852.0-1_amd64.deb -o /tmp/edge.deb
sudo apt install /tmp/edge.deb \-y
```

***
Links: 
Source:


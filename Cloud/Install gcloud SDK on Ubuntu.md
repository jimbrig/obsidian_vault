---
creation date: 2021-05-04 19:40
modification date: Tuesday 4th May 2021 19:40:23
tags: ["#note"]
author: Jimmy Briggs
---

# Install gcloud SDK on Ubuntu

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

***
Links: 
Source:


---
creation date: 2021-05-15 15:39
modification date: Saturday 15th May 2021 15:39:06
tags: ["#note"]
author: Jimmy Briggs
---

# GCP API Services Notes

```bash

gcloud services enable [SERVICE]

```

## GCP Service Accounts

### Compute Instance Permissions

1. `Navigation Menu > Compute Engine > VM Instances` then click `Create`
2. Notice `Identity and API Access` section
3. Select Service Account
4. Select Access Scope - will not be visible if a custom Service Account is chosen

### Create Service Account - Best Practice

- Navigation Menu > IAM & Admin > Service Accounts > Create Service Account
- Enter details for `Name` and `Description`
- Grant `Roles`
- Grant yourself permission to use the service account
***
Links:  [[GCP]] | [[Google Cloud APIs]] | [[Docker]] | [[GCP Services Table]] | [[Google Cloud Setup Notes]]
Source: [Github: ivan/curada/Awesome-GCP](https://github.com/ivan-curada/Awesome-GCP)
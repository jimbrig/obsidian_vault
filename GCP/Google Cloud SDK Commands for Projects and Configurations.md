---
creation date: 2021-05-15 15:43
modification date: Saturday 15th May 2021 15:43:53
tags: ["#note"]
author: Jimmy Briggs
---

# Google Cloud SDK Commands for Projects and Configurations
## Accounts

List active account name

```cli
gcloud auth list
```

## Projects

- <https://cloud.google.com/sdk/gcloud/reference/projects>
- create and manage IAM policies for projects in GCP

``` cli
List all project associated with account

$ gcloud projects list


Create a new project
Google Cloud Project IDs need to be unique accross ALL projects by ALL users

$ gcloud projects create [unique-project-name] --folder [organization-folder]

$ gcloud projects create [PROJECT_ID] [--no-enable-cloud-apis] [--folder=FOLDER_ID] [--labels=[KEY=VALUE,…]] [--name=NAME] [--organization=ORGANIZATION_ID] [--set-as-default] [GCLOUD_WIDE_FLAG …]


Check current project

$ gcloud config get-value project


Change project

$ gcloud config set project [project-ide]


Get full URI

$ gcloud projects list --uri


Update Project Name

$ gcloud projects update [PROJECT_ID] --name [NEW_NAME]
```

## Configuration

- <https://cloud.google.com/sdk/gcloud/reference/config>
- set, view, and unser properties used by Cloud SDK
- a set of properties tha govern the behavior of gcloud and other cloud SDK tools.

``` cli

gcloud config GROUP | COMMAND [GCLOUD_WIDE_FLAG …]

Show current configuration properties (account and project)

$ gcloud config list 

> [core]
account = myemail@gmail.com
disable_usage_reporting = True
project = project_id

Your active configuration is: [default]


Show current configuration

$ gcloud config configuration list

> NAME          IS_ACTIVE  ACCOUNT  PROJECT                 DEFAULT_ZONE  DEFAULT_REGION
[configuration] True                practice-258411


Create a new configuration

$ gcloud config configurations create [configuration_name]


Switch between different configurations

$ gcloud config configurations activate [CONFIGURATION_NAME]


List project ID

$ gcloud config list project

```

## Accounts

``` cli
Set a different account for our new configuration

$ gcloud auth login


Checl current account

$ gcloud config get-value account
```


***
Links:  [[GCP]] | [[Google Cloud APIs]] | [[Docker]] | [[GCP Services Table]] | [[Google Cloud Setup Notes]]
Source: [Github: ivan/curada/Awesome-GCP](https://github.com/ivan-curada/Awesome-GCP)
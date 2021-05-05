---
creation date: 2021-05-04 19:40
modification date: Tuesday 4th May 2021 19:40:23
tags: ["#gcp", "#dev"]
author: Jimmy Briggs
---

# Install gcloud SDK on Ubuntu

## Quick Start

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

## In Depth

**Note:** Depending on your setup, you can choose other installation methods:

-   If you use Snap on your system, you can install Cloud SDK as a [snap package](https://cloud.google.com/sdk/docs/downloads-snap)
-   If you're using an instance on Google Compute Engine, Cloud SDK is installed by default.

**Package contents**

Cloud SDK is available in package format for installation on Debian and Ubuntu systems. This package contains the `gcloud`, `gcloud alpha`, `gcloud beta`, `gsutil`, and `bq` commands only. It does not include `kubectl` or the App Engine extensions required to deploy an application using `gcloud` commands. If you want these components, you must install them separately as described later in this section.

**Prerequisites**

Before you install Cloud SDK, make sure that your operating system is one of the following:

-   Ubuntu release that has not reached [end-of-life](https://wiki.ubuntu.com/Releases)
-   Debian [stable release](https://wiki.debian.org/DebianReleases) from Wheezy forward

**Installation**

1.  Add the Cloud SDK distribution URI as a package source:
    
```bash
echo "deb \[signed-by=/usr/share/keyrings/cloud.google.gpg\] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee \-a /etc/apt/sources.list.d/google\-cloud\-sdk.list
```

Make sure you have [apt-transport-https](https://packages.debian.org/jessie/apt-transport-https) installed:
    
```bash
sudo apt\-get install apt\-transport\-https ca\-certificates gnupg
```

**Note:** If your distribution does not support the signed-by option run this command instead:
    
```bash
echo "deb https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee \-a /etc/apt/sources.list.d/google\-cloud\-sdk.list
```

**Note:** Make sure you do not have duplicate entries for the cloud-sdk repo.
    
2.  Import the Google Cloud public key:

```bash
curl https://packages.cloud.google.com/apt/doc/apt\-key.gpg | sudo apt\-key \--keyring /usr/share/keyrings/cloud.google.gpg add \-
```
    
    
    **Note:** If you are unable to get latest updates due to an expired key, [obtain the latest apt-get.gpg key file](https://cloud.google.com/compute/docs/troubleshooting/known-issues#keyexpired).
    
    **Note:** If your distribution's apt-key command does not support the --keyring argument run this command instead:
    
    curl https://packages.cloud.google.com/apt/doc/apt\-key.gpg | sudo apt\-key add \-
    
3.  Update and install the Cloud SDK:
    
    sudo apt\-get update && sudo apt\-get install google\-cloud\-sdk
    
    For additional `apt-get` options, such as disabling prompts or dry runs, refer to the [`apt-get` man pages](https://linux.die.net/man/8/apt-get).
    
    **Docker Tip:** If installing the Cloud SDK inside a Docker image, use a single RUN step instead:
    
    RUN echo "deb \[signed-by=/usr/share/keyrings/cloud.google.gpg\] http://packages.cloud.google.com/apt cloud-sdk main" | tee \-a /etc/apt/sources.list.d/google\-cloud\-sdk.list && curl https://packages.cloud.google.com/apt/doc/apt\-key.gpg | apt\-key \--keyring /usr/share/keyrings/cloud.google.gpg  add \- && apt\-get update \-y && apt\-get install google\-cloud\-sdk \-y 
    
4.  Optionally, install any of these [additional components](https://cloud.google.com/sdk/docs/components#additional_components):
    
    -   `google-cloud-sdk-app-engine-python`
    -   `google-cloud-sdk-app-engine-python-extras`
    -   `google-cloud-sdk-app-engine-java`
    -   `google-cloud-sdk-app-engine-go`
    -   `google-cloud-sdk-bigtable-emulator`
    -   `google-cloud-sdk-cbt`
    -   `google-cloud-sdk-cloud-build-local`
    -   `google-cloud-sdk-datalab`
    -   `google-cloud-sdk-datastore-emulator`
    -   `google-cloud-sdk-firestore-emulator`
    -   `google-cloud-sdk-pubsub-emulator`
    -   `kubectl`
    
    For example, the `google-cloud-sdk-app-engine-java` component can be installed as follows:
    
    sudo apt\-get install google\-cloud\-sdk\-app\-engine\-java
    
5.  Run [`gcloud init`](https://cloud.google.com/sdk/gcloud/reference/init) to get started:
    
    gcloud init
    

**Downgrading Cloud SDK versions**

If you'd like to revert to a specific version of Cloud SDK, where `VERSION` is of the form `123.0.0`, run: `sudo apt-get update && sudo apt-get install google-cloud-sdk=123.0.0-0` The most recent ten releases will always be available in the repo.

## Optional: Install the latest Google Cloud Client Libraries

You can download [Cloud Client Libraries](https://cloud.google.com/sdk/cloud-client-libraries) for supported languages.

## Initializing the Cloud SDK

Use the [`gcloud init`](https://cloud.google.com/sdk/gcloud/reference/init) command to perform several common Cloud SDK setup tasks. These include authorizing the Cloud SDK tools to access Google Cloud using your user account credentials and setting up the default configuration.

To initialize the Cloud SDK:

1.  Run the following at a command prompt:
    
    ```
    gcloud init
    ```
    
    **Note:** To prevent the command from launching a web browser, use `gcloud init --console-only` instead. To authorize without a web browser and non-interactively, create a service account with the appropriate scopes using the [Google Cloud Console](https://console.cloud.google.com/) and use `gcloud auth activate-service-account` with the corresponding JSON key file.
    
2.  Accept the option to log in using your Google user account:
    
    To continue, you must log in. Would you like to log in (Y/n)? Y 
3.  In your browser, log in to your Google user account when prompted and click **Allow** to grant permission to access Google Cloud resources.
    
4.  At the command prompt, select a Google Cloud project from the list of those where you have **Owner**, **Editor** or **Viewer** permissions:
    
    Pick cloud project to use:
     \[1\] \[my-project-1\]
     \[2\] \[my-project-2\]
     ...
     Please enter your numeric choice: 
    
    If you only have one project, `gcloud init` selects it for you.
    
    If you have access to more than 200 projects, you will be prompted to enter a project id, create a new project, or list projects.
    
    This account has a lot of projects! Listing them all can take a while.
     \[1\] Enter a project ID
     \[2\] Create a new project
     \[3\] List projects
    Please enter your numeric choice: 
    
    **Note:** If you choose to create a project, you'll also need to [enable billing on your project](https://cloud.google.com/billing/docs/how-to/modify-project) to use Google Cloud services.
    
5.  If you have the Google Compute Engine API enabled, `gcloud init` allows you to choose a default Compute Engine zone:
    
    Which compute zone would you like to use as project default?
     \[1\] \[asia-east1-a\]
     \[2\] \[asia-east1-b\]
     ...
     \[14\] Do not use default zone
     Please enter your numeric choice: 
    
    `gcloud init` confirms that you have complete the setup steps successfully:
    
    gcloud has now been configured!
    You can use \[gcloud config\] to change more gcloud settings.
    
    Your active configuration is: \[default\] 
6.  (Optional) If you'd like a more streamlined screen reader experience, the gcloud command-line tool comes with an `accessibility/screen_reader` property.
    
    To enable this property, run:
    
    ```
    gcloud config set accessibility/screen_reader true
    ```
    
    For more details about the accessibility features that come with the gcloud command-line tool, refer to the [Enabling accessibility features](https://cloud.google.com/sdk/docs/enabling-accessibility-features) guide.
    

## Running core commands

Run these `gcloud` commands to view information about your Cloud SDK installation:

1.  To list accounts whose credentials are stored on the local system:
    
    ```
    gcloud auth list
    ```
    
    `gcloud` displays a list of credentialed accounts:
    
     Credentialed Accounts
    ACTIVE             ACCOUNT
    \*                  example-user-1@gmail.com
                       example-user-2@gmail.com 
2.  To list the properties in your active Cloud SDK configuration:
    
    ```
    gcloud config list
    ```
    
    `gcloud` displays the list of properties:
    
    \[core\]
    account = example-user-1@gmail.com
    disable\_usage\_reporting = False
    project = example-project 
3.  To view information about your Cloud SDK installation and the active configuration:
    
    ```
    gcloud info
    ```
    
    `gcloud` displays a summary of information about your Cloud SDK installation. This includes information about your system, the installed components, the active user account and current project, and the properties in the active configuration.
    
4.  To view information about `gcloud` commands and other topics from the command line:
    
    ```
    gcloud help
    ```
    
    For example, to view the help for `gcloud compute instances create`:
    
    ```
    gcloud help compute instances create
    ```
    
    `gcloud` displays a help topic that contains a description of the command, a list of command flags and arguments, and examples of how to use it.
    

## What's next

-   Read the [gcloud command-line tool guide](https://cloud.google.com/sdk/gcloud) for an overview of the gcloud command-line tool, including a quick introduction to key concepts, command conventions, and helpful tips.
-   Read the [gcloud command-line tool reference guide](https://cloud.google.com/sdk/gcloud/reference) for detailed pages on each `gcloud` command, including descriptions, flags, and examples, that you can use to perform a variety of tasks on Google Cloud.
-   Refer to the [gcloud command-line tool cheat sheet](https://cloud.google.com/sdk/docs/cheatsheet) for a list of commonly used commands and key concepts.
-   Install additional components such as the App Engine emulators or `kubectl` using the [Cloud SDK component manager](https://cloud.google.com/sdk/gcloud/guide/managing-components).

***
Links: [[Cloud/Google Cloud Setup Notes]]
Source: 
- [Useful Google Cloud Platform Commands Cheat Sheet](https://chriskyfung.github.io/blog/qwiklabs/useful-google-cloud-platform-commands-cheat-sheet)
- [Installing Google Cloud SDK  |  Cloud SDK Documentation](https://cloud.google.com/sdk/docs/install)

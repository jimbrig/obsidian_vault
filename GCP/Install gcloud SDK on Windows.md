---
creation date: 2021-05-04 19:44
modification date: Tuesday 4th May 2021 19:44:50
tags: ["#gcp", "#dev"]
author: Jimmy Briggs
---

# Install gcloud SDK on Windows

1.  Download the [Cloud SDK installer](https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe).
    
    Alternatively, open a PowerShell terminal and run the following PowerShell commands.
    
```powershell
(New\-Object Net.WebClient).DownloadFile("https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe", "$env:Temp\\GoogleCloudSDKInstaller.exe")

& $env:Temp\\GoogleCloudSDKInstaller.exe 
```

2.  Launch the installer and follow the prompts. The installer is signed by Google LLC.
    
    If you'd like to enable screen reader mode, select the **Turn on screen reader mode** option for a more streamlined screen reader experience. To read more about the Cloud SDK screen reader experience, refer to the [Accessibility features guide](https://cloud.google.com/sdk/docs/enabling-accessibility-features).
    
    ![Google Cloud SDK Setup welcome dialog for Windows with checkbox for enabling screen reader mode](https://cloud.google.com/sdk/docs/images/screen-reader-mode.png)
    
3.  Cloud SDK requires Python; supported versions are Python 3 (preferred, 3.5 to 3.8) and Python 2 (2.7.9 or higher).
    
    The installer will install all necessary dependencies, including the needed Python version. While Cloud SDK currently uses Python 3 by default, you can use an existing Python installation if necessary by **unchecking** the option to Install Bundled Python.
    
4.  After installation has completed, the installer presents several options:
    
    ![Windows installer prompts](https://cloud.google.com/sdk/images/windows-installer-prompt.png)
    
    Make sure that the following are selected:
    
    -   **Start Google Cloud SDK Shell**
    -   **Run `gcloud init`**
    
    The installer starts a terminal window and runs the [`gcloud init`](https://cloud.google.com/sdk/gcloud/reference/init) command.
    
5.  The default installation does not include the App Engine extensions required to deploy an application using `gcloud` commands. These components can be installed using the [Cloud SDK component manager](https://cloud.google.com/sdk/docs/managing-components).

**Troubleshooting tips:**

-   If the Cloud SDK fails to run after installing version 274.0.0, please refer to this [tracking bug](https://issuetracker.google.com/issues/146458519) for the latest workarounds.
-   If your installation is unsuccessful due to the `find` command not being recognized, ensure your `PATH` environment variable is set to include the folder containing `find`. Usually, this is `C:\WINDOWS\system32;`.
-   If you have just uninstalled Cloud SDK, you will need to reboot your system before installing Cloud SDK again.

### Optional: Install the latest Google Cloud Client Libraries

You can download [Cloud Client Libraries](https://cloud.google.com/sdk/cloud-client-libraries) for supported languages.

## Other installation options

Depending on your development needs, instead of the [recommended installation](https://cloud.google.com/sdk/docs/install#installation_instructions), you can use an alternative method of installing Cloud SDK:

-   **Using Cloud SDK with scripts or Continuous Integration/Deployment?** Download a [versioned archive](https://cloud.google.com/sdk/docs/downloads-versioned-archives) for a non-interactive installation of a specific version of Cloud SDK.
-   **Need to run Cloud SDK as a Docker image?** Use the [Cloud SDK Docker image](https://cloud.google.com/sdk/docs/downloads-docker) for the latest release (or specific version) of Cloud SDK.
-   **Running Ubuntu and prefer automatic updates?** Use a [snap package](https://cloud.google.com/sdk/docs/downloads-snap) to install the Cloud SDK.
-   For Windows and macOS interactive installations, and all other use cases, run the [interactive installer](https://cloud.google.com/sdk/docs/downloads-interactive) to install the latest release of Cloud SDK.

## What's in the box?

All of the installation methods above install the default Cloud SDK components, which include `gcloud`, `gsutil` and `bq` command-line tools.

You can [install additional components](https://cloud.google.com/sdk/gcloud/guide/managing-components) using the `gcloud components install` command, or by installing the appropriate deb or RPM packages.

## Managing an installation

After you have installed Cloud SDK, you can use commands in the [`gcloud components`](https://cloud.google.com/sdk/gcloud/reference/components) command group to [manage your installation](https://cloud.google.com/sdk/gcloud/guide/managing-components). This includes viewing installed components, adding and removing components, and upgrading to a new version (or downgrading to a specific version) of Cloud SDK.

**Note:** Updating and removing components using `gcloud components` is disabled if you installed Cloud SDK using _apt-get_ or _yum_. To manage the Cloud SDK in this case, continue using the package management tool used during installation.

## Older versions of Cloud SDK

If you'd need an older version of Cloud SDK to revert to, you can find all previous releases available to download from [this archive](https://storage.cloud.google.com/cloud-sdk-release).

***
Links: [[Install gcloud SDK on Ubuntu]] | [[GCP/Google Cloud Setup Notes]]
Source: [Installing Google Cloud SDK  (Windows) |  Cloud SDK Documentation](https://cloud.google.com/sdk/docs/install#windows)


---
creation date: 2021-04-28 10:15
modification date: Wednesday 28th April 2021 10:15:09
tags: ["#gcp", "dev"]
author: Jimmy Briggs
---

# Google Cloud Setup Notes

## Environment Setup and Configuration

1. In the [Google Cloud Console](https://console.cloud.google.com/), select or create a GCP project.
   - [Project Selector Page](https://console.cloud.google.com/projectselector2/home/dashboard?_ga=2.153494008.1742946965.1610938789-26772365.1609112598)
2. Ensure [Billing is Enabled](https://cloud.google.com/billing/docs/how-to/modify-project) for the project.
3. [Enable the Cloud Run API](http://console.cloud.google.com/apis/library/run.googleapis.com?_ga=2.220194521.1742946965.1610938789-26772365.1609112598).
4. [Install and Initialize `gcloud` SDK](https://cloud.google.com/sdk/docs/) on local machine.
   - On windows run, `cinst gcloud` if using Chocolatey.
   - Update components via `gcloud components update`
5. Authenticate GCP (two methods):
   - Using a dedicated `service account`

***
Links: 
Source:


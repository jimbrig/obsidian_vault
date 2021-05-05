---
creation date: 2021-05-04 20:12
modification date: Tuesday 4th May 2021 20:12:33
tags: ["#note"]
author: Jimmy Briggs
---

# Setup Cloud SQL for PostgreSQL in Production

## Deploying a Cloud SQL for PostgreSQL instance

You can set up a Cloud SQL for PostgreSQL instance in a few steps by using the Google Cloud Console or the `gcloud` command-line tool. 

Both methods are described here.

1.  Create the PostgreSQL instance:
    
```
gcloud sql instances create postgresql01 --cpu=2 --memory=7680MB --region=us-central1 --zone=us-central1-a
```
    
2.  Assign a password for the PostgreSQL default user (syntax example):

```powershell
gcloud sql users set-password postgres --instance <INSTANCE_NAME> --password <PASSWORD>
```
 
You can specify these additional options:
    
-   **Database version:** One of the supported PostgreSQL [versions](https://cloud.google.com/sql/docs/postgres/db-versions).
-   **Storage type:** Either SSD or HDD as the storage type.
-   **Storage capacity:** The initial storage settings for the instance.
-   **Automatic storage increase:** Cloud SQL automation for adding additional storage when free space runs low.
-   **High-availability:** Cloud SQL high-availability.
-   **Automatic backups:** The start-time window for backups.
-   **Point-in-time recovery:** Point-in-time recovery and write-ahead logging.
-   **Maintenance window:** A one-hour window when Cloud SQL can perform disruptive maintenance.
-   **Maintenance timing:** The preferred timing for performing updates on the PostgreSQL instance. You can specify **preview** for earlier updates or **production** for later updates.
-   **Database flags:** The PostgreSQL database flags for controlling settings and parameters.
    
The following `gcloud` command creates a Cloud SQL for PostgreSQL instance with some additional options:

```powershell
gcloud sql instances create postgresql01 --cpu=2 --memory=7680MB --region=us-central1 \    --zone=us-central1-a \    --database-version=POSTGRES_12 \    --storage-type=SSD \    --storage-size=100 \    --storage-auto-increase \    --availability-type=regional \    --backup-start-time=23:30 \    --enable-point-in-time-recovery \    --maintenance-window-day=sun \    --maintenance-window-hour=11 \    --maintenance-release-channel=production \    --database-flags max_connections=100
    ```
    
    For more information, see [Creating instances](https://cloud.google.com/sql/docs/postgres/create-instance#gcloud).

***
Links: [[Google Cloud APIs]] | [[GCP/Google Cloud Setup Notes]]
Source: [Setting up Cloud SQL for PostgreSQL for production use  |  Solutions (google.com)](https://cloud.google.com/solutions/setting-up-cloud-sql-for-postgresql-for-production)


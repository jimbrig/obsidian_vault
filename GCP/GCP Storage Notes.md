---
creation date: 2021-05-15 15:38
modification date: Saturday 15th May 2021 15:38:46
tags: ["#note"]
author: Jimmy Briggs
---

# GCP Storage Notes

## Cloud Storage Bucket Public Access

By default, **Not Public** access

2 main ways to control access

- Uniform Bucket Level Access
  - uses **Cloud IAM permissions** 
  - whole bucket and all of its objects
  - **GCP recommended practice** - < https://cloud.google.com/storage/docs/access-control#recommended_bucket_architecture>
- Fine Grained Access
  - uses **Access Control Lists**
    - legacy acces control system to set permissions at object level
  - created to have interoperability with AWS S3

## Bucket 

Bucket names are **globally unique.**

## Practicing IAM in GCP Cloud Storage

### Uniform Bucket Level Access

Bucket with Public Access
Bucket names are **globally unique.**

1. Navigation Menu > Storage > Browser > Click **Create Bucket**
2. **Choose how to control access to objects** Section > choose **Uniform**
3. **Bucket List** > **Kebab Menu** (3 vertical dot) of the Bucket > Edit bucket permissions
4. Choose the policy to be attached.

### Limited Access 

1. Navigation Menu > Storage > Browser > Click **Create Bucket**
2. **Choose how to control access to objects** Section > choose **Uniform**
3. **Bucket List** > **Kebab Menu** (3 vertical dot) of the Bucket > Edit bucket permissions
4. Choose the policy to be attached.

***
Links:  [[GCP]] | [[Google Cloud APIs]] | [[Docker]] | [[GCP Services Table]] | [[Google Cloud Setup Notes]]
Source: [Github: ivan/curada/Awesome-GCP](https://github.com/ivan-curada/Awesome-GCP)
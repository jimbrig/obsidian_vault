---
creation date: 2021-05-15 15:35
modification date: Saturday 15th May 2021 15:35:31
tags: ["#gpc", "#dev", "#cloud"]
author: Jimmy Briggs
---

# GCP IAM Notes

# GCP Identity and Access Maangement

<https://cloud.google.com/iam/docs/overview#how_cloud_iam_works >

## Main parts

### Member

Identity of a user is an email address associated with:

- a Google Account (for end users)
- a service account (for apps and virtual machines)
- a Google Group
- or a domain name associated with a GSuite or Cloud Identity Domain

### allUsers

<https://cloud.google.com/iam/docs/overview#allusers>

- represents anyone on the internet
    - authenticated users and unauthenticated users

### Role

- A **collection of permissions**.
- created per project or per organization
- **Permissions** determine what operations are allowed on a resource.
    - cannot be granted directly to an end user
- When you grant a role to a member, you grant all the permissions that the role contains.
- not an identity (AWS)

### Cloud IAM Policy

- binds one or more members to a role
- we give access to users by attaching a policy to a resource giving permission to a user
- defines *who* (**member**) has what type of access (**role**) on a resource
  - grants **roles** to an authenticaed user
- attached only to a resource not a user (**except service accounts with are both identities and resources**)

## Permissions

Describes the actions user can perform with a GCP resource.

``` cli
service.resource.verb

ex.
iam.roles.create
```

## Role Types

<https://cloud.google.com/iam/docs/understanding-roles#role_types >

### Primitive Roles

<https://cloud.google.com/iam/docs/understanding-roles#primitive_roles>

A Project creator is automatically given a primitive role **Owner.**
    - read/write permissions for the whole project and it's resources
    - can change permissions for resources/services
    - a pre-defined role

### Predefined Roles

- provides granular access
- managed by Google Cloud

### Custom Roles

- created by user
    - Project Owner has the **iam.roles.create** permission for a project to create Custom Roles

## Roles

### Storage Object Viewer

Read only permissions on the bucket

## etag

- used to as a concurrency mechanism when updating a role
- Whenever a role is created or update, it's etag is updated.
  - Any update role action must include the etag and must match the current etag in the role.
- This way if two user update a role at the same time, only one will succeed and the other update command will fail since the role will have a new etag

## Service Accounts and Access Scopes

If Service Accounts and Access Scopes do not match, permission is denied.

Best practice is to create a separate service account then attach the roles with the permissiosn you want to use for that instance.

### Service Accounts

<https://cloud.google.com/iam/docs/service-accounts#what_are_service_accounts>

`A service account is a special kind of account used by an application or a virtual machine (VM) instance, not a person. Applications use service accounts to make authorized API calls.`

- special identities used by compute instances, applciations to make authorized Google Cloud API calls
- they have an email address
- can only use public/private key pairs for authentication

- `Compute Engine defaults service account`
  - default Service account for VMs
  - can be shared by all the VM instances in the project
  - wil share permissions granted

### Access Scopes

- type and level of API access to grant the VM
- legacy authorization mechanism to may API calls
- uses Oauth
- if a different authentication protocol (gRPC) is used, the Access Scopes don't apply anymore

- default access
  - read access to Cloud Storage
  - write access to Stackdriver logging

### Best Practice

<https://cloud.google.com/compute/docs/access/service-accounts#associating_a_service_account_to_an_instance>

`As a result, a best practice is for you to set the full cloud-platform access scope on the instance, then securely limit your service account's access by granting IAM roles to the service account.`

***
Links:  [[GCP]] | [[Google Cloud APIs]] | [[Docker]] | [[GCP Services Table]] | [[Google Cloud Setup Notes]]
Source: [Github: ivan/curada/Awesome-GCP](https://github.com/ivan-curada/Awesome-GCP)


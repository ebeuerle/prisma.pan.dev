---
id: gcp_cloudstorage
title: Cloud Storage
sidebar_label: Cloud Storage
description: GCP Cloud Storage Queries
---

# Sample RQL Queries

:::note
The following guide will walk you through GCP Cloud Storage RQL Examples
:::

## List storage buckets set to "private" with object ACLs set to "public"

```bash
config where cloud.type = 'gcp' AND api.name = 'gcloud-storage-buckets-list' AND json.rule = 'iam.bindings[*] size greater than 0 and iam.bindings[*].members[*] any equal allUsers and acl[*].entity contains "allUsers"'
```

## List storage buckets not located in EU region

```bash
config where api.name = 'gcloud-storage-buckets-list' AND json.rule =  location does not contain eu and location does not contain EU
```
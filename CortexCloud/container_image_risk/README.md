# Container Image Risk Dashboard

## Description

This dashboard displays detected container images over time and where they are detected in the SDLC (runtime, build, deploy).

## Requirements

This script currently uses environment variables to authenticate against Prisma Cloud. In the future this may be changed to another method, but currently it is required to have the following 3 settings added as environment variables on the machine where you run the script. Alternatively you can edit the contents of [config.py](/modules/config.py).

 | drilldown |  setting  | type | description |
 |----|-----------|------|-------------|
 | PRISMA_CLOUD_URL | placeholder.com | `string` | 
 | PRISMA_CLOUD_IDENTITY | Prisma Cloud Identity | `string` | Username or access key with the ability to view and modify policy.
 | PRISMA_CLOUD_SECRET | Prisma Cloud Secret | `string` | Password for username or access key above


 runtime.xdr.jp.paloaltonetworks.com
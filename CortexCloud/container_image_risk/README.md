# Container Image Risk Dashboard

## Description

This dashboard displays detected container images over time and where they are detected in the SDLC (runtime, build, deploy).

## Requirements

> [!IMPORTANT]
> In order for the dashboard drilldowns to work, it is required to search/replace the dashboard.json for placeholder.com and replace with your tenant URL.
>
> - Example:
>    - Before: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory
>    - After: https://placeholder.com/assets/inventory


## Dashboard Screenshot

![Dashboard](dashboard.pngpng)

## Dashboard Widgets

 | widget |  name  | type | drilldown |
 |----|-----------|------|-------------|
 | Bar Chart | Container Images Detected Across SDLC | Time Series | `yes` | 
 | Table | Prisma Cloud Identity | `string` | Username or access key with the ability to view and modify policy.
 | Bar Chart | Prisma Cloud Secret | `string` | Password for username or access key above
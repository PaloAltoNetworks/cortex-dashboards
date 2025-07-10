# Contributing Guidelines

In order to maintain the quality and consistency of the dashboards, we have established the following guidelines.

- [Getting Started](#getting-started)
- [Required Steps](#required-steps)
    - [Create a Folder](#create-a-folder)
    - [Format Dashboard JSON](#format-dashboard-json)
    - [Create a Dashboard Screenshot](#create-a-dashboard-screenshot)
    - [Create a README](#create-a-readme)

- [XQL Formatting](#xql-structure)
- [Widget Documentation](#widget-documentation)
- [README Structure](#readme-structure)
- [Optional Steps](#optional-steps)

---

## Getting Started

To add a new dashboard start by [forking the repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo), creating a new branch, and then finally [submitting a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests).

---

## Required Steps

##### Create a Folder
- Create a new folder in the appropriate section for your dashboard

> [!NOTE] 
> The folder name should provide some detail about the dashboard, use only lowercase letters and _ as a separator
---
##### Format Dashboard JSON
- After exporting your dashboard from the console format your dashboard JSON file and name it dashboard.json

> [!TIP]
> Using a code formatter like [Prettier](https://prettier.io/) makes it easier to read and edit the JSON file

- Scrub your exported dashboard JSON file of any sensitive information (drilldowns using internal or tenant URL's, email addresses, etc.) before committing it.

> [!WARNING]
> If you have drilldowns that reference the URL of your tenant replace the tenant URL with: placeholder.com
> - Example:
>    - Before: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory
>    - After: https://placeholder.com/assets/inventory

---
##### Create a Dashboard Screenshot
- Take a screen shot of your dashbord and name it dashboard.png

> [!NOTE] 
> Ensure that the screenshot of your dashboard captures only the dashbord and not the entire browser window. It is recommended to collapse the left sidebar to maximize the dashboard.

> [!TIP]
> For large dashboards with lots of widgets and information use your browser zoom to increase the size of what is captured in the screenshot.

- Save the dashboard JSON file and screenshot in the folder you created

---
#### Create a README.md
- Create a new file named README.md in the folder and copy/paste the [README template](#readme-structure) into this file
- Edit the README.md file and replace the placeholders with the appropriate information

> [!NOTE]
> If your dasboard doesn't need any modifications just set the Requirements section to None and remove the existing markdown

- Make sure your folder contains only these 3 files:
    - README.md
    - dashboard.json
    - dashboard.png

---

## XQL Formatting

---

## Widget Documentation

---

## README Structure

```shell
## Container Image Risk Dashboard

- [Repository Files](#repository-files)
- [Description](#description)
- [Requirements](#requirements)
- [Dashboard Screenshot](#dashboard-screenshot)

---

#### Repository Files

 | Files |  Description |
 |----|----|
 | [README.md](README.md) | Dashboard Description |
 | [dashboard.json](dashboard.json) | Dashboard JSON |
 | [dashboard.png](dashboard.png) | Dashboard Screenshot |

---

#### Description

My dashboard details and description.

---

#### Requirements

> [!IMPORTANT]
> In order for the dashboard drilldowns to work, it is required to search/replace the dashboard.json for :point_right: `placeholder.com` and replace with your tenant URL.
>
> - Example:
>    - Before: https://placeholder.com/assets/inventory
>    - After: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory

---

#### Dashboard Screenshot

![Dashboard](dashboard.png)

```



[Country Flag Markdown Icons](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#flags)

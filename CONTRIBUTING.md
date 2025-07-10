# Contributing Guidelines

In order to maintain the quality and consistency of the dashboards, we have established the following guidelines.

- [Getting Started](#getting-started)
- [Required Steps](#required-steps)
    - [Create a Folder](#create-a-folder)
    - [Format Dashboard JSON](#format-dashboard-json)
    - [Create a Dashboard Screenshot](#create-a-dashboard-screenshot)
    - [Create a Readme](#create-a-readme)
    - [Edit Directory Readme](#edit-directory-readme)
- [XQL Formatting](#xql-structure)
    - [Line Breaks](#line-breaks)
    - [Joins](#joins)
    - [Code Comments](#code-comments)
- [Widget Documentation](#widget-documentation)
- [README Structure](#readme-structure)
- [Optional Steps](#optional-steps)

---

## Getting Started

To add a new dashboard start by [forking the repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo), creating a new branch, and then finally [submitting a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests).

## Required Steps

### Create a Folder
- Create a new folder in the appropriate section for your dashboard

> [!NOTE] 
> The folder name should provide some detail about the dashboard, use only lowercase letters and _ as a separator
---
### Format Dashboard JSON
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
### Create a Dashboard Screenshot
- Take a screen shot of your dashbord and name it dashboard.png

> [!NOTE] 
> Ensure that the screenshot of your dashboard captures only the dashbord and not the entire browser window. It is recommended to collapse the left sidebar to maximize the dashboard.

> [!TIP]
> For large dashboards with lots of widgets and information use your browser zoom to increase the size of what is captured in the screenshot.

- Save the dashboard JSON file and screenshot in the folder you created

---
### Create a README.md
- Create a new file named README.md in the folder and copy/paste the [README template](#readme-structure) into this file
- Edit the README.md file and replace the placeholders with the appropriate information

> [!NOTE]
> If your dasboard doesn't need any modifications just set the Requirements section to None and remove the existing markdown

- Make sure your folder contains only these 3 files:
    - README.md
    - dashboard.json
    - dashboard.png

---
### Edit Directory Readme

In the parent folder where your dashboadard is located, there is a directory listing of all the dashboards in that hierarchy. Fill in the required fields for your dashboard and insert it alphabetically. Your dashboard position in the table can be easily identified by looking at the folder structure as they are sorted alphabetically by default.

Example:
 | Dashboard Title |  Description  | Requires Updating URL's  | Contributor | Contributor Country |
 |---|---|---|---|---|
 | [Your Dashboard Name](your_folder_path/) | Your dashboard description. | [No | [Optional](#optional-steps)  | [Optional](#optional-steps) |


Copy/Paste:
```shell
 | [Your Dashboard Name](your_folder_path/) | Your_dashboard_description. | [Yes](#drilldown-url) |  |  |
```

---

## XQL Formatting

In order to maintain consistency across dashboards we have established the following guidelines for formatting your XQL queries. Although some of these tasks may seem duplicative and mundane, it is important to understand not everyone who will be using these queries has the same level of experience. Because of this code readability and in-code comments are important.

---

### Line Breaks

Try to separate  your queries into logical sections using line breaks. This will make it easier to read and edit your XQL queries. Although you can string together multiple XQL queries in a single line, it is recommended to break them up into separate lines for readability.

---

Bad
```js
dataset = asset_inventory | filter xdm.asset.type.category = "VM Instance" | fields xdm.asset.provider as Cloud | comp count() as Total by Cloud | alter Time = current_time() | target type = dataset append = true vm_instance_count
```

Good
```js
dataset = asset_inventory 
| filter xdm.asset.type.category = "VM Instance"
| fields xdm.asset.provider as Cloud
| comp count() as Total by Cloud
| alter Time = current_time()
| target type = dataset append = true vm_instance_count
```

---
### Joins

Joins by their nature tend to be complex and difficult to read. To make it easier to read and edit your joins, always start the line before the join with an empty comment //

Joins should also be split apart where after specifying the joined dataset you line break, issue your filter, fields, etc., and then specify the "as joinname" on the final line and finish with another line break.

---

Bad
```js
dataset = asset_inventory 
| filter xdm.asset.type.category = "VM Instance" 
| fields xdm.asset.id, xdm.asset.name 
| join (dataset = uvm_findings 
| filter asset_category = "VM Instance" 
| alter severity = arrayindex(split(cvss_severity, "_"), 2) 
| fields asset_name , asset_id , severity ) as joined joined.asset_id = xdm.asset.id 
| comp count() as CVE_COUNT by asset_id , severity
| sort desc asset_id 
```

Good
```js
dataset = asset_inventory 
| filter xdm.asset.type.category = "VM Instance" 
| fields xdm.asset.id, xdm.asset.name 
//
| join (dataset = uvm_findings 
| filter asset_category = "VM Instance" 
| alter severity = arrayindex(split(cvss_severity, "_"), 2) 
| fields asset_name , asset_id , severity 
) as joined joined.asset_id = xdm.asset.id 
//
| comp count() as CVE_COUNT by asset_id , severity
| sort desc asset_id 
```
---
### Code Comments

Try to document your XQL with comments. This will help others understand what your query is doing and why. This is especially important when you are working on a query that is complex or has a lot of joins.

Addiotionally, if there are parts of a query where you want to add functionality (filtering out certain items, etc.), but you don't want to add it by default, leave the command in, but commented out. For these scenarios follow the same advice as above with an empty comment above and below the code.

Example:
```js
//
// Optional: Exclude images from results by filtering out specific image names
//| filter asset_name not contains "cortex-agent"
//
```

---

Bad
```js
dataset = asset_inventory  
| filter xdm.asset.type.category = "VM Instance" 
| fields xdm.asset.normalized_fields, xdm.asset.name as Name, xdm.asset.id as asset_id 
| alter image_list = xdm.asset.normalized_fields -> ["xdm.asset.relations"][] 
| alter image_ids = arraymap(image_list, "@element"->["xdm.asset.relation.asset_id"]) 
| arrayexpand image_ids 
| comp count() as host_count by image_ids 
| join (dataset = asset_inventory 
| filter xdm.asset.type.category = "Container Image" 
| fields xdm.asset.id, xdm.asset.name 
) as asset_lookup asset_lookup.xdm.asset.id = image_ids 
| fields host_count , xdm.asset.name as image_name, xdm.asset.id as asset_id
| sort desc host_count 
| limit 20 
```

Good
```js
dataset = asset_inventory  // Search in asset inventory database
| filter xdm.asset.type.category = "VM Instance" // Only include types of VM Instance
| fields xdm.asset.normalized_fields, xdm.asset.name as Name, xdm.asset.id as asset_id // Only return these fields
| alter image_list = xdm.asset.normalized_fields -> ["xdm.asset.relations"][] // Parse JSON to return asset relationships
| alter image_ids = arraymap(image_list, "@element"->["xdm.asset.relation.asset_id"]) // Loop through asset relationship to return asset id's
| arrayexpand image_ids // List each unique asset id on it's own row
| comp count() as host_count by image_ids // Count and group image id's by the number of times they are seen on hosts
//
| join (dataset = asset_inventory // Join asset inventory data to add back fields removed by comp count()
| filter xdm.asset.type.category = "Container Image" // Only include types of Container Image
| fields xdm.asset.id, xdm.asset.name // Only return these fields
) as asset_lookup asset_lookup.xdm.asset.id = image_ids // Match asset id to image id
//
| fields host_count , xdm.asset.name as image_name, xdm.asset.id as asset_id // Only return these fields
| sort desc host_count // Sort by most images on a host first
| limit 20 // Limit to 20 results
```

---
## Widget Documentation

Make certain to include a descriptive name for your widgets, and a description of what the widget is showing. Although the description fields is not required for saving the widgets, in order for your PR to be accepted, the description must be included.

---
## Readme Structure

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

---
## Optional Steps

Add your name and/or country flag to the parent directory of your dashboard.

[Country Flag Markdown Icons](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#flags)

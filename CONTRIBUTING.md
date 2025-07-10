# Contributing Guidelines

In order to maintain the quality and consistency of the dashboards, we have established the following guidelines.

- [Getting Started](#getting-started)
- [Required Steps](#required-steps)
- [README Structure](#readme-structure)

---

## Getting Started

To add a new dashboard start by [forking the repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo), creating a new branch, and then finally [submitting a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests).

---

## Required Steps

Naming Conventions



- Create a **new folder** in the appropriate section for your dashboard using lowercase letters and _ as a separator
- the folder name should provide a deescription of the dashboard
- The folder should contain 3 files: 
    - README.md
    - dashboard.json
    - dashboard.png
- After exporting your dashboard from the console, format your dashboard JSON file (recommedned to use a code formater like [Prettier](https://prettier.io/))
- Scrub your exported dashboard JSON file of any sensitive information (drilldowns using internal or tenant URL's, email addresses, etc.) before sharing it.
> [!NOTE]
> If you have drilldowns that reference the URL of your tenant replace the tenant URL with: placeholder.com
> - Example:
>    - Before: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory
>    - After: https://placeholder.com/assets/inventory
- Ensure that the **screenshot** of your dashboard is clear and captures the essence of your dashboard.
- 

---

## README Structure


[Country Flag Markdown Icons](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md#flags)

# Contributing Guidelines

In order to maintain the quality and consistency of the dashboards, we have established the following guidelines:

To add a new dashboard start by [forking the repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo), creating a new branch, and then finally [submitting a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests).



1. Create a **new folder** for your dashboard using lowercase letters and _ as a separator.
2. The folder should contain 3 files: 
    - **README.md** - A description of your dashboard.
    - **dashboard.json** - The JSON code of your dashboard.
    - **dashboard.png** - A screenshot of your dashboard.
3. After exporting your dashboard from the console, format your dashboard JSON file (recommedned to use a code formater like [Prettier](https://prettier.io/))
4. Scrub your exported dashboard JSON file of any sensitive information (drilldowns using internal or tenant URL's, email addresses, etc.) before sharing it.
> [!NOTE]
> If you have drilldowns that reference the URL of your tenant replace the tenant URL with: placeholder.com
- Example:
    - Before: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory
    - After: https://placeholder.com/assets/inventory
5. Ensure that the **screenshot** of your dashboard is clear and captures the essence of your dashboard.
6.

## Container Image Risk Dashboard

- [Description](#description)
- [Repository Files](#repository-files)
- [Requirements](#requirements)
- [Dashboard Screenshot](#dashboard-screenshot)

---

#### Description

This dashboard displays detected container images over time and where they are detected in the SDLC (runtime, build, deploy).
Each detected container image is assigned a weighted risk score based on the number and severity of vulnerabilities detected.
The weighted risk score is calculated by the following formula:

$$\left(Critical \times 25\right) + \left(High \times 15\right) + \left(Medium \times 5\right) + \left(Low \times 1\right)$$

---

#### Repository Files

 | Files |  Description |
 |----|----|
 | [README.md](README.md) | Dashboard Description |
 | [dashboard.json](dashboard.json) | Dashboard JSON |
 | [dashboard.png](dashboard.png) | Dashboard Screenshot |

---

#### Requirements

> [!IMPORTANT]
> In order for the dashboard drilldowns to work, it is required to search/replace the dashboard.json for placeholder.com and replace with your tenant URL.
>
> - Example:
>    - Before: https://placeholder.com/assets/inventory
>    - After: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory

---

#### Dashboard Screenshot

![Dashboard](dashboard.png)
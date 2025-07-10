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

This dashboard displays detected container images over time and where they are detected in the SDLC (runtime, build, deploy).
Each detected container image is assigned a weighted risk score based on the number and severity of vulnerabilities detected.
The weighted risk score is calculated by the following formula:

---

Temporal = $$\left(Critical \times 25\right) + \left(High \times 15\right) + \left(Medium \times 5\right) + \left(Low \times 1\right)$$

Risk = $$\left(\frac{Temporal}{Temporal + 100}\right) \times 100$$

---

> [!NOTE]
> The highest risk score is 100, and the lowest risk score is 0. If malware is detected on a container image the risk score is set to 90.

In addtion, the dashboard displays the most common container images found on hosts, and identifies vulnerable container image packages using [sematic versioning](https://semver.org/) that have patch fixes available.

---


#### Requirements

> [!IMPORTANT]
> In order for the dashboard drilldowns to work, it is required to search/replace the dashboard.json for :point_right: ```placeholder.com``` and replace with your tenant URL.
>
> - Example:
>    - Before: https://placeholder.com/assets/inventory
>    - After: https://mytenant.xdr.us.paloaltonetworks.com/assets/inventory

---

#### Dashboard Screenshot

![Dashboard](dashboard.png)
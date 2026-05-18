# Cortex Cloud Dashboards

---

## Dashboard Directory

 | Dashboard Title | Description                                                                                                                                                                                         | Requires Updating URL's  | Contributor | Contributor Country |
 |---|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
 | [Container Images and Daily Risk](container_image_risk/) | View detected container images over time, per-image risk scores, container images that have "patch fixes", and most the common container images on hosts.                                           | [Yes](#drilldown-url) | [Erick Moore](https://github.com/erickmoore) | :us: |
| [SecOps Dashboard](secops_dashboard/) | View MTTR across issues, open issues by age, open issues by type, vulnerability distribution, top identites at risk, top critical issues to address, top impacted assets, and top impacted accounts | No | Stuart Wyatt | :uk: |
| [CNAPP - Runtime Workload Protection/Scan Status Dashboard](runtime_workloads_onboarding_status/) | Status of discovered VMs, K8S Clusters, Serverless Functions, Container Instances                                                                                                                   |  No | [Oleg Kostine](https://github.com/okostine-panw) | :uk: |
| [CNAPP - Container/VM Image Protection/Scan Status Dashboard](images_onboarding_status/) | Status of discovered Container/VM Images protection and scanning, VM Images, Container Image Registries, Repositories and Container Images                                                          |  No |  [Oleg Kostine](https://github.com/okostine-panw) | :uk: |
| [CNAPP - SecOps Issues Analysis Dashboard](posture_issues/) | CNAPP posture issues with detailed breakdowns by severity, status, category, and asset context **without Asset Group filter**                                                         |  No |  [Oleg Kostine](https://github.com/okostine-panw)  | :uk: |
| [CNAPP - SecOps Issues Analysis Dashboard](posture_issues_with_assetgroups/) | CNAPP posture issues with detailed breakdowns by severity, status, category, and asset context **with Asset Group filter**                                                         |  No |  [Oleg Kostine](https://github.com/okostine-panw)  | :uk: |
| [CNAPP - Cloud Health Ingestion/Scan Status Dashboard](cloud_health_status/) | Cloud Health ingestion/scans auditing errors across providers, assets, regions, and error messages                                                                                                  |  No |  [Oleg Kostine](https://github.com/okostine-panw)  | :uk: |
| [CORTEX - AppSec Findings Dashboard](cortex_appsec_findings/) | Cortex AppSec Findings view table with filters and download option                                                          |  No |  [Oleg Kostine](https://github.com/okostine-panw)  | :uk: |
| [CORTEX - Network Flows Connections Analysis Dashboard](network_analysis/) | Network flow log analysis built on the network_story preset. Covers all traffic product types — geo-distribution, top processes, protocol analysis, port usage, hourly trends, unsigned process detection, IMDS access, causality chain anomalies, and full flow details.                                                                                                                   |  No | [Oleg Kostine](https://github.com/okostine-panw) | :uk: |
| [CORTEX - AWS VPC Network Flows Analysis Dashboard](network_vpc_analysis/) | Cloud VPC flow log analysis built on raw cloud audit logs (Cloud Flow Log filter). Covers AWS VPC Flow Logs (amazon_aws_raw) . Includes traffic volume, byte-level analysis, TCP flags, ACCEPT/REJECT breakdown, IMDS detection, geo-location, and full flow detail tables. Replaces network_story preset which lacked volume data and included rejected connections.                                                                                                                   |  No | [Oleg Kostine](https://github.com/okostine-panw) | :uk: |
 ---

## Drilldown URL

 > [!NOTE]
> When importing dashboards with URL drilldowns that reference your tenant, in order for the drlldowns to work, it is required to search/replace
> the dashboard.json for placeholder.com and replace with your tenant URL.
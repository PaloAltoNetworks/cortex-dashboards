# Cortex Cloud Dashboards

---

## Dashboard Directory

 | Dashboard Title |  Description  | Requires Updating URL's  | Contributor | Contributor Country |
 |---|---|---|---|---|
 | [Container Images and Daily Risk](container_image_risk/) | View detected container images over time, per-image risk scores, container images that have "patch fixes", and most the common container images on hosts. | [Yes](#drilldown-url) | [Erick Moore](https://github.com/erickmoore) | :us: |
| [SecOps Dashboard](secops_dashboard/) | View MTTR across issues, open issues by age, open issues by type, vulnerability distribution, top identites at risk, top critical issues to address, top impacted assets, and top impacted accounts | No | Stuart Wyatt | :uk: |
 | [Cloud Network Analyzer Issues](cloud_network_analyzer_issues_dashboard/) | Identify all Open and Resolved Cloud Network Analyzer Issues. | [Yes](#drilldown-url) | Luis Latorre | :canada: | 
 | [Internet Exposed Issues](internet_exposed_Issues/) | Identify all Open Cloud Network Analyzer Issues and Internet Exposed Issues. | [Yes](#drilldown-url) | Luis Latorre | :canada: |
| [CNAPP - Runtime Workload Protection/Scan Status Dashboard](runtime_workloads_onboarding_status/) | Status of discovered VMs, K8S Clusters, Serverless Functions, Container Instances |  No | [Oleg Kostine](https://github.com/okostine-panw) | :uk: |
| [CNAPP - Container/VM Image Protection/Scan Status Dashboard](images_onboarding_status/) | Status of discovered Container/VM Images protection and scanning, VM Images, Container Image Registries, Repositories and Container Images |  No | Oleg Kostine | :uk: |

 ---

## Drilldown URL

 > [!NOTE]
> When importing dashboards with URL drilldowns that reference your tenant, in order for the drlldowns to work, it is required to search/replace
> the dashboard.json for placeholder.com and replace with your tenant URL.

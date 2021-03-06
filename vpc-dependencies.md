---

copyright:
  years: 2018, 2019, 2020
lastupdated: "2020-04-28"

keywords: VPC, IBM CLoud, Virtual Private Cloud, generation 2, gen 2, system dependencies, dependencies, hard dependency

subcollection: vpc

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}
{:download: .download}

# VPC dependencies
{: #vpc-dependencies}

The {{site.data.keyword.vpc_full}} (VPC) depends upon various {{site.data.keyword.cloud_notm}} integrated services for purposes such as:

* Hosting the internal microservices of the VPC service 
* Integrating with {{site.data.keyword.cloud_notm}} and its user interface
* Storing and backing up service data (including VPC resource metadata)
* Logging and auditing service events.
{:shortdesc}


The following table lists the main dependencies of the VPC service and the purpose of each one:

| Service | Purpose |
| ------- | ------- |
| Identity and Access Management (IAM) | Provides authentication and authorization of all VPC API requests |
| Global Catalog | Provides structured, globally consistent metadata for VPC resource profiles |
| Resource Controller + Manager | Coordinates the provisioning and lifecycle of all VPC resources |
| Cloud Usage Metering (Billing Data) | Collects usage metrics the VPC service to generate bills for customer accounts |
| Container Registries | Hosts and validates the container images for the internal components of the VPC service |
| IBM Kubernetes Service (IKS) | Hosts clusters of containers that run the internal regional microservices of the VPC service |
| Red Hat Licensing Service | Activates a compute instance that was provisioned with an IBM-provided RHEL image |
| Windows Licensing Service | Activates a compute instance that was provisioned with an IBM-provided Windows image |
| Cloud Object Storage | Provides interim storage of customer-provided VPC images, recent storage of LogDNA data, and backups of all VPC resource metadata |
| Infrastructure Management Service (IMS) | Provides physical rack and server data; controls VPC storage volumes |
| Key Protect | Hosts customer root keys that wrap the data encryption keys for encrypted storage |
| Hyper Protect Crypto Services | Also hosts customer root keys that wrap the data encryption keys for encrypted storage |
| Global Search and Tagging - Search (GhoST) |  Identifies whether your root key is hosted in HPCS or KeyProtect; provides a global view of an account's VPC resources.
| Hypersync | Enables VPC resource and lifecycle events to be published to GhoST and other subscribers |
| IBM Event Streams | Enables VPC resource and lifecycle events to be published to GhoST and other subscribers |
| IBM Log Analysis with LogDNA | Collects logs that are generated by the VPC service. Depending on the type of log, it can be used by IBM support and operations, customers, or both |
| IBM Cloud Activity Tracker (AT) with LogDNA | Collects activity tracker events that are generated by the VPC service. Depending on the type of event, it can be used by IBM support and operations, customers, or both |
| Technical Integration Point (Tivoli Integrated Portal) | Notifies IBM's support and operations team of VPC service outages and incidents |
| OSS Event Data WebSphere Message Broker (OSS EDB) | Monitors the health of the internal components of the VPC service |
| Ops Dashboard | Allows IBM's operations team to track the inventory and consumption of VPC resources |
| IBM Databases for Elasticsearch | Houses tracing data used for debugging, troubleshooting, and performance monitoring of the internal components of the VPC service |
| IBM Cloud Monitoring with Sysdig | Stores metrics used for debugging, troubleshooting, and performance monitoring of the internal components of the VPC service |
| IBM Cloud Certificate Manager | Stores and manages certificates. Certificates are used to securely deploy VPC components, and to provide secure communication between VPC components |


The following diagram depicts and classifies the dependencies of the VPC service:

![VPC Dependency Diagram](images/vpc-dependencies.png)

For purposes of classification, a dependency is considered "hard" if a failure can impact the
availability of some of or all of the VPC service. For example, failure of the Red Hat Licensing Service prevents activation of compute instances that are provisioned with {{site.data.keyword.cloud_notm}}-provided Red Hat Enterprise Linux images in that region.

The data that you provide to the VPC service in your region is exchanged only with logging and
data services in the same region. Data backups are stored in {{site.data.keyword.cloud_notm}} Object Storage in the same region.

<!-- Acrolinx = 89 -->

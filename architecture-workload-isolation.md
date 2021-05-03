---

copyright:
  years: 2020
lastupdated: "2020-10-15"

keywords: public isolation for API Connect Reserved instance, compute isolation for API Connect Reserved instance, API Connect Reserved instance architecture, workload isolation in API Connect Reserved instance

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Learning about {{site.data.keyword.apiconnect_short}} architecture and workload isolation
{: #compute-isolation}

Review the following sample architecture for {{site.data.keyword.apiconnect_full}} V10 Reserved instance, and learn more about different isolation levels so that you can choose the solution that best meets the requirements of the workloads that you want to run in the cloud.
{: shortdesc}

## {{site.data.keyword.apiconnect_short}} V10 Reserved instance architecture
{: #architecture}

_Review the following example: https://cloud.ibm.com/docs/containers?topic=containers-service-arch. Review the System Architecture Guide: https://pages.github.ibm.com/CloudEngineering/system_architecture/services/multitenancy.html. Provide an architectural overview diagram identifying what runs within the IBM Service Account and what runs in the customer's account._

## {{site.data.keyword.apiconnect_short}} V10 Reserved instance workload isolation
{: #workload-isolation}

_Document how customer workloads are isolated from each other by plan. Do customer workloads run within the customer account?  Are customer workloads isolated within Kubernetes namespaces? Do customer workloads run on dedicated compute? Check out the example from Kubernetes: https://cloud.ibm.com/docs/containers?topic=containers-service-arch#worker-components_

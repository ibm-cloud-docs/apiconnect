---

copyright:
  years: 2020
lastupdated: "2020-10-15"

keywords: API management, API, gateway, support, responsibility, responsible

subcollection: apiconnect

---

{:external: target="_blank" .external} 
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}

# Understanding your responsibilities when using {{site.data.keyword.apiconnect_short}}
{: #responsibilities}

Review the following tables to understand who is responsible for managing the different resources and features in {{site.data.keyword.apiconnect_short}}.
{: shortdesc}


For a general overview of IBM and customer responsibilities in {{site.data.keyword.Bluemix_notm}}, see [Shared responsibilities for IBM Cloud offerings](/docs/overview?topic=overview-shared-responsibilities).

## Responsibility for {{site.data.keyword.apiconnect_short}} resources
{: #resources_responsibilities}

While most of the {{site.data.keyword.apiconnect_short}} resources are managed by IBM, you are responsible for some resources that are typically managed by you. Table 1 lists the {{site.data.keyword.apiconnect_short}} resources and notes which party is responsible for managing different aspects of each resource.

| Resource                     | Incident and Operations Management | Identity and Access Management | Security and Regulation Compliance | Disaster Recovery |
| ---------------------------- | --------------------- | ------------------| --------------------- | -------- |
| Data                         | You                   | You               | You                   | Shared   |
| Application                  | You                   | You               | Shared                | Shared   |
| Observability                | Shared                | Shared            | Shared                | IBM      |
| App networking               | Shared                | IBM               | IBM                   | IBM      |
| Virtual storage              | IBM                   | IBM               | IBM                   | IBM      |
| Virtual network              | IBM                   | IBM               | IBM                   | IBM      |
| Hypervisor                   | IBM                   | IBM               | IBM                   | IBM      |
| Physical servers and memory  | IBM                   | IBM               | IBM                   | IBM      |
| Physical storage             | IBM                   | IBM               | IBM                   | IBM      |
| Physical network and devices | IBM                   | IBM               | IBM                   | IBM      |
| Facilities and Data Centers  | IBM                   | IBM               | IBM                   | IBM      |
{: caption="Table 1. Resource responsibility" caption-side="top"}


## Responsibility for {{site.data.keyword.apiconnect_short}} features
{: #features_responsibilities}

Most of the responsibility for {{site.data.keyword.apiconnect_short}} features is shared between you and IBM. Table 2 specifies each party's responsibilities for features.

| Feature             | Your Responsibility           | IBM's Responsibility           |
| --------------------| ----------------------------- | -------------------------------|
| API and Product creation        | Provide REST API and API Product specifications using OpenAPI files, the {{site.data.keyword.apiconnect_short}} APIs, and the {{site.data.keyword.apiconnect_short}} user interface | Provision and deploy the REST API using the your specifications |
| Networking      | Provide the endpoints for routing API traffic; deploy and manageremote DataPower API Gateways (if desired) | Expose the API to a public or private network via the IBM managed or a self-managed DataPower API Gateway |
| API subscriptions            | Enable API subscriptions as an identification/authentication method for a REST APIs and distribute appropriate keys to API subscribers | Generate and authenticate API keys |
| API security               | Enable IBM-supported security mechanisms (e.g. OAuth provider/consumer, basic auth, etc) as an authentication method for a REST API | Protect published APIs via OAuth tokens, basic auth, etc |
| Actions             | Configure | Integrate, generate, and activate |
| Monitoring          | Monitor individual API uptime and configure necessary alerts | Integrate with {{site.data.keyword.cloud_notm}} Log Analysis with LogDNA to provide customer-accessible API operational logs |
| Rate limiting       | Define appropriate rate limiting rules via the API Connect Product and API YAML specifications | Enforce rate limits |
| API management | Configure {{site.data.keyword.apiconnect_short}} using the provided interfaces and supported design specifications. | Host, provision, integrate, and implement your APIs using your {{site.data.keyword.apiconnect_short}}-compatible specifications |
{: caption="Table 2. Feature responsibility" caption-side="top"}


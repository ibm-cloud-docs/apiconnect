---

copyright:
  years: 2020, 2021
lastupdated: "2020-10-15"

keywords: management, Reserved instance, administer

subcollection: apiconnect

---

{:external: target="_blank" .external} 
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Administering your {{site.data.keyword.apiconnect_short}} Reserved instance
{: #ri-admin-over}

Use the administration console to manage users and register additional gateways for {{site.data.keyword.apiconnect_short}} V10 Reserved.
{: shortdesc}


## Managing users
{: #users_ri-admin-over}

In {{site.data.keyword.apiconnect_short}}, users are grouped into _provider organizations_. Each provider organization owns a set of assets includeing APIs, products, catalogs, and developer portals. You can create a single provider organization (for example, in a small company) or create multiple provider organizations (for example, different departments in a large company). 

In {{site.data.keyword.cloud_notm}}, user access is managed with the Identity and Access Management (IAM) service. You can define access groups with policies that determine permissions within each provider organization in {{site.data.keyword.apiconnect_short}}, and then you can add members of your company's {{site.data.keyword.cloud_notm}} to the appropriate access groups, which results in the users becoming members of the provider organization. 

For more information on managing users in your Reserved instance, see [Managing users](/docs/apiconnect?apiconnect-ri-mng-users).


## Adding and managing gateways
{: #gwys_ri-admin-over}

{{site.data.keyword.apiconnect_short}} uses gateways to manage API traffic. A gateway hosts published APIs and provides the API endpoints used by client applications. Gateways execute API proxy invocations to back-end systems and enforce API policies that manage client identification, security, and rate limiting.

{{site.data.keyword.apiconnect_short}} V10 Reserved deploys with the IBM DataPower API gateway by default. You can deploy additional DataPower gateways for use with your Reserved instance; for example, to distribute API endpoints for different purposes.

For more information on adding gateways to your Reserved instance, see [Adding remote gateways](/docs/apiconnect?apiconnect-ri-reg-gwy). For information on managing user access to gateways, see [Managing gateways](/docs/apiconnect?apiconnect-ri-mng-gwy).


## Using the toolkit
{: #toolkit_ri-admin-over}

The toolkit provides a CLI for working with assets such as APIs and developer portals. For information on downloading and setting up the toolkit, see [Setting up your toolkit](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.toolkit.doc/ri_toolkit.html){: external} in the extended V10 Reserved documentation.

---

copyright:
   years: 2024, 2026
lastupdated: "2026-07-02"

keywords: IBM Cloud, API Connect, V12 Reserved instance, getting started, provision

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v-getting-started}

Set up your {{site.data.keyword.apiconnect_short}} V12 Reserved instance and begin developing, publishing, and managing APIs in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Before you begin
{: #prereqs_v12ri-getting-started}

To use {{site.data.keyword.apiconnect_short}} V12 Reserved, you need:
- An active {{site.data.keyword.cloud_notm}} account
- An activation code obtained by purchasing {{site.data.keyword.apiconnect_short}} V12 Reserved through IBM Sales
- Administrator access to your {{site.data.keyword.cloud_notm}} account

## Step 1: Provision your V12 Reserved instance
{: #step1_v12ri-getting-started}

Contact IBM Sales to purchase your V12 Reserved instance. When the purchase is complete, IBM provides an activation code (an entitlement key) that authorizes you to provision an instance of {{site.data.keyword.apiconnect_short}} V12 Reserved in {{site.data.keyword.cloud_notm}}.

For provisioning instructions, see [Provisioning a V12 Reserved instance](/docs/apiconnect?topic=apiconnect-provision).

## Step 2: Configure access
{: #step2_v12ri-getting-started}

Use {{site.data.keyword.iamlong}} (IAM) to create resource groups and access policies for your V12 Reserved instance. Assign administrator and user roles to control who can access the service and what they can do.

For information on configuring access, see [Managing access with IAM](/docs/apiconnect?topic=apiconnect-vri-iam).

## Step 3: Set up users and provider organizations
{: #step3_v12ri-getting-started}

In {{site.data.keyword.apiconnect_short}}, users are grouped into _provider organizations_. Each provider organization owns a set of assets including APIs, products, catalogs, and developer portals. As an administrator, you create provider organizations and assign users to them.

For information on managing users, see [Managing users in V12 Reserved](/docs/apiconnect?topic=apiconnect-mng-users).

## Step 4: Start developing APIs
{: #step4_v12ri-getting-started}

Use IBM API Studio — the AI-powered design and management tool — to start building your first API. You can also use the API Connect toolkit CLI for scripted workflows.

For information on developing APIs in V12 Reserved, see [Developing APIs in V12 Reserved](/docs/apiconnect?topic=apiconnect-develop-api).

## Step 5: Publish and manage your APIs
{: #step5_v12ri-getting-started}

After you develop your APIs, publish them to catalogs and manage their lifecycle using the API Manager. Share them with consumers through the IBM Developer Portal.

For information on managing products and catalogs, see [Managing products and catalogs in V12 Reserved](/docs/apiconnect?topic=apiconnect-v-mng-prod-cat).

## Next steps
{: #next_v12ri-getting-started}

- Explore [Federated API Management](/docs/apiconnect?topic=apiconnect-fed-api-mgmt) to manage distributed API runtimes from one place.
- Configure [analytics offloading](/docs/apiconnect?topic=apiconnect-v12rioffload-analytics) to route API event data to external systems.
- Set up [IBM AI Gateway](/docs/apiconnect?topic=apiconnect-ai-gateway) to govern AI services and LLM providers.
- Read the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/SSCL05_12.1.x){: external} for advanced topics.

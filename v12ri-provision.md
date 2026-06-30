---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-30"

keywords: IBM Cloud, API Connect, V12 Reserved instance, provision, activate

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Provisioning an instance of {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v12riprovision}

Create your {{site.data.keyword.apiconnect_short}} V12 Reserved instance so your users can develop APIs, publish them to consumers, and manage usage and lifecycles.
{: shortdesc}

To provision a new service instance of {{site.data.keyword.apiconnect_short}} V12 Reserved, complete the following steps.

1. Contact IBM Sales to purchase your V12 Reserved instance.

   When the purchase is complete, IBM generates an activation code for you. An activation code is an entitlement key that authorizes you to provision an instance of {{site.data.keyword.apiconnect_short}} V12 Reserved in {{site.data.keyword.cloud_notm}}.

   You cannot provision your instance without an activation code.

1. Use {{site.data.keyword.iamlong}} to create a resource group for your service instance.

   Assign appropriate access policies to control who can access the service instance. For information, see [Assigning access to resources by using access groups](/docs/account?topic=account-access-getstarted).

1. Provision your service instance:

   a. Navigate to the [{{site.data.keyword.cloud_notm}} Catalog](https://cloud.ibm.com/catalog) and search for "API Connect".

   b. On the API Connect page, select the **Create** tab and complete the provisioning settings:

   - **Select a location**: Select the region where you want to deploy your service instance. A multizone deployment provisions all data centers within the same region.

   - **Select a pricing plan**: Select **V12 Reserved** to provision a new instance.

   - **Configure your resource**:

     - **Service name**: Accept the default or provide your own. Use a name that includes a reference to your organization so that IBM Support can easily identify your service instance if needed.

     - **Select a resource group**: Select the resource group that you created for your service instance.

     - **Tags**: Optional. Add tags to help identify team usage or cost allocation.

   c. Enter the **Activation code** that IBM provided when you purchased the service.

   d. Click **Create** to provision the instance.

   IBM provisions your {{site.data.keyword.apiconnect_short}} V12 Reserved instance. Provisioning can take some time; IBM notifies you by email when the instance is ready.

1. When you receive notification that your instance is ready, log in to the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com/resources) and navigate to your {{site.data.keyword.apiconnect_short}} V12 Reserved instance.

1. Follow the instructions in [Administering your V12 Reserved instance](/docs/apiconnect?topic=apiconnect-v12ri-admin-over) to configure your instance for use.

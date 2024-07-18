---

copyright:
   years: 2020, 2024
lastupdated: "2024-07-18"

keywords: IBM Cloud, API Connect, Reserved instance, deploy, provision

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Provisioning an instance of {{site.data.keyword.apiconnect_short}} Reserved
{: #ri-provision}

Create your instance of {{site.data.keyword.apiconnect_short}} Reserved so your users can develop APIs, publish them to consumers, and manage usage and lifecycles.
{: shortdesc}

To provision a new service instance of {{site.data.keyword.apiconnect_short}} Reserved, complete the following steps.

1. Contact IBM Sales to purchase your Reserved instance.

When the purchase is complete, IBM generates an activation code for you. An activation code is an entitlement key that authorizes you to provision an instance of {{site.data.keyword.apiconnect_short}} Reserved in {{site.data.keyword.cloud}}.

You cannot provision your instance without an activation code.

1. Use {{site.data.keyword.iamlong}} to create a resource group that will be used for assigning permissions for users to access the service instance that you will provision.

For information, see [Assigning access to resources by using access groups](/docs/account?topic=account-access-getstarted).

1. Provision your service instance:

   a. Navigate to the [{{site.data.keyword.cloud}} Catalog](https://test.cloud.ibm.com/catalog) and search for "API Connect".

   b. On the API Connect page, select the **Create** tab and complete the provisioning settings:

   - Select a location: Select the region where you want to deploy your service instance.
        A multizone deployment provisions all data centers within the same region.

   - Select a pricing plan: Select "Reserved" to provision a new instance.

   - Configure your resource:

     - Service name: Accept the default or provide your own. It's a good idea to create a name that includes a reference to your organization so that IBM Support can easily  find your  service instance if needed.

     - Select a resource group: The list of resource groups is based on your {{site.data.keyword.cloud}} account permissions. Select the resource group that you created for your service instance.

     - Tags: Optional. Add some tags to help you with identifying specific team usage or cost allocation.

     - Access resources tags: Optional. Add some access tags to manage access to resources.

     - Activation code: Paste the activation code provided by IBM Sales.

   c. Accept the license terms.

   d. Click **Create**.

1. Switch to the "Resource list" page to track your provisioning status.

    Click ![Navigation menu](images/icon_cloud_menu.png "Navigation menu icon") in the page banner, and then click ![Resource list](images/icon_cloud_resource_list.png "Resource list icon") to open the Resource list. 

    In the Resource list, expand the **Integration** section and look for the service name that you assigned when you provisioned the instance.

Deploying a new service instance takes several hours. While your instance is being deployed, its status displays as "Provisioning". When provisioning is complete, the status changes to "Active".

## What to do next
{: #ri-provision-next}

When your instance is provisioned, you're ready to start using it. For your next steps, see [Getting started as an admin in API Connect V10 Reserved](/docs/apiconnect?topic=apiconnect-getting-started-admin).

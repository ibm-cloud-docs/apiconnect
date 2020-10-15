---

copyright:
  years: 2020
lastupdated: "2020-10-15"

keywords: IBM Cloud, API Connect, V10, Reserved plan, lifecycle, develop, create, manage, API

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

# Getting started as a user in {{site.data.keyword.apiconnect_short}} V10 Reserved
{: #getting-started}

See how easy it is to create, manage, secure, and share APIs.
{: shortdesc}

{{site.data.keyword.apiconnect_short}} V10 Reserved plan is the cloud-based edition of IBM {{site.data.keyword.apiconnect_short}}. The Reserved plan offers a comparable set of features for managing the lifecycle of APIs, hosted in {{site.data.keyword.cloud_notm}}. {{site.data.keyword.apiconnect_short}} makes it easy to create, securely expose, manage, and monetize APIs so that you and your customers can power digital applications and spur innovation. 

If you are an administrator, see [Getting started as an administrator](/docs/apiconnect?topic=apiconnect-getting-started-admin) for instructions on configuring your new Reserved plan and adding users.
{: note}

In this tutorial, you verify your access to {{site.data.keyword.apiconnect_short}}, then open the API Manager and create an API. Ready to get started? 


## Step 1. Log in to {{site.data.keyword.apiconnect_short}} with your provider organization
{: #open-apim_getting-started}

To use the API Manager, you must be invited to a provider organization in {{site.data.keyword.apiconnect_short}}. An administrator from your company creates the provider organization, defines access settings, and then adds users. 

You can log into the {{site.data.keyword.apiconnect_short}} with your provider organization by completing the following steps:

1. [Log in](https://cloud.ibm.com/login/){: external} to {{site.data.keyword.cloud_notm}} using your IBM ID.

2. On the {{site.data.keyword.cloud_notm}} Dashboard, click ![Menu icon](images_v10/icon_cloud_menu.png "Menu icon") and select **API Management**.

3. In the navigation list, expand **API Connect** and click **Services**.

4. On the Services page, expand the row for your company's {{site.data.keyword.apiconnect_short}} Reserved plan.

   Provider organizations belong to Reserved plans, so you need to expand the Reserved plan service to see the list of associated provider organizations. Each provider organization is labelled as "Provider Organization" in the "Plan" column. If your company has multiple Reserved plans and you don't know which one to use, expand each one until you see your provider organization.
   
5. Click the name of a provider organization to start the {{site.data.keyword.apiconnect_short}} API Manager.

   Your administrator can tell you which provider organization you belong to if it's not clear to you. When you click the provider organization to start API Manager, you are automatically logged in.
   
   If you belong to multiple provider organizations and want to log in with a different one, log out of API Manager. Then, return to the {{site.data.keyword.apiconnect_short}} Services page and log in with another provider organization.
   
   Whenever you want to work in API Manager, return to the Services page and select your provider organization. 

When you see the {{site.data.keyword.apiconnect_short}} Home page, you're ready to proceed.


## Step 2. Create an API
{: #create-api_getting-started}

See how easy it is to create an API by importing a YAML definition. 

Complete the tutorial [Importing an API](https://rtpdoc01.rtp.raleigh.ibm.com:9443/kc/v10_cloud_test/com.ibm.apic.apionprem.doc/tutorial_apionprem_import_api.html){: external} in the {{site.data.keyword.apiconnect_short}} V10 Reserved Knowledge Center.


## Next steps
{: #next-steps_getting-started}

For more step-by-step examples on creating, securing, and testing APIs, see the additional [API Manager tutorials](https://rtpdoc01.rtp.raleigh.ibm.com:9443/kc/v10_cloud_test/com.ibm.apic.apionprem.doc/tapim_management_tutorials.html){: external} in the {{site.data.keyword.apiconnect_short}} V10 Reserved Knowledge Center.

If you're ready to focus on specific tasks, see the topics in the [Using API Connect Reserved](/docs/apiconnect?topic=apiconnect-ri-user-over) section for more information on working with APIs and products, catalogs, event analytics, and the Developer Portal.


## About your personal data
{: #personal-data_getting-started}

The {{site.data.keyword.apiconnect_short}} service processes but doesn't store user data. You don't need to take any action to manage or delete your data.

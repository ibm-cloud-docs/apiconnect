---

copyright:
   years: 2020, 2025
lastupdated: "2025-06-16"

keywords: IBM Cloud, API Connect Reserved, faq 

subcollection: apiconnect

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}

# FAQ for {{site.data.keyword.apiconnect_short}} Reserved

{: #apiconnect-faqs}

Frequently asked questions for {{site.data.keyword.apiconnect_short}} Reserved answers questions about purchasing and provisioning {{site.data.keyword.apiconnect_short}} Reserved. To find all FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## What is {{site.data.keyword.apiconnect_short}} Reserved?

{: #faq-content-what-is}
{: faq}

{{site.data.keyword.apiconnect_short}} Reserved lets you create and manage APIs directly in {{site.data.keyword.cloud}}. Use {{site.data.keyword.apiconnect_short}} Reserved to host your APIs in the cloud and easily deploy, administer, and manage them.

To use {{site.data.keyword.apiconnect_short}} Reserved, you provision a private service instance in {{site.data.keyword.cloud}}, and IBM deploys it for you. IBM maintains the infrastructure and you administer your {{site.data.keyword.apiconnect_short}} deployment on the service instance.

## What regions is {{site.data.keyword.apiconnect_short}} Reserved available in?

{: #faq-content-regions}
{: faq}

{{site.data.keyword.apiconnect_short}} Reserved is available in the following {{site.data.keyword.cloud}} regions:

- Asia Pacific: Sydney (au-syd), Tokyo (jp-tok)
- Europe: Frankfurt (eu-de), London (eu-gb)
- North America: Dallas (us-south), Toronto (ca-tor), Washington (us-east)
- South America: Sao Paulo (br-sao)

## How do I purchase {{site.data.keyword.apiconnect_short}} Reserved?

{: #faq-content-purchase}
{: faq}

To purchase a service instance of {{site.data.keyword.apiconnect_short}} Reserved, contact IBM Sales. You can purchase {{site.data.keyword.apiconnect_short}} Reserved with a single-zone or a multi-zone configuration, depending on your needs.

When you complete your purchase, IBM generates an activation code that authorizes you to provision your service instance.

## How do I provision my {{site.data.keyword.apiconnect_short}} Reserved instance?

{: #faq-content-provision}
{: faq}

For instructions on provisioning an instance of {{site.data.keyword.apiconnect_short}} Reserved, see [Provision an instance of {{site.data.keyword.apiconnect_short}} Reserved](/docs/apiconnect?topic=apiconnect-ri-provision).

## How will I know when my new service instance is available?

{: #faq-content-service-status}
{: faq}

The status of your service instance displays in the Integration section of the Resources list on your {{site.data.keyword.cloud}} Dashboard.

To see the Resource list, click ![Navigation menu](images/icon_cloud_menu.png "Navigation menu") in the page banner, and then click ![Resource list](images/icon_cloud_resource_list.png "Resource list icon") to see the Resource list. In the Resource list, expand the **Integration** section and look for the service name that you assigned when you provisioned the instance.

Deploying a new service instance takes several hours. While your instance is being deployed, its status displays as "Provisioning". When provisioning is complete, the status changes to "Active".

## What should I do if my service doesn't work correctly?

{: #faq-content-service-fail}
{: faq}

If you encounter problems provisioning or using your {{site.data.keyword.apiconnect_short}} Reserved instance, submit a case with IBM Support as explained in [Using the Support Center](/docs/apiconnect?topic=apiconnect-get_help).

## How do I manage resources for my instance?

{: #faq-content-manage-resources}
{: faq}

To secure access to resources for your instance and its users, configure a resource group that will be used for assigning permissions for your users. For information, see [Assigning access to resources by using access groups](/docs/account?topic=account-access-getstarted).

## How do I add users to my service instance?

{: #faq-content-add-users}
{: faq}

To give users access to your service instance, create a provider organization in {{site.data.keyword.apiconnect_short}} Reserved, and add individual users. Then, use {{site.data.keyword.iamlong}} to create IAM access groups, assign access policies to each group, and then add users to each group. The IAM access groups correspond to roles in your provider organization and determine the permissions for each of your users.

For instructions, see [Managing users](/docs/apiconnect?topic=apiconnect-ri-mng-users).

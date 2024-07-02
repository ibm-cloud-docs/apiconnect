---

copyright:
   years: 2020, 2024
lastupdated: "2024-07-02"

keywords: management, Reserved plan, develop, manage, use, publish, socialize, customer, consumer, lifecycle, API Connect

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# What is {{site.data.keyword.apiconnect_short}} Reserved?

{: #ri-user-over}

{{site.data.keyword.apiconnect_short}} V10 Reserved lets you create and manage APIs directly in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Managing the API lifecycle in {{site.data.keyword.apiconnect_short}}

{: #lifecycle_ri-user-over}

{{site.data.keyword.apiconnect_short}} enables you to manage the lifecyle of your APIs with a set of integrated features. Use the {{site.data.keyword.apiconnect_short}} Reserved plan to host your APIs in the cloud and easily complete the tasks needed for all phases of an API's life:

- Develop APIs, bundle them into consumable products, and deploy them to production environments.

- Administer API publication and security with development catalogs, access gateways, OAuth, and execution policies to control access to your APIs and back-end systems.

- Manage API products with a Developer Portal where you can make them available to application developers, and a robust set of analytics so you can monitor API usage and performance.

## Who does what in {{site.data.keyword.apiconnect_short}}?

{: #whodoeswhat_ri-user-over}

In {{site.data.keyword.apiconnect_short}}, users are grouped into provider organizations, and are assigned permissions that control access to resources based on the job that each person typically performs.
{: shortdesc}

Jobs can be assigned to people based on their expertise; for example, administering users, developing APIs, and monitoring event analytics. In a small company, one or two people might perform all of the work in creating and managing APIs. In a large company, a different person (or even multiple people) might be assigned to each job. When you read the {{site.data.keyword.apiconnect_short}}, you'll see that information about tasks and features is often organized based on the following jobs that people are typically assigned to perform:

- **{{site.data.keyword.apiconnect_short}} Administrator**

   Everyone who has administrator privileges in your company's IBM Cloud account is automatically assigned the role of {{site.data.keyword.apiconnect_short}} Administrator. The Administrator provisions and manages your company's {{site.data.keyword.apiconnect_short}} Reserved plan. The Admin adds users to {{site.data.keyword.apiconnect_short}} and configures services such as the gateways that control customer access to your APIs.

   One of the Admin's main jobs is to set up provider organizations and add users. A _provider organization_ is a group of people who use the API Manager component of {{site.data.keyword.apiconnect_short}}. _Members_ of the provider organization create and manage APIs, products, and related assets. {{site.data.keyword.apiconnect_short}} Admins create the provider organizations, add members, and define the roles that control user access.

- **API Developer**

   An API developer creates new APIs and updates existing APIs as needed. The API developer can configure policies that define security restrictions, logging rules, and quotas that control access to your company’s resources.

- **API Administrator**

   After an API developer creates a set of APIs, the API administrator manages the distribution. The API administrator defines _plans_ that determine access to the APIs, bundles a set of related APIs and plans into _products_, and _publishes_ them to the _developer portal_ where customers can find them. The API administrator also manages the _catalogs_ and _spaces_ where API developers create and test APIs.

- **Product Manager**

   A product manager controls access to the Developer Portal where consumers can _subscribe_ to APIs, which they use in their applications. For each group of customers, the product manager creates a _consumer organization_ that controls access to the Developer Portal. The product manager uses the Analytics feature to track API usage and performance, which helps determine when APIs should be updated or retired.

- **Consumer**

   _Consumers_ are your customers, and are not members of your provider organization. When your organization publishes products that contain APIs, consumers subscribe to the products so they can use the APIs in their applications. A consumer can subscribe to use APIs and products that are developed by different provider organizations. Each provider organization assigns one or more Product Managers to manage the relationship with its consumers. The Product Manager creates _consumer organizations_ and adds customers to give them access to the developer portal.

For more information on working in {{site.data.keyword.apiconnect_short}}, see [Understanding {{site.data.keyword.apiconnect_short}}](https://www.ibm.com/docs/SSMNED_v10cloud/com.ibm.apic.overview.doc/capic_whatis.html){: external} in the V10 Reserved Knowledge Center.

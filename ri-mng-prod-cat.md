---

copyright:
  years: 2020, 2021
lastupdated: "2020-10-15"

keywords: management, Reserved instance

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

# Managing APIs, products, and catalogs
{: #ri-manage-assets}

Managing APIs, catalogs, and products in {{site.data.keyword.apiconnect_full}} involves a series of tasks to maintain catalogs where developers can create and test APIs, and to manage the lifecycle of the products containing APIs that are published for customer use.
{: shortdesc}


## API administration tasks in {{site.data.keyword.apiconnect_short}}
{: #tasks-docs_ri-manage-assets}

Every provider organization has its own set of APIs, catalogs, and products. While the API Developer creates APIs and products, the API Administrator manages them, along with the catalogs where development work takes place.
 
After an API developer creates a set of APIs, the API administrator manages the distribution. The API administrator defines _Plans_ that determine access to the APIs, bundles a set of related APIs and Plans into _Products_, and _publishes_ them to the consumer _Developer Portals_. The API administrator also manages the _Catalogs_ and _Spaces_ where API developers create and test APIs. API Administrators should read the topics in the "Managing catalogs and products" section of the extended V10 Reserved documentation.

You can perform API management tasks in the API Manager interface, or in the toolkit command-line interface. For information on working with the toolkit, see [Setting up your toolkit](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.toolkit.doc/ri_toolkit.html){: external} in the extended V10 Reserved documentation.


### Managing catalogs
{: #catalog-docs_ri-manage-assets}

A _catalog_ is a staging target where developers can create and test APIs before publishing them for customers to use. Each provider organization can create multiple catalogs. Catalogs are useful for organizing products and APIs for testing before you make them available to consumer organizations. For more information on managing catalogs, see the following topics in the extended V10 documentation:

- [Creating catalogs](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/create_env.html){: external}
- [Adding users to catalogs](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_catalog_members_manage.html){: external}

You can partition a catalog into _spaces_ and then assign a different team of developers to work in each space.

#### Using spaces in a catalog
{: #space-docs_ri-manage-assets}

Each space is used by a different team of developers, and has its own set of management capabilities relating specifically to the APIs that are developed by associated team. Using spaces enables each development team to manage their APIs independently. For information on working with spaces, see the following topics in the extended V10 Reserved documentation:

- [Managing API syndication with spaces](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_syndication_spaces_configure.html){: external}

- Adding spaces to a catalog: 
   1. [Enable spaces](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_syndication_spaces_enable.html){: external}
   2. [Create a space](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_syndication_spaces_manage.html){: external}
   3. [Add users to the space](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_syndication_spaces_members_manage.html){: external}


### Configuring OAuth providers for APIs
{: #oauth-docs_ri-manage-assets}

Secure access to your organization's APIs by configuring an OAuth provider. When a customer's application calls your API, the app must obtain a token from the OAuth provider and pass it to {{site.data.keyword.apiconnect_short}} to prove that it has authorization to use the API. For information on working with OAuth, see the following topics in the extended V10 Reserved documentation:

- [OAuth concepts](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/con_apionprem_authentication.html){: external}
- [Creating a native OAuth provider](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/oauth_native_apim.html){: external}
- [Creating a third-party OAuth provider](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/oauth_thirdparty_apim.html){: external}


### Managing product lifecycles
{: #product-docs_ri-manage-assets}

A _product_ is a set of APIs and the _plans_ that specify usage rules such as rate limits. You publish a product to your organization's _developer portal_ where customers can _subscribe_ to use the APIs contained in each product. Every product has a lifecycle spanning its initial publication through its removal from the Developer Portal. You can manage the stages in the product lifecycle in {{site.data.keyword.apiconnect_short}}. For information on working with products, see the following topics in the extended V10 Reserved documentation:

#### Publishing a product
{: #publish-docs_ri-manage-assets}

- [Publish a new product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_publishing_a_product.html){: external}
- [Replace a product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_replacing_a_product.html){: external}
- [Supercede a product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_superseding_a_product.html){: external}
             
#### Changing product availability
{: #change-docs_ri-manage-assets}

Restrict a product to specific consumers or endpoints, or remove a product from the developer portal.

- [Approve product requests](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_accessrequests_product.html){: external}
- [Update gateway services](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/tapic_product_update_gw.html){: external}
- [Set a product's visibility](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_change_product_availability.html){: external}
- [Deprecate a product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_deprecate_product.html){: external}
- [Retire a product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_retire_product.html){: external}
- [Remove a product](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/task_unpublish_product.html){: external}

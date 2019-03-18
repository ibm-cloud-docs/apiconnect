---

copyright:
  years: 2017
lastupdated: "2017-10-10"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Managing API and Product versions
{: #tut_manage_version_landing}

After publishing an API and the product that contains it, API providers typically want or need to update those products and APIs. Updating an API product can happen in different ways.  

- Replace the old with the new, automatically updating all subscriptions
- Supersede the old with the new, manually updating subscriptions on a per app basis

After replacing an API, you can then take an API product out of service and remove it by following these steps:

- **Deprecate the API product.** This prevents any new subscriptions to the API but does not prohibit usage.
- **Retire the API product.** This prevents any use of the API but does not remove it.
- **Archive the API product.** This removes the API from use but does not delete it completely; it can be reinstated.
- **Delete the API product.** The API product is gone completely and cannot be retrieved.

In this series of tutorials, you will move API products through all of these states. Complete the tutorials in the following order:

1. [Replace an API product](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace)
2. [Supersede an API product](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede)
3. [Archive and delete an API product](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_remove)









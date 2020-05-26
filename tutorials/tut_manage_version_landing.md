---

copyright:
  years: 2017
lastupdated: "2017-10-10"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Managing API and Product versions
{: #tut_manage_version_landing}

After publishing an API and the product that contains it, API providers typically need to update those products and APIs. Updating an API product can happen in different ways; for example:  

- Completely replace the old API product with a new version, automatically updating all subscriptions.
- Supersede the old API product with the new version, manually updating individual subscriptions.

To replace an API, take the API product out of service and then remove it by completing the following tasks:

- **Deprecate the API product**: Prevent new subscriptions to the API but do not prohibit usage.
- **Retire the API product**: Prevents any use of the API but do not remove it.
- **Archive the API product**: Remove the API from use but do not delete it completely. The API can be can be reinstated if needed.
- **Delete the API product**: Permanently delete API product.

In this series of tutorials, you will move API products through all of these states. Complete the tutorials in the following sequence:

1. [Replace an API product](/docs/apiconnect/tutorials?topic=apiconnect-tut_manage_replace).
2. [Supersede an API product](/docs/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede).
3. [Archive and delete an API product](/docs/apiconnect/tutorials?topic=apiconnect-tut_manage_remove).









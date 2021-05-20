---

copyright:
  years: 2020, 2021
lastupdated: "2020-10-15"

keywords: IBM Cloud, API Connect, V10, Reserved instance, lifecycle, develop, create, manage, API, user, role, access, group

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

# Managing gateways
{: #ri-mng-gwy}

Manage gateways in {{site.data.keyword.apiconnect_short}} Reserved by defining whether they are available to users, and whether they are included in new catalogs.
{: shortdesc}


## Controlling a gateway's visibility
{: #visible_ri-mng-gwy}

A gateway's visibility setting determines which provider organizations can use the gateway. If you deploy multiple gateways, you might want to assign each gateway to a specific set of provider organizations.

1. On the administration console's home page, click **Gateways**.

2. On the "Gateways" page, locate the gateway in the table. At the end of the row, click ![Menu icon](images/icon_options.png "Menu icon") > **Set visibility**.

3. On the "Set visibility of gateway" page, select the visibility level for the current gateway.

4. If you selected the **Custom** option, use the "Provider organizations" panel to specify which provider organizations can use the gateway:

   a. Locate a provider organization:
      - Click the **Search for provider organizations** field to display a list of provider organizations.
      - Type a string in the **Search for provider organizations** field to filter the list of provider organizations.
   
   b. Click the name of the provider organization to select it.

5. Click **Save** to save the visibility settings.


## Specifying default gateways for catalogs
{: #default_ri-mng-gwy}

Members of a provider organization publish APIs by adding them to a product and then publishing the product to a catalog. The catalog must be assigned at least one gateway so that the APIs can be called using the gateway endpoint. To ensure that new catalogs have access to gateways, you can assign _default gateways_ that are automatically added to every new catalog. 

1. On the administration console's home page, click **Settings**.

2. On the "Default gateways" page, click **Edit**.

3. In the "Specify default gateways" page, select all of the gateways that you want to be available to new catalogs.

4. Click **Save** to apply the new setting.

Existing catalogs are not affected when you change this setting. You can update a catalog later in API Manager to remove unwanted gateways or add new gateways. For information on working with catalog settings, see [Creating and configuring catalogs](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.apionprem.doc/create_env.html){: external} in the extended V10 Reserved documentation.

---

copyright:
  years: 2017, 2020
lastupdated: "2020-02-24"

keywords: IBM Cloud, API Connect, API management, API, APIs, lifecycle, catalog, API Connect Enterprise, API Connect Hybrid

subcollection: apiconnect

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Configuring a Catalog
{: #create_catalog}

You can create and configure your API Manager Catalogs in the Lite, Enterprise, and Hybrid plans. 
{: shortdesc}

Catalogs are useful for separating Products and APIs for testing before you make them available to Developer organizations. When you configure a Catalog, you can also configure custom branding so that you do not have to use
the default API URL provided by the API Manager.

Complete the following steps to create your Catalog:

1. Click ![Navigate icon](images/navigate_to_icon.png "Navigate icon") > **Dashboard**.

2. Click **+ Add** > **Catalog**.
The **Add Catalog** window is displayed.

3.  Enter the name of your new Catalog in the **Display Name** field.

4. Enter the text that you want to form the Catalog segment of the URL, in the
**Name** field.
	**Note:** The **Name** field can contain only lowercase alphanumeric characters (a-z
	and 0-9), or hyphen characters (-). A hyphen cannot be used as the first or last character in the name.

5. Click **Add**. Your Catalog is created, and is displayed on your dashboard.

6. To configure the Catalog, click the name of the Catalog, then click **Settings** > **Info**, and proceed with the following steps:

   a. If the new Catalog is a development Catalog, select **Development mode**.
	
      Development and Production catalogs behave differently:

      - Development catalog:

        If you select the development mode, staging and publishing actions are forced. If you republish a Product, it is overwritten without warning. If conflicts are found, they are automatically resolved by the system. Unpublish actions happen automatically.

        **Note:** Approval boxes are not displayed for development Catalogs. You cannot enable the approval process for lifecycles.

      - Production catalog:

        You will be prevented from publishing a Product to a Production Catalog if there is already a Product in the Catalog with the same name and version; you must create a new version of the Product for publication. If Spaces are enabled in a production Catalog, you cannot publish a Product with the same name and version to more than one Space in the Catalog.

        If you create a new Product that contains one or more modified APIs, you must create new versions of those APIs for inclusion in the Product. If the Product contains a modified API and there is already a published API with the same name and version, your changes will not be published.
	
   b. If you want to enable automatic subscription for the Catalog, select **Automatic
subscription**.

      Enabling automatic subscription makes testing your APIs easier because a test application is used. The test application includes a pre-supplied client ID and client secret. The test application is automatically subscribed to all of the Plans in the Catalog, so you don't have to specify a plan or application when testing. 
	 
      **Note:** Automatic subscription is available only for a development Catalog.
	
   c. If the Catalog is the default staging Catalog, select **Default**. Then, calls to APIs that are published to the Catalog can use a shorter URL that does not include the Catalog name.

     **Note:** You can select **Default** for one Catalog.
	
   d. **Optional**: Click **Endpoints**, and populate the following fields:

      - **Custom Gateway URL**: In the Custom Gateway URL text field, enter a URL. You use the Custom Gateway URL if you want to
         achieve custom branding of URLs for APIs that are deployed to {{site.data.keyword.apiconnect_short}}, rather than using the default URL
        that API Manager generates.
        By default, the {{site.data.keyword.apiconnect_short}} gateway URL has the following format:
		
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        However, you can override the default by specifying a URL that is more appropriate for your enterprise; for
        example, `https://api.mycompany.com`. Any API endpoints that are displayed in the
        Developer Portal reflect the custom URL.
		
		**Notes:**
        - This option is not available for the Lite plan.
        - To set up the URL redirect, contact {{site.data.keyword.apiconnect_short}} Support.
        - You must configure a DNS entry that maps your custom host name and domain to the default gateway URL.
        - If you want the endpoints of an API to reflect your custom gateway URL, configure the API to be enforced by the API Connect gateway. For more information, see [Specifying an alternative host for an API](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: external}.
        - Ensure that the same custom gateway URL is not applied to multiple Catalogs as the behavior in that scenario is undefined.
           **TIP**: When you call the API, you can also set the HTTP host header on the API request to the value that you specified in the Custom Gateway URL field.

      - **Custom API URL**
         In the Custom API URL text field, enter the URL. You use the Custom API URL to specify the URL for APIs that are deployed to a third-party gateway.

         The Custom API URL represents the endpoint by which the API is known externally. The endpoint is published to the developer portal and used by an application developer to invoke or advertise the API.

        If you are using a third-party gateway or external load balancer in this Catalog, supply the URL in this field. Any API endpoints that are displayed in the developer portal reflect the custom URL. These endpoints exist on the third-party gateway or load balancer and project a
	    virtual address that is mapped to the API proxy or API assembly endpoints on the gateway. The endpoints that are derived from the custom API URL are typically published in production developer portals to advertise the address of the API.

        **Note:** If you specify a custom API URL for a Catalog, it takes precedence over any host name that you specify when you configure the API. For more information, see [Specifying an alternative host for an API](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: external}.

      - **Hostname for Developer Portal API Calls**:
         In the Port API Endpoint window area, enter a host name for Developer Portal API calls. The host name that you enter can be the host name of your Management service. To access the Developer Portal API within the context of a Developer Portal, you must configure the base host name for the Developer Portal API calls. This action allows API Manager to map your host name to the provider organization and Catalog of the Developer Portal API calls. Your calls don't need to include the information.

7. Click the **Save** icon.

## Partitioning a Catalog
{: #apic_spaces-create_catalog}

To use the syndication feature in {{site.data.keyword.apiconnect_short}}, you must enable Spaces in any
Catalog in which you require syndication capabilities.

To enable Spaces in a Catalog, complete the following steps:
1. On the Dashboard of the API Manager UI, select the Catalog that you want to work with.

1. Click **Settings** > **Overview**, and click the **Spaces** slider control.

1. In the **Enable Spaces** window, click **Enable**, then click ![Save icon](images/icon_save.png "Save icon").
A **Manage spaces** link is displayed beneath the **Spaces** slider control, and a **Spaces** link is added to
the navigation list. You can manage your Spaces by clicking either of these links.

Spaces are enabled for your Catalog, and a default Space, called New Space is
created.

For more information about using syndication, see the Knowledge Center topics, [Using syndication in IBM API Connect](https://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: external}.

---
copyright:
  years: 2017
lastupdated: "2017-10-24"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configuring a Catalog

You can create and configure your API Manager Catalogs. Catalogs are useful for
separating Products and APIs for testing before you make them available to Developer organizations.
When you configure a Catalog, you can also configure custom branding so that you do not have to use
the default API URL provided by the API Manager.

Complete the following steps to create your Catalog:

1. Click **Navigate to** <img alt="Navigate to icon" src="images/navigate_to_icon.png"> > **Dashboard**.

2. Click **+ Add** > **Catalog **.
The **Add Catalog** window is displayed.

3.  Enter the name of your new Catalog in the **Display Name** field.

4. Enter the text that you want to form the Catalog segment of the URL, in the
**Name** field.
	**NOTE:** The **Name** field can contain only lowercase alphanumeric characters (a-z
	and 0-9), or hyphen characters (-). A hyphen cannot be used as the first or last character in the name.

5. Click **Add**. Your Catalog is created, and is displayed on your dashboard.

6. To configure the Catalog, click the name of the Catalog, then click **Settings** > **Info**, and proceed with the following steps:
  1. If the new Catalog is a development Catalog, select **Development mode**.
If you select the development mode, staging and publishing actions are forced, meaning
that if you republish a previously published Product it is overwritten without warning. If conflicts
are found, they are automatically resolved by the system. Unpublish actions happen automatically.
	**Note:** Approval boxes are not displayed for development Catalogs. You cannot enable the approval process for lifecycles.
  2. If you want to enable automatic subscription for the Catalog, select **Automatic
subscription**.
Enabling automatic subscription makes testing your APIs easier because a test application is used with a pre-supplied client ID and client secret. The test application is automatically subscribed to all of the Plans in the Catalog, so you don't have to specify a plan or application when testing. 
    **Note:** Automatic subscription is available only for a development Catalog.
  3. If the Catalog is the default staging Catalog, select **Default**. Then,
calls to APIs that are published to the Catalog can use a shorter URL that does not include the
Catalog name.
    **Note:** You can only select **Default** for one Catalog.
  4. **Optional**: Click **Endpoints**, and populate the following fields:
        - **Custom Gateway URL**: In the Custom Gateway URL text field, enter a URL. You use the Custom Gateway URL if you want to
        achieve custom branding of URLs for APIs that are deployed to {{site.data.keyword.apiconnect_short}}, rather than using the default URL
        that API Manager generates.
        By default, the {{site.data.keyword.apiconnect_short}} gateway
        URL has the following format:
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        However, you can override the default by specifying a URL that is more appropriate for your enterprise; for
        example, `https://api.mycompany.com`. Any API endpoints that are displayed in the
        Developer Portal will then reflect the specified URL.
			**Notes:**
		    - You must configure a DNS entry that maps your custom host name and domain to the default gateway
		    URL.
		    - For the endpoints of an API to reflect your custom gateway URL, you must configure the API to be
		    enforced by the API Connect gateway. For more information, see [Specifying an alternative host for an API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.
		    - Ensure that the same custom gateway URL is not applied to multiple Catalogs as the behavior in
		    that scenario is undefined.
				**TIP**: When you call the API, you can also set the HTTP host header on the API request to the value that you specified in the Custom Gateway URL field.

	    - **Custom API URL**
	    In the Custom API URL text field, enter the URL. You use the Custom API URL to specify the URL
	    for APIs that are deployed to a third party gateway.

	    The Custom API URL represents the endpoint by which the API is known externally; that is, the
	    endpoint that is published to the developer portal and used by an application developer to invoke or
	    advertise the API.

	    If you are using a third party gateway or external load balancer in this Catalog, supply the URL
	    in this field. Any API endpoints that are displayed in the developer portal will then reflect the
	    specified URL. These endpoints exist on the third party gateway or load balancer and project a
	    virtual address, exposed to API consumers, that is mapped to the API proxy or API assembly endpoints
	    on the gateway. The endpoints that are derived from the custom API URL are typically published in
	    production developer portals to advertise the address of the API.

	    **Note:** If you specify a custom API URL for a Catalog, it takes precedence over any host name that you
	    specify when you configure the API. For more information, see [Specifying an alternative host for an API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){:new_window}.

	    - **Hostname for Developer Portal API Calls**:
	    In the Port API Endpoint window area, enter a host name for Developer Portal API calls. The host
	    name that you enter can be the host name of your Management service. To access the Developer
	    Portal API within the context of a Developer Portal, you must configure the base host name for the
	    Developer Portal API calls. This action allows API Manager to map your host name to the
	    provider organization and Catalog of the Developer Portal API calls instead of requiring you to look
	    it up and include them in your calls.

7. Click the **Save** icon.

## Partitioning a Catalog
{: #apic_spaces}

To use the syndication feature in {{site.data.keyword.apiconnect_short}}, you must enable Spaces in any
Catalog in which you require syndication capabilities.

To enable Spaces in a Catalog, complete the following steps:
1. On the Dashboard of the API Manager UI, select the Catalog that you want to work with.

2. Click **Settings** > **Overview**, and click the **Spaces** slider control.

3. In the **Enable Spaces** window, click **Enable**, then click the **Save** icon <img src="images/icon_save.png" alt="save icon"/>.
A **Manage spaces** link is displayed beneath the **Spaces** slider control, and a **Spaces** link is added to
the navigation pane. You can manage your Spaces by clicking either of these links.

Spaces are enabled for your Catalog, and a default Space, called New Space is
created.

For more information about using syndication, see the Knowledge Center topics, [Using syndication in IBM API Connect ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){:new_window}.

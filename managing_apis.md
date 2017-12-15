---

copyright:
  years: 2017
lastupdated: "2017-12-15"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Managing APIs
{: #managing_apis}

You can use API Connect to manage APIs in {{site.data.keyword.Bluemix}}, whether they are in {{site.data.keyword.Bluemix_notm}} or maintained outside of {{site.data.keyword.Bluemix_notm}}. Managing your APIs allows you to control usage, increase adoption and track statistics.

If you are a customer, you can manage how it is used within the API Manager UI after a developer creates an API and pushes the product to {{site.data.keyword.Bluemix_notm}}. The following topics describe how to create and manage products within {{site.data.keyword.apiconnect_short}}.

## Exposing on-premises APIs through a Secure Gateway
{: #expose_apis_sec_gate}

You can create a secure gateway to safely expose on-premises APIs to {{site.data.keyword.apiconnect_full}}.

When you create a secure gateway, you integrate the features of the {{site.data.keyword.Bluemix_notm}}
{{site.data.keyword.SecureGateway}} service with {{site.data.keyword.apiconnect_short}}. This means that you have a secure
way to access your on-premises APIs from {{site.data.keyword.apiconnect_short}} through a secure passage without the
need to provision a separate instance of the {{site.data.keyword.SecureGateway}} service. Effectively you create a tunnel
to {{site.data.keyword.apiconnect_short}} on a public environment
without exposing your on-premises data. All that you need to do is, create the gateway and attach it
to an API. The creation of a destination, SSL profile, and certificates are all completed for you.
For more information about the {{site.data.keyword.SecureGateway}} service, see [About {{site.data.keyword.SecureGateway}}](../../services/SecureGateway/sg_overview.html#sg_overview).
To create a secure gateway, complete the steps in the following topics.

### Creating a secure gateway
{: #create_sec_gate notoc}

When you create a secure gateway, a gateway ID and security token is generated for you.
You also set up a secure gateway client on your on-premises environment for {{site.data.keyword.apiconnect_short}} to connect with. After the client is set up, you use the gateway ID and security token to connect to the client so that you can access
your on-premises APIs.

To create a gateway, complete the following steps:

1. Click **Navigate to** <img alt="Navigate to icon" src="images/navigate_to_icon.png"> > **Admin** > **Secure Gateways**.
The `Secure Gateways` page is displayed and a Secure Gateways
guided tour is displayed in the corner of the UI.

2. **Optional**:
Click through each step of the guided tour to complete your gateway setup.

3. Click **Add**.
The `Create Secure Gateway` dialog box is displayed.

4. Provide a name for your gateway.
    **Note:** Only alphanumeric characters and underscores are permitted.

5. Click **Save**.
The gateway is displayed along with the gateway ID and security token.

6. Click **Set Up**.
Clicking **Set Up** enables you to download and install a secure gateway
client on your on-premises workstation to connect a remote network to a secure gateway in the Bluemix&reg; network.

    The `Set Up Secure Gateway Clients` window is displayed.

7. Click the client that you want to use from the following options:

    - IBM&reg; Installers
    - Docker
    - IBM DataPower&reg;

8. Follow the on-screen directions to install and run the client that you selected.
For more information about setting up a secure gateway client, see [Setting up a client](../../services/SecureGateway/sg_021.html#sg_021).

9. When you finish installing the client, close the **Set Up Secure Gateway Clients** window.

10. Refresh the page.

The client is connected and the gateway ID and status is displayed. You have completed your
gateway configuration and created a secure gateway.
Next, use the secure gateway to access your on-premises APIs.

### Using the secure gateway with your APIs
{: #using_sec_gate_apis notoc}

When you have configured the gateway, you can use it with your APIs.
{:shortdesc}

To use your secure gateway with APIs, complete the following steps:
1. Create your API and Product as described in the following steps.
  - Click **Navigate to** <img src="images/navigate_to_icon.png" alt="Navigate to icon" /> > **Drafts** > **APIs** > **Add**.
  - Select the type of API that you want to create.
  - Select or click **Add a Product**. **IMPORTANT**: Do not publish the Product yet.
  - Click **Create API**.
  The API is displayed in the `Design` View.
  
2. Click **Assemble**.

3. Click the **invoke** policy to open the **invoke** palette.
**RESTRICTION**: Logic switches, for instance `Switch`, `Operation Switch`, and
`If`, cannot be used with APIs that use a secure gateway.

4. Select **Access URL through Secure Gateway**.

5. In the URL field, update the `target-url` with the on-premises host name and
port number. For example,
```
target-url: http://onpremdb2.rtp.raleigh.ibm.com:3055$(request.path)$(request.search)
```

6. Click **Save** <img src="images/icon_save.png" alt="Save icon" />.

7. Click the **Source** tab.  Notice the `secure-gateway` field with a `true` value.

8. Click **All APIs** > **Products** and select the Product that you created earlier.

9. Click the **Publish** icon to stage the Product to a chosen Catalog.

10. Select the Catalog that you want to use.

11. Select the staged Product.

12. Click **Publish** and select **Secure Gateway Assignments**.

You have securely exposed your on-premises API to {{site.data.keyword.apiconnect_short}}. Any TLS profiles that are associated
with a destination are added. To check the TLS profiles,
click **Navigate to** <img src="images/navigate_to_icon.png" alt="Navigate to icon" /> > **Admin** > **Security** > **TLS Profiles**.
You can have multiple gateways for each API. You decide which gateway to use when
you publish the API.If you already have the {{site.data.keyword.SecureGateway}} service provisioned, you will be able to
monitor your destinations in the {{site.data.keyword.SecureGateway}} Dashboard. However, you cannot edit any {{site.data.keyword.apiconnect_short}} destinations that are created by the
{{site.data.keyword.apiconnect_short}} service.
Next, test your {{site.data.keyword.SecureGateway}} API.

### Testing your secure gateway API
{: test_sec_gate notoc}

After you have attached the gateway to an API, you can test the API to ensure that the
gateway is working and that it produces the correct response.

To test an API using the secure gateway, complete the following steps:

1. Click <img alt="Navigate to icon" src="images/navigate_to_icon.png" /> > **Drafts** > **APIs**
**<Your API>** > **Assemble**.

2. Click the **Test** icon <img src="images/test_icon.png" alt="test icon"/>.

3. Select a Catalog to test within from the list provided.

4. Select a secure gateway to test with from the list provided.

5. Choose an existing Product from the list that is provided then click **Republish
product**.
   **Important** If this Product is already published to a Catalog, it will republish the
   Product with the new gateway.

6. **Optional**:
Provide a name to create a new Product then click **Create and
publish**.

7. Click **Next**.

8. Select an operation to invoke from the list provided.

9. Click **Invoke**.

The test results are displayed.

## Staging and publishing a LoopBack application
{: #stage_publish_lb_app}

1. In the navigation pane of the API Designer, click **Products**.
The Products tab opens.

2. Select the version of the Product, ensure that you click the version that you want to work with.

3. To publish the run time to {{site.data.keyword.Bluemix_notm}}, click **Publish**.

4. Click **Add and Manage Targets** > **Add IBM Cloud target**.

5. Select the {{site.data.keyword.Bluemix_notm}} **Region** that you want to publish to and sign in.

6. Select the {{site.data.keyword.Bluemix_notm}} **Organization** that you want to publish to.

7.  A list of Catalogs is displayed. Select the Catalog that you want to publish to.

8.  Click **Next**.

9. Select the LoopBack application that you want to publish.
If this is the first time that you are deploying the run time to {{site.data.keyword.Bluemix_notm}}, add a name and click the
**Add** icon.

10.  Click **Save**.

11.  Click **Publish** again and select **Publish application**.

12.  Click **Publish**.

13. In the command line, the API Target URL and API invoke tls-profile is specified for the API.
Make a note of this information. The API invoke tls-profile is always `client:Loopback-client`, but you can retrieve the API Target URL as described in the
following step.
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. In the API Designer UI, complete the following steps:
    1. Click **APIs**.
    2. Select your API.
    3. Click **Assemble**.
    4. In the Assembly editor, click the **Filter policies** icon.
    5. Select **DataPower Gateway policies**.
    6. Click **Save** to save the API.

15.  Next, you need to publish to the API Manager. Click **Publish**.
    1. Select **Publish application** then choose one of the following options:
	    - **Replace existing app**: If you have a published application, select this option to overwrite the existing app.
        - **As a brand new app (using the existing route)**: Select this option to create a new app and provide a name for it in the **New app** field. The service is not interrupted.

    2. Select the following options:
	    - Stage or Publish products
        - Select specific products
        - _your product_
 
    3. Click **Publish**.

To test that the publish worked, complete the following steps:

1. Ensure that the {{site.data.keyword.Bluemix_notm}} app is
running.

2. Open a browser window and navigate to the API target URL.
The application is secure with client validation. If you don’t supply the correct client
certificate, it will error out (this is expected).

3. Navigate to the exposed {{site.data.keyword.apiconnect_short}}
URL.
For example:
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
A 200 response is displayed.

## Configuring a Catalog

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
**Note:** The **Name** field can contain only lowercase alphanumeric characters (a-z
and 0-9), or hyphen characters (-). A hyphen cannot be used as the first or last character in the
name.

5. Click **Add**. Your Catalog is created, and is displayed on your dashboard.

6. To configure the Catalog, click the name of the Catalog, then click **Settings** > **Info**, and proceed with the following steps:
  1. If the new Catalog is a development Catalog, select **Development mode**.
If you select the development mode, staging and publishing actions are forced, meaning
that if you republish a previously published Product it is overwritten without warning. If conflicts
are found, they are automatically resolved by the system. Unpublish actions happen automatically.
**Note:** Approval boxes are not displayed for development Catalogs. You cannot enable the approval
process for lifecycles.
  2. If you want to enable automatic subscription for the Catalog, select **Automatic
subscription**.
Enabling automatic subscription makes testing of your APIs easier because a test application
is used, with a pre-supplied client ID and client secret, which is automatically subscribed to all
the Plans in the Catalog, so you don't have to specify a plan or application when
testing.**Note:** Automatic subscription is available only for a development Catalog.
  3. If the Catalog is the default staging Catalog, select **Default**. Then,
calls to APIs that are published to the Catalog can use a shorter URL that does not include the
Catalog name
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
	        **TIP**: When you call the API, you can also set the HTTP host header on the API
		    request to the value that you specified in the Custom Gateway URL field.

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

## Configuring a Developer Portal
{: #config_dev_portal}

A Developer Portal is the place where your plans are published for application developers
to access and use.

You can build a customized Developer Portal for application developers to use. You have full
administrative control over appearance, content, user settings, and configuration settings.

In addition to allowing application developers to find and use APIs, the Developer Portal
provides more features such as forums, blogs, comments, ratings, and a swagger UI for APIs.

1. In the API Manager UI, select the Catalog that you want to work with.

2. Select the **Settings** tab.

3. Click **Portal**.

4. In the **Portal Configuration** section, select **IBM Developer
Portal**. The Portal URL is displayed.

5. Click **Save**. You are sent an email that contains a one-time login link for the Developer Portal web
admin user.

6. Click the link that is sent in the email and follow the instructions to reset your
password.

Your Developer Portal is configured. You can find the URL for the Developer Portal in the
subject line of the email that you received. You can also find the URL in the API Manager UI by
clicking **Portal** > **Settings**.

For more information about the tasks that you can complete in the Developer Portal, see the IBM
Knowledge Center topics about the [Developer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){:new_window}.

## Configuring permissions for roles
{: #config_permissions_roles}

To configure the Permissions for the roles in API Manager, complete the following
steps.

1. In the API Manager **Dashboard**, click the Catalog that you want to work
with.

2. Click **Settings** > **Permissions**.
The Product management permissions to which you can assign roles are displayed:
  - **Stage**: Allow staging of Products to the Catalog.
  - **View**: Allow viewing and listing of Products in the Catalog.
  - **Manage**: Allow management of Product lifecycle (publishing, deprecating, retiring and archiving).
  - **Approve**: Enable approvals for Product lifecycle state changes.
**Note:** Approval for Product lifecycle state changes is disabled for all development Catalogs.

3. To add a Role to the **Stage**, **View** or **Manage** permissions, click the corresponding **+** icon.
The following list shows the default available roles:
  - Administrator
  - Product Manager
  - API Developer
  - Publisher
The Owner role has all permissions.

4. Enable approvals for Product lifecycle state changes by selecting the required check boxes,
then clicking the corresponding **+** icon to assign the roles that have
permission to approve a lifecycle state change.
The lifecycle state changes that you select are those for which you want to enforce approval.
For example, if you select Publish but leave the others cleared, approval is required when anyone
attempts to publish a Product, but no approval is required for any of the other lifecycle state
changes.
5. To assign the roles that have permission to manage user-defined policies, click the
**+** icon in the **Policy Management** section.
The policy management permissions are displayed, enabling you to assign roles as
required.
6. Click the **Save** icon.

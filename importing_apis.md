---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Importing APIs
{: #importing_apis}

You can use a Swagger definition file to add a REST API.
{:shortdesc}

## Prerequisites
{: #prereq_import_swagger_importing_apis}

Before you begin, ensure that your file conforms to version 2.0 of the Swagger
specification. The format of the file can be JSON or YAML.

To add a REST API by loading a Swagger file, complete the following
steps:

1. In the API Manager UI navigation pane, click **Drafts**, then click
**APIs**.
The APIs tab opens.

2. Click **+ Add** and then select **Swagger 2.0** from the
**Import** section.
The **Import Swagger API** window opens.

3. **Optional**:
To upload a file from your local file system, click **Select file** and, in
your file system, select the file that you want to use. `.json`,
`.yml`, and `.yaml` files are supported if they contain a
valid Swagger definition.

4. **Optional**:
To upload a file from a URL, click **Or import from URL** and then provide
the correct URL in the **URL** field that is presented. If authentication is
required to access the URL, provide a user name and password. `.json`,
`.yml`, and `.yaml` files are supported if they contain a
valid Swagger definition.

5. Click **Import**.
A new REST API definition is created, including Paths and HTTP operations.

When the API definition has been imported, it is shown in the list of API definitions in the
**APIs** tab of the **Drafts** page.
Next, you can edit your API definition as you would any other REST API definition.

## Importing APIs from IBM Integration Bus
{: #tut_import_iib_apic_importing_apis}

With this tutorial, you can import REST APIs that you create with IBM Integration Bus into {{site.data.keyword.apiconnect_full}}, which makes it easier to manage and publish them. 
{: shortdesc}

Before you begin, ensure that your REST API file conforms to version 2.0 of the Swagger specification. The format of the file can be JSON or YAML.

You can use IBM Integration Bus to create REST APIs, which
are specialized applications that can be used to expose integrations as a RESTful web service and
can be called by HTTP clients. After you create the APIs, you can import them into {{site.data.keyword.apiconnect_short}} to manage and publish them.

The following list contains a few advantages of managing your APIs in {{site.data.keyword.apiconnect_short}}:
* You can monitor the number of calls to your API.
* You can control the number of calls to your API.
* You can maintain multiple versions of an API.

For more benefits, see [Managing APIs](managing_apis.html).

To create a REST API in IBM Integration Bus and import it
into {{site.data.keyword.apiconnect_short}}, complete the following
steps:
1. Create the REST API by using IBM Integration Bus. Restriction: You can create a REST API only with the IBM Integration Toolkit, which is provided with the installed version of IBM Integration Bus.
	1. Create a REST API by using the IBM Integration
		Toolkit. For more information about how to complete the tasks for creating a REST API with IBM Integration Bus, see [Developing integration solutions by using REST APIs ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: #new_window} in the IBM Knowledge Center.
		
	2. Open the Create a REST API wizard by selecting **File** > **New** > **REST API**.
		
	3. Enter a name for the REST API. The name that you specify is used as the name of the project in
		the IBM Integration Toolkit.
		
	4. Select one of the following methods of creating the REST API, and complete the procedure:
		
	**From scratch by using the REST API Editor provided with the IBM Integration Toolkit**:
		1. Select **Create a REST API and define resources and operations yourself**.
		2. Click **Finish**. The REST API Editor for the new REST API opens automatically, which you must use to define resources, models, and operations.
		
	**From an existing Swagger 2.0 document**:
		1. Select **Import resources and operations defined in a Swagger document** and click **Next**.
		2. Select the path to the Swagger document that describes the resources and operations that you want in the REST API. You can import the Swagger document from the file system or from an existing project in the workspace. The file is validated for use in a REST API. If any errors are found while the selected Swagger document is validated, those validation errors are displayed at the beginning of the wizard. You cannot proceed if validation errors are found in the selected Swagger document.
		3. Select **Finish** to create the API.
	5. Implement the subflows for your REST API, which are the REST operations that you want to include.
2. Add the REST API project to a new or existing broker archive (BAR) file of the IBM Integration Bus.
3. Deploy the BAR file to IBM Integration Bus on Cloud.
	1. Log in to IBM Integration Bus on Cloud by using your IBMid, if you are not already logged in. Sign up for an account if you do not have one.
	2. Click **Add Integration** > **Upload BAR file**.
	3. Select the BAR file that you created for your REST API project. Tip: You can find the location of your BAR file by right-clicking it in the IBM Integration Toolkit and viewing its properties.
	4. Select **Save**.
	5. Select **Refresh listing** to update the screen.
	6. Verify that the BAR file was successfully uploaded by viewing the API Integration Flow for the API in the *Integrations* window of the IBM Integration Bus on Cloud.
4. Start the integration flow by selecting the start icon ![Screen capture that shows the start icon.](images/a_play_button.jpg " "). The API starts and displays a status of `Running`.
5. Select the integration from the list of integrations to view information about it. The tree in the Contents menu displays the REST API and the subflows that are associated with it. You can also view information in the other sections. In the Public Endpoints section, you can
view the public URL that IBM Integration Bus on Cloud assigned
to your integration flow. Select **Show full URL** to view the complete URL for that operation.
6. Copy the complete URL for the operation to your clipboard. You need it when you configure the API to work with {{site.data.keyword.apiconnect_short}}. If you enabled Basic Authentication, also note the assigned username and password.

### Integrate the IBM Integration Bus with API Connect.
{: #integrateiibapic_importing_apis}

1. Import the Swagger file that is associated with the REST API project in the IBM Integration Toolkit into the {{site.data.keyword.apiconnect_short}} service. 
	1. Log in to your {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} service.
	2. In the API Manager UI navigation pane, select **Drafts** > **APIs**. The APIs tab opens.
	3. Select **+ Add** > **Import API from a file or URL**. The *Import OpenAPI (Swagger)* window opens.
	4. To upload the file that you created from your local file system, select **Select File** and select the file that you created with IBM Integration Bus. Files with the `.json`, `.yml`, and `.yaml` extensions are supported if they contain a valid Swagger definition. Make sure that the option for **Add a product** is selected. You can optionally publish the product by selecting **Publish this product to a catalog**.
	5. Click **Import**. A new REST API definition is created, including Paths and HTTP operations. Tip: Cancel the import, refresh your browser, and try importing it again if it takes longer than 1 minute to import. Your session might be expired.
2. Associate the imported API in {{site.data.keyword.apiconnect_short}} with the API in IBM Integration Bus on Cloud.
	1. Go to the Dashboard of {{site.data.keyword.apiconnect_short}}.
	2. Select **Drafts** > **APIs**.
	3. Click the REST API that you imported.
	4. Select the Assemble tab, and select **Create assembly** to add the proxy policy.
	5. Drag the **Proxy** policy to the new empty policy to enable it.
	6. Paste the URL for your API that you copied from the public Endpoints section of IBM Integration Bus on Cloud.
	7. If you enabled Basic Authentication for your REST API, enter the username and password that were generated in IBM Integration Bus on Cloud.
	8. Save the API settings.
3. Test the API.
	1. In the Assemble tab of your API, select the Test button ![Test button](images/a_play_button.jpg "Screen capture that shows the test button icon.").
	2. Select **Republish product**.
	3. Select the Operation.
	4. Enter the required parameters.
	5. Select **Invoke**.
	6. Verify that you receive the expected response from the API. 
	
When the API definition is imported and integrated, you can manage and govern the APIs as you with any other REST API definition. For more information about the APIs, see [Managing APIs](managing_apis.html).

## Publishing APIs created with IBM App Connect Professional in IBM API Connect
{: #publish_importing_apis}

With this tutorial, you can publish and manage REST APIs that you create with IBM App Connect Professional with {{site.data.keyword.apiconnect_full}}.

### Prerequisites
{: #prereq_pub_api_appconn_importing_apis}

You need valid accounts for IBM App Connect
Professional on Cloud and for {{site.data.keyword.apiconnect_short}} to complete this tutorial. Ensure that your REST
API file conforms to version 2.0 of the Swagger specification. The format of the file can be JSON or
YAML.

You can use IBM App Connect Professional to create REST
APIs, which are specialized applications that can be used to expose integrations as a RESTful web
service and can be called by HTTP clients. After you create the APIs, you can publish and manage
them by using {{site.data.keyword.apiconnect_short}}.
The following list contains a few advantages of managing your APIs in {{site.data.keyword.apiconnect_short}}:

- You can monitor the number of calls to your API.
- You can control the number of calls to your API.
- You can maintain multiple versions of an API.

For more benefits, see [Managing APIs](managing_apis.html).
To create a REST API in IBM App Connect Professional and
publish it to {{site.data.keyword.apiconnect_short}}, complete the
following steps:

1. Create the REST API by using IBM App Connect
Professional.
  - Log in to the [App Connect Professional Web Management Console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/app-connect){:new_window} with your IBMid. For more information about how to complete the tasks for creating a REST API with IBM App Connect Professional Web Management Console, see [About management console settings ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window} in the IBM Knowledge Center.
  - Select the Production tab, if it is not already selected.
  - Select **Repository** > **Configurations** in the navigation panel.
  - On the Project Configurations screen, select the project that you are publishing to {{site.data.keyword.apiconnect_short}}.  The Configuration Details of the project that is being published are displayed.
  - Select **Push to API Management**. 
      **Tip**: The **Push to API Management** button is active only when the project that you are importing has a status of running or deployed. Select the play button to start the project, if the link is not displayed.
  - On the Push to API Management screen, enter the following information to create a connection to the API management system.

  <table><caption>Table 1. Connection information for API publishing to {{site.data.keyword.apiconnect_short}}</caption>
  <thead>
  <tr>
  <th>Field name</th>
  <th>Description</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>Host</td>
  <td>Specifies the host name of the Management Cluster, Server, or Cloud address. For {{site.data.keyword.Bluemix_notm}}, this entry is most likely us.apiconnect.ibmcloud.com.</td>
  </tr>
  <tr>
  <td>Port</td>
  <td>Specifies the port number that is needed to connect to the Management Cluster, Server, or Cloud address.</td>
  </tr>
  <tr><td>User ID</td>
  <td>Specifies the authentication user name that is used for accessing the Management Cluster, Server, or Cloud address. This is most likely your IBMid that you use to log in to {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  <tr><td>Password</td>
  <td>Specifies the authentication password that is used for accessing the Management Cluster,
  Server, or Cloud address. This is most likely your IBMid password that you use to log in to
  {{site.data.keyword.Bluemix_notm}}.</td>
  </tr>
  </tbody>
  </table>

2. Select **Load Organizations** to populate the list of organizations that are
associated with your ID and password.

3. Select **Organizations** to associate the project to one of the
organizations that are available.

4. Select **Push to APIM**, and then select **Ok**.

5. Select **Close** to close the window.
A new browser tab opens in your default browser and displays your API.

Associate the IBM App Connect API with {{site.data.keyword.apiconnect_short}}.

#### Import Swagger API definition
{: #import_sw_importing_apis}

To import the Swagger file that is associated with the REST API project in the IBM App Connect into the {{site.data.keyword.apiconnect_short}} service, follow these steps:

1. Log in to your {{site.data.keyword.apiconnect_short}}
{{site.data.keyword.Bluemix_notm}} service.

1.  In the API Manager UI title bar, select **Navigate to** > **Drafts**.

2. Select **APIs** in the menu bar.
The APIs tab opens.

3. Select your imported API to open the API Designer.

4. Select **Assemble** in the navigation window.
A list of policies is displayed in the navigation window.

5. Select **Create assembly**, if necessary.

6. Add the **Invoke** policy by dragging it to your assembly in the main
window.

7. Select the **Invoke** policy on the main window to modify its configuration
settings.

8. Configure the host/basePath to the URL field with the following information:

- **hostname**: Setting that depends on your cloud instance. For more information about this setting, see
[IBM App Connect Professional ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SS3LC4_7.5.2.0/mapfiles/ic_home.html){:new_window}.

- **basepath**: Path that you specify on the httpReceive Request note in App Connect Professional orchestration.

9. Add and save your IBMid user name and password to the Http Basic authentication details that
you use for App Connect Professional.

#### Test the API
{: #test_importing_apis}

To test the API, follow these steps:

1. In the Assemble tab of your API, select the Test button <img alt="Screen capture that shows the test button icon" src="images/a_play_button.jpg" />.
2. Select **Republish product**.
3. Select the Operation.
4.  Enter the required parameters.
5. Select **Invoke**.
6. Verify that you receive the expected response from the API.

When the API definition is imported and integrated, you can manage and govern the APIs as
you would with any other REST API definition. For more information about the APIs, see [Managing APIs](/docs/services/apiconnect?topic=managing_apis).



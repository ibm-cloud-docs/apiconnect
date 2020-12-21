---
copyright:
  years: 2018,2020
lastupdated: "2020-12-21"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial, API Connect V5

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}


# Creating an API in Node.js
{: #tut_create_api_node}

**Duration**: 20 mins  
**Skill level**: Beginner  

---
## Objective
{: #object_tut_create_api_node}

This tutorial guides you through creating an API in Node.js using the LoopBack framework with API Connect V5. The tutorial describes how to:
1. Create a LoopBack project.
2. Use API Designer in the {{site.data.keyword.apiconnect_full}} toolkit to add a data source and model to a LoopBack project.

---
## Prerequisites
{: #prereq_tut_create_api_node}

Before you begin, [install the {{site.data.keyword.apiconnect_short}} toolkit](/docs/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit) version 5.0.8.1, or later. Check the version of an existing toolkit by opening a command window and running the following command::
	```
	apic -v
	```

---
## Create a Loopback project
{: #create_tut_create_api_node}

You can create a Loopback project with either the {{site.data.keyword.apiconnect_short}} developer toolkit command line interface (CLI) or API Designer interface. 
 
### Create a LoopBack project with the toolkit CLI
{: #create_cli_tut_create_api_node}

To create a LoopBack project with the {{site.data.keyword.apiconnect_short}} toolkit CLI, complete the following steps:
1.  Run the following command to create a LoopBack application.
	```bash 
	apic loopback
	```
	For this tutorial, you will create a project called weather-data.
2.  At the prompt, enter `weather-data` as the project name and press **Enter**.
	```bash
	? What's the name of your application? weather-data
	```

  	A project name can contain any characters except blank space (" "), forward slash ("/"), ampersand ("&"), at ("@"), plus ("+"), percent ("%"), and colon (":").
	
3.  Enter the name of the directory in which to create the project. Press **Enter** to use a directory with the same name as the project, or type a new name and press **Enter**.
	```bash
	? Enter name of the directory to contain the project: weather-data
	```
4.  Select the version of LoopBack to use. Choose the current production version: 3.x.
	```bash
	? Which version of LoopBack would you like to use? 
  	2.x (long term support) 
	? 3.x (current) 
	```
5.  Specify the kind of application that you want to create by using the arrow keys to select **empty-server**.
	```bash
	? What kind of application do you have in mind? (Use arrow keys)
	? empty-server (An empty LoopBack API, without any configured models or datasources) 
  	hello-world (A project containing a basic working example, including a memory database) 
  	notes (A project containing a basic working example, including a memory database)
	```
6.  Press **Enter** to create an empty LoopBack API. 

The tool displays a number of messages as it creates the project directory and adds a number of directories and files to it. It also runs npm install to install all the project dependencies, as specified in package.json. This process creates a node_modules directory and might take some time.

An empty LoopBack project contains the following directories:
- server: contains server model and data source definitions, and other server code
- definitions: contains YAML definition files
- node_modules: created by node.js


### Create a LoopBack project using API Designer
{: #create_apid_tut_create_api_node}

To create a LoopBack project using API Designer, complete the following steps:
1.  Run the following command to start API Designer:
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	The command initializes the {{site.data.keyword.apiconnect_short}} toolkit and opens API Designer in the default browser.
2.  Pin the UI navigation pane by clicking ![Navigate icon](images/navigate-to.png "Navigate icon"). When the API Manager UI navigation pane opens, click ![Pin icon](images/pinned.png "Pin icon").
3.  In the side bar, click ![Projects Plus icon](images/add-icon.png "Projects Plus icon").
4.  Click **Create LoopBack Project**. You'll see the **Add new LoopBack project ** dialog.
5.  Select **empty-server** as the project template.
6.  For **LoopBack Version**, select version 3.x (the current version).
7.  Enter `weather-data` for the Display Name and Name fields.
8.  For the **Project Directory**, select the `weather-data` folder created in step 1 by clicking **Browse**.
	![](images/api-designer-2.png)
9.  Click **Add** to add the project.
	A number of messages display in the **Add new LoopBack project** window as it creates the project directory and adds a number of directories and files to it. It also runs npm install to install all the project dependencies, as specified in package.json. This process creates a node_modules directory and might take some time.
	
	An empty LoopBack project contains the following directories:
	- server: contains server model and data source definitions, and other server code
	- definitions: contains YAML definition files
	- node_modules: created by node.js
10. Click **Finished** to close the **Add new LoopBack project** dialog box.
11. Exit API Designer by returning to the command window and entering `Ctrl + C`. Type `Y` to confirm the exit.
12. Close the browser session.

---
## Add a data source and model
{: #add_tut_create_api_node}

To add a model and data source to a LoopBack project using API Designer, complete the following steps:

### Add a data source
{: #add_ds_tut_create_api_node}

To add a data source to a LoopBack project using API Designer, complete the following steps.
1. You must also create a LoopBack project (the "weather-data" project) as described in `Create a LoopBack project from the command line` and make sure that the current working directory is the project root directory:
	```bash
	cd weather-data
	```
2. From the command line, enter the following command:
	```bash
	apic edit
	```
	After a brief pause, the console displays this message:
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer opens in your default web browser, initially displaying the login page if you haven't logged in recently.  
	You can log in using your {{site.data.keyword.cloud_notm}} account or create one.
3. Click ![Data Sources icon](images/datasource-icon.png "Data Sources icon").
4. Click **Add**. The "New LoopBack Data Source" window opens.
5. Enter `weatherDS` in the **Name** text field.
	Use any alphanumeric characters, dashes, and underscores in a data source name.
6. Click **New**.
7. By default, the **Connector** setting shows **In-memory db** and the other settings are blank. Keep the default settings for now, and API Designer automatically saves the new data source.
	The In-memory data source is built into LoopBack and is suitable only for development and initial testing. When you are ready to connect your models to a real data source such as a database server:
	- Change the **Connector** setting.
    - Install the data source connector as explained in the IBM Knowledge Center topic, [Installing LoopBack connectors](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv){: external}.
    - Enter the connector settings (host name, port, database name, user name, password) as appropriate for your Connector type, and click ![Save icon](images/save-icon.png "Save icon"). 
	
	API Designer automatically tests the connection to the data source. A successful test displays the message **Success - Data source connection test succeeded**.
8. Click ![Test Connection icon](images/db-test-icon.png "Test Connection icon") to test the data source connection. The message "Data source connection test succeeded" is displayed.
9. Click **All Data Sources**. The data source will appear in the list of data sources, and the editor updates the server/datasources.json file with settings for the new data source.

### Add a model
{: #add_model_tut_create_api_node}

To add a model to a LoopBack project using API Designer, complete the following steps:
1. Click ![Models icon](images/models-icon.png "Models icon").
2. Click **Add**. The New LoopBack Model window opens.
3. Enter `weather` in the **Name** text field, then click **New**.
4. In the **Data Source** field, select **weatherDS**.
	![](images/new-model-1.png)
5. In the **Properties**, click ![Add property icon](images/add-icon.png 'Add property icon").
6. In the **Property Name** text field, enter `zip_code`.
7. For **Type**, select **number**.
8. Select **Required** to make the property required. This means that it must have a value when you add or update a model instance. 
9. Select **ID** to ensure that the property has a unique identifier. For now, keep the default values for the other settings:
	- **Is Array**: Whether the property is a JavaScript array with elements of the specified type.
	- **Index**: Whether the property represents a column (field) that is a database index.
	- **Description**: Text description of the property.
9. Click ![Add property icon](images/add-icon.png 'Add property icon") again to add another property.  Reference the table below to complete the remaining properties:
	![](images/new-model-property-1.png)
10. Click ![Save icon](images/save-icon.png "Save icon") to save your changes.
11. Click **All Models** to finish editing the model.

This completes adding a data source and model to the weather-data LoopBack project.

---

## What you accomplished in this tutorial
{: #conclusion_tut_create_api_node}

In this tutorial, you completed the following:
1. Created a LoopBack project using the {{site.data.keyword.apiconnect_short}} toolkit command line.
2. Added a model and data source to a LoopBack project by using API Designer in {{site.data.keyword.apiconnect_short}} toolkit.


---

## Next step
{: #next_tut_create_api_node}

[Manage a REST service](/docs/apiconnect/tutorials?topic=apiconnect-tut_rest_landing) or [Manage a SOAP service](/docs/apiconnect/tutorials?topic=apiconnect-tut_manage_soap_api).

Create > **Manage** > Secure > Socialize > Analyze

 

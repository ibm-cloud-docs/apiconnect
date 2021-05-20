---

copyright:
  years: 2017, 2021
lastupdated: "2017-10-31"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials, API Connect V5

subcollection: apiconnect

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}


# Securing your API with Client ID and Client Secret using the Developer Toolkit
{: #tut_secure_id_secret_tk}

**Duration:** 10 mins  
**Skill level:** Beginner


## Objective
{: #object_tut_secure_id_secret_tk}

This tutorial guides you through securing your API with Client ID and Client Secret in API Connect V5. When applications are registered in your Developer Portal, a Client ID is generated to identify the application. Optionally, a Client Secret (which serves as a password) can also be generated. Applications need to supply the Client ID and Client Secret keys when calling your API.


## Prerequisites
{: #prereq_tut_secure_id_secret_tk}

Before you begin, complete one of the following tutorials:
- [Import an OpenAPI2.0 spec and proxy an existing REST service](/docs/apiconnect/tutorials?topic=apiconnect-tut_rest_landing).
- [Add a New API Spec and Invoke an Existing REST Service](/docs/apiconnect/tutorials?topic=apiconnect-tut_rest_landing).


## Set the identification mechanism of your API
{: #set_id_tut_secure_id_secret_tk}

1. Start API Designer:  
   a. Open a command window.  
   b. Run the following command: `apic edit` 
      API Designer opens in your default web browser.
   c. Click **Sign in with {{site.data.keyword.cloud_notm}}**.  
   d. Enter your {{site.data.keyword.cloud_notm}} login information.  

2. Navigate to your API's Design view:
    a. Click **Drafts** in the navigation panel. 
    b. Click the **APIs** tab.
    c. Click the _Weather Provider API_ that you created in a previous tutorial. 
	   The API opens in the **Design** view.  
    ![](images/1_goto_drafts_api.png)  

3. In the Design view:  
   b. In the "Security Definitions" section, click the **Add Security Definitions** icon (+), and then click **API Key**.  
       ![](images/1b.png) 

	  Add two keys using the following settings:
      - Name: Client ID; Parameter name: X-IBM-Client-ID  
      - Name: Client Secret; Parameter name: X-IBM-Client-Secret  
      For both new keys, ensure that the **Located In** field is set to "Header".  
      ![](images/2a.png)    

4. In the "Security" section, add a security option:  
   a. Select the new Client ID and Client Secret keys.  
   b. Save your API.  
   c. Click the **Assemble** tab.  
    ![](images/3a.png) 

## Test the changes made to your API
{: #test_tut_secure_id_secret_tk}

1. In the Assemble tab, click the Test icon to test your changes.
2. In the Test panel, click the **get /current** operation.
3. Notice that Client ID and Client Secret values are already populated.
   The values are generated for your Sandbox. Applications that call your API need to supply these values.  

   These Client ID and Client Secret keys can also be found under  **Dashboard** > **Catalog** > **Settings** > **Endpoints**  
   {: note}
   
 ![](images/test_api_keys_1.png)

4. Enter a valid US zip code (for example, 90210). 
5. Click **Invoke**.
   The API returns `200 OK` response, along with the message body returning the weather information.
6. Return to the Client ID field. 
7. Replace the Client ID with a random value.
8. Run the test again by clicking **Invoke**. 
   This time, you receive the `401 Unauthorized` response with the message "Client ID not registered". 
  ![](images/test_api_keys_3.png)  
  

## Call your API using the Client ID and Client Secret
{: #call_tut_secure_id_secret_tk}

The security settings can also be tested using the Explore tool. The Explore tool explicitly calls the proxy endpoint, and passes the Client ID and Client Secret keys as header values.


1. Click **Explore**.
    ![](images/explore_1.png)

2. Click the **GET /current** operation from the list.  

3. Click **Call operation** to run the test.  
    ![](images/4.png)  
    
---

### Conclusion
{: #conclusion_tut_secure_id_secret_tk}

In this tutorial, you learned how to set the identification mechanism of your API, test changes made to your API, and call your API using the Client ID and Client secret. 

---

## Next step
{: #next_tut_secure_id_secret_tk}

Start to socialize your API by [setting up and configuring a developer portal](/docs/apiconnect?topic=apiconnect-tut_config_dev_portal).

Create > Manage > **Secure** > Socialize > Analyze

---

copyright:
   years: 2017, 2021
lastupdated: "2017-11-02"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials, API Connect V5

subcollection: apiconnect

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Setting up rate limits in API Connect V5
{: #tut_rate_limit}

**Duration**: 15 mins  
**Skill level**: Beginner  


## Objective
{: #object_tut_rate_limit}

This tutorial shows you how to establish rate limits on your APIs. A rate limit is the maximum number of calls that you want to allow in a particular time interval. Setting rate limits enables you to manage the network traffic for your
APIs and for specific operations within your APIs. 

In {{site.data.keyword.apiconnect_full}}, *Products* provide a way of grouping APIs into a package for a particular set of users, or _consumers_. Products also contain *Plans*, which specify whether the set of APIs are controlled with rate limits, and whether subscriptions to the Product reuqire approval from your organization.

When an application developer wants to use your APIs, they select a Product that contains the API they want to use, and subscribe to one of that Product's Plans.

In this tutorial, you will complete the following tasks to estable a rate limit on an API:
1. Create a new rate-limited Plan in an existing Product.
2. See what happens when an application exceeds the allowed rate limits.


## Prerequisites
{: #prereq_tut_rate_limit}

You must have already created an API in {{site.data.keyword.apiconnect_short}}, secured with at least an API Key. In the following instructions, our starting point is the [Weather Provider API example file](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){: external}, secured using a client ID and secret.

Complete the following tutorials to set up the prerequisite conditions for this tutorial:
- [Import your API spec, and proxy an existing REST service](/docs/apiconnect/tutorials?topic=apiconnect-tut_rest_landing).
- [Secure your API with a client ID and secret](/docs/apiconnect/tutorials?topic=apiconnect-tut_secure_landing).


---
## Launching API Connect
{: #launch_tut_rate_limit}

1. Log in to {{site.data.keyword.cloud_notm}}: [https://cloud.ibm.com/login](https://cloud.ibm.com/login){: external}.
2. Click **All Services**, and then select **API Connect**.
3. Click **API Connect** to start the {{site.data.keyword.apiconnect_short}} service.

## Exploring the Default Plan
{: #explore_tut_rate_limit}

1. In the {{site.data.keyword.apiconnect_short}} navigation panel, select **Drafts**. (If the navigation panel is not open, click **>>** to open it.)
2. Select the **Products tab**, and verify that the Weather Provider API product displays in the list.

   ![](./images/draftproducts.png)      

3. Click the Product link, and the Design view opens, displaying information about the Product.

4. Look in the Plans section of the page. A Default Plan was created when you generated this Product. 

   ![](./images/defaultplanlist.png)    
5. Expand the Default Plan details. Notice the default rate limit (100 calls / 1 Hour) and API list, which can be expanded to show specific operations.

   ![](./images/defaultplandetails.png) 

   
## Creating a rate-limited Plan
{: #create_tut_rate_limit}

Create a Plan with more restrictive rate limits, to demonstrate what happens when an API consumer exceeds a Plan's limits. 

1. Click the button to add a Plan.
 
    ![](./images/newplanbutton.png) 
    
    A new Plan is created for you, and by default, it is set to allow unlimited usage (that is, no rate limits at all). Let's give it a more meaningful name, and set a more restrictive limit. 
2. Click the new Plan (`New Plan 1`) to expand the details.
3. Click the Title field and set the Plan title to: `Demo`.
4. Click the Name field and set the Plan name to `demo-plan`.
5. Click + to add a new rate limit.
6. Rename the new rate limit to `demo-rate-limit`, and ensure it is set to `1 / 1 Minute`.
7. Check the `Enforce hard limit` checkbox. 
   When `Enforce hard limit` is enabled, an application receives an error if it exceeds the rate limit by callin an API more times that allowed in hte specified time period.
8. Accept the remaining default settings and save the Product.

   ![](./images/demoplan.png) 


## Staging & publishing an updated Product to the Sandbox Catalog
{: #stage_tut_rate_limit}

In previous examples, you might have published your Product using the test tool, which calls your API with a pre-supplied test application's credentials. The test application is not subject to rate limits, so you must create a new application for rate limiting purposes. For more information on creating products, see the [IBM Knowledge Center content for API Connect](https://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.toolkit.doc/tapim_create_product.html){: external}.

1. Click the Publish icon to *stage* the Product to the **Sandbox** Catalog. 
   Staging the Product adds it to the selected Catalog. We need to *publish* the Product changes next, to make them available to consumers via the Developer Portal.
   ![](./images/stageproduct.png) 
2. Click the >> button to open the navigation menu.
3. Select Dashboard, then open the **Sandbox** Catalog. The Weather Provider API Product is listed as **Staged**.
4. Click the More Actions menu (the three dots), and select **Publish**.
   ![](./images/publish.png) 
5. Accept the default visibility settings and click the **Publish** button. When the Product is published and made visible on the Developer Portal, application developers can subscribe to the available Plans.


## Registering a consumer application in the Developer Portal
{: #reg_tut_rate_limit}

Application developers discover and use your APIs by using the Developer Portal. For more information on the Developer Portal, check out this [IBM Knowledge Center topic](https://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/tapim_tutorial_using_ADP.html){: external}.

If this is your first time working with the Developer Portal, you must provision a Developer Portal for your Sandbox Catalog. The account you are logged in as when you provision the Portal is used as the administrator account for that Portal. Then, you need to create and log in with a new developer account to explore and test APIs.

Complete the following steps to set up the Developer Portal for testing:

1. Start the Developer Portal. If you don't know the URL, you can find it in the Settings tab of the Sandbox Catalog. To provision the Developer Portal for the first time, see [see setting up and configuring your Developer Portal](/docs/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).
    - Provisiong the Developer Portal takes up an hour. When your Sandbox Developer Portal is ready, you will receive an email
with a single-use link to your new Developer Portal site. The link is a single-use link for the administrator account.
2. Log into the Portal using your app developer credentials (**not** your IBM id). ***(Create a new developer account if necessary, using a different address than your IBM id.)***
3. Click the **Apps** link on the toolbar, and click the **Create new App** button.

4. Give the application a title and click **Submit**.

   ![](./images/mymobileapp.png)
5. Save the client secret and client id displayed. This will be the only time your client secret is available for you to copy!

   ![](./images/clientidandsecret.png)
   
   ![](./images/clientsecret.png)



## Subscribing to an API Product
{: #subscr_tut_rate_limit}

1. Click the **API Products** link on the toolbar. Your Weather Provider API Product is listed! 

   ![](./images/apiproducts.png)
2. Click the link to see details and options. Two Plans are available: the original Default Plan, and your new Demo Plan. 
   If you only see one Plan, return to {{site.data.keyword.apiconnect_short}} and ensure that your Product changes have been saved, staged, and published to the Sandbox Catalog.

   ![](./images/plans.png)
3. Click to **Subscribe** to the Demo Plan, and select the application you just registered. Now, your application can call the APIs associated with this Plan, at a rate of up to *one* API call every minute. 

We are ready to test this behavior and observe what happens when the application exceeds the specified rate.

## Calling a rate-limited API
{: #call_tut_rate_limit}

1. On the Weather Provider API Product page in the Developer Portal, click the API link.

   ![](./images/weatherproviderapi.png)
2. The page refreshes to display details about the API, and to provide a place for testing the API. 
   This is how your API consumers will discover and test out your API as well. 
   
3. Locate the first **Try this operation** section.

4. To test the `GET /current` operation, enter your application's client secret and a valid US zip code. 

5. Click the **Call operation** button. 
   The response displays the `200 OK` status and data about the current weather in the specified zip code. 

   ![](./images/trythisop-1.png)

   ![](./images/response-1.png)

6. Now, _before a minute passesp_, click the the **Call operation** button again (with a different zip code if you prefer). 
   This time, the response is the `429 Too Many Requests` status.

   ![](./images/response-2.png)

7. To validate that the rate-limit resets, wait a minute. Then, try again and confirm that you receive a valid response.


## Conclusion
{: #conclusion_tut_rate_limit}

Congratulations! You have successfully created a rate-limiting Plan, associated it with your secure API, and verified that your API only responds to requests within the parameters you specified.

---

## Next step
{: #next_tut_rate_limit}

Start to socialize your API by [setting up and configuring a developer portal](/docs/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal).

Create > Manage > **Secure** > Socialize > Analyze

---

copyright:
  years: 2017
lastupdated: "2017-11-20"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Discovering APIs
{: #tut_discover_apis}

**Duration**: 25 mins  
**Skill level**: Beginner  

## Objective
{: #object_tut_discover_apis}

In this tutorial, you will learn how a portal user might consume the APIs in the {{site.data.keyword.apiconnect_full}} Developer Portal. You will gain an understanding of how a portal user would explore products and APIs, view and test APIs, and subscribe to APIs. 

## Prerequisite
{: #prereq_tut_discover_apis}

There is no prerequisite for this tutorial. As a portal administrator, you can also complete this tutorial while you navigate your developer portal to experience how your portal users navigate your developer portal. Keep in mind that all developer portals have different skins. 

If you do not have an existing developer portal, you can set up and configure a developer portal in {{site.data.keyword.Bluemix_short}} before proceeding with this tutorial.

## Explore Products & APIs
{: #explore_tut_discover_apis}

This section shows how a portal user would explore the products and APIs in the developer portal.

1. In a browser, navigate to your **API Connect Developer Portal**.
![API Connect Developer Portal](images/11-developer-portal.png)

2. In the {{site.data.keyword.apiconnect_short}} Developer Portal, select the API Products tab. 
![API Products](images/12-API-products.png)

3. Select one of the available API products to display the available APIs and Plans for the product.  
  ![Select Product](images/13-product.png)

4. Select an API to explore the details of the available APIs.  
  ![Products APIs](images/14-api.png)

5. On the details page of an API, you can view the available operations along with their parameters and the responses returned. At the end of the page, you can view the definitions that are used by the API.  
  ![API Details](images/15-details.png) 

6. In the Code examples panel, you can view examples in different coding languages of how to invoke the requests and their responses. Select one of the examples, such as **Node**, to see an example in that coding language.  
  ![API Details](images/16-examples.png) 

---

## View and test the APIs
{: #view_tut_discover_apis}

This section shows how a portal user would view and test the available APIs for a product. 

1. Navigate to the API details in the {{site.data.keyword.apiconnect_short}} Developer Portal as outlined in the previous section.  
  ![API Details](images/21-details.png) 

2. You can download and view the APIs Swagger yaml information by selecting **Open API**.  
  ![Download Swagger yaml](images/22-swagger.png) 

3. Scroll down to one of the operations to view its details. You can also click on the operations link to jump to it on the page. 
![Operation](images/23-operation.png)

4. In the right panel under the examples, scroll to the **Try this operation** section. Enter the parameters and select **Call operation**.  
  ![Try this operation](images/24-try-this-operation.png)

5. Scroll down to view the request and response of the operation call. A returned response of **200 OK** and the message body are displayed, indicating that the operation call was successful.  
  ![Operation response](images/25-operation-response.png)

---

## Subscribe to APIs
{: #subscr_tut_discover_apis}

This section shows how a portal user would subscribe to APIs in the developer portal. 

1. Select **Create an account**. 
![API Products](images/31-create-account.png)

2. Complete the required fields and select **Create new account** at the bottom of the page. 
**Note:** Use a different email address than the one that you used to create your developer portal in the previous tutorial.
![API Products](images/32-create-new-account.png)

3. After the developer account is created, log in to view the home page. You must have an app to subscribe to the APIs. Select **Apps** to go to the registered apps page.  
  ![API Products](images/33-login.png)

4. To register a new application, select **Create new App**.  
  ![Register new app](images/34-create-new-app.png)

5. Enter a *Title* and *Description* for your app and select **Submit**.  
  ![Submit new app](images/35-submit-new-app.png) 

6. Now that you have an App, you can subscribe to API Product plans. Select **available APIs** or **API Products** to browse the API Product plans.  
  ![API Details](images/36-api-products.png) 

7. Select the API Product you want to subscribe to.  
  ![API Product](images/37-select-product.png) 

8. Select **Subscribe** to subscribe to the API Product Plan.  
  ![API Product Plan](images/38-subscribe-plan.png) 

9. Select the app that you want to subscribe to the product Plan, then select **Subscribe**. 
  ![App Subscribe plan](images/39-subscribe-app-plan.png) 

10. Your application has successfully subscribed to the product Plan. 
  ![App Subscribe Success](images/310-subscribe-success.png) 

## Conclusion
{: #conclusion_tut_discover_apis}

In this tutorial, you learned how your portal users would explore products and APIs, view and test APIs, and subscribe to APIs. 

---

## Next step
{: #next_tut_discover_apis}

Learn [how to gain insights from basic analytics](/docs/services/apiconnect/tutorials?topic=tut_insights_analytics).

Create > Manage > Secure > **Socialize** > Analyze  




---

copyright:
  years: 2017
lastupdated: "2017-07-14"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Getting Started Discovering APIs
**Duration**: 30 mins  
**Skill level**: Beginner  


## Prerequisite
Before you begin, you will need to [install {{site.data.keyword.apiconnect_full}} Developer Portal](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.install.doc/tapim_portal_installing_VA.html). 


## Objective
In this tutorial you will learn how to consume the APIs in the {{site.data.keyword.apiconnect_short}} Developer Portal. You will gain an understanding of how to explore products and APIs, view and test APIs, and subscribe to APIs. 
 

## Explore Products & APIs
In this section, you will explore the products and APIs in the developer portal.

1. In a browser, navigate to your **API Connect Developer Portal**.
![API Connect Developer Portal](images/11-developer-portal.png)

2. In the {{site.data.keyword.apiconnect_short}} Developer Portal, select the **API Products** tab. 
![API Products](images/12-API-products.png)

3. Select one of the available **API products** to display the available APIs and Plans for the product.  
  ![Select Product](images/13-product.png)

4. Select an **API** to explore the details of the available APIs.  
  ![Products APIs](images/14-api.png)

5. In the details page of an API you can view the available operations along with their parameters and the responses returned. At the bottom of the page you can view the definitions used by the API.  
  ![API Details](images/15-details.png) 

6. In the right panel, you can view examples in different languages for how to invoke the requests and their responses. Select one of the examples, such as **Node**, to see an example in that language.  
  ![API Details](images/16-examples.png) 

---

## View and test the APIs
In this section, you will learn how to view and test the available APIs for a product. 

1. Navigate to the API details in the {{site.data.keyword.apiconnect_short}} Developer portal as outlined above.  
  ![API Details](images/21-details.png) 

2. You can download and view the APIs Swagger yaml by selecting **Open API**.  
  ![Download Swagger yaml](images/22-swagger.png) 

3. Scroll down to one of the operations to view its details. You can also click on the operations link to jump to it on the page. 
![Operation](images/23-operation.png)

4. In the right panel under the examples, scroll down to the **Try this operation** section. Enter the parameters and select **Call operation**.  
  ![Try this operation](images/24-try-this-operation.png)

5. Scroll down to view the request and response of the operation call. A returned response of **200 OK** and the message body are displayed, indicating that the operation call was successful.  
  ![Operation response](images/25-operation-response.png)

---

## Subscribe to APIs
In this section, you will learn how to subscribe to APIs in the developer portal. Before you can subscribe to an API, you must login and create an application.

1. Select **Create an account**. 
![API Products](images/31-create-account.png)

2. Fill in the required fields and select **Create new account** at the bottom of the page. 
**Note:** Use a different email address than the one used to create your developer portal in the previous tutorial.
![API Products](images/32-create-new-account.png)

3. Once the developer account is created, log in to view the home page. You must have an app to subscribe to the APIs. Select **Apps** to go to the registered apps page.  
  ![API Products](images/33-login.png)

4. To register a new application, select **Create new App**.  
  ![Register new app](images/34-create-new-app.png)

5. Enter a *Title* and *Description* for your app and select **Submit**.  
  ![Submit new app](images/35-submit-new-app.png) 

6. Now that you have an App, you can subscribe to API Product plans. Select **available APIs** or **API Products** to browse the API Product plans.  
  ![API Details](images/36-api-products.png) 

7. Select the **API Product** you wish to subscribe to.  
  ![API Product](images/37-select-product.png) 

8. Select **Subscribe** to subscribe to the API Product Plan.  
  ![API Product Plan](images/38-subscribe-plan.png) 

9. Select the **app** you wish to subscribe to the product plan, then select **Subscribe**. 
  ![App Subscribe plan](images/39-subscribe-app-plan.png) 

10. Your application has successfully subscribed to the product plan. 
  ![App Subscribe Success](images/310-subscribe-success.png) 

## Conclusion
In this tutorial, you learned how to explore products and APIs, view and test APIs, and subscribe to APIs. 





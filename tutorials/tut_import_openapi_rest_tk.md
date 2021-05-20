---

copyright:
  years: 2017, 2021, 2021
lastupdated: "2020-12-21"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial, API Connect V5

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Import your API spec and proxy an existing REST service by using the Developer Toolkit
{: #tut_import_openapi_rest_tk}

Duration: 5 mins  
Skill level: Beginner  


## Objective
{: #object_tut_import_openapi_rest_tk}

This tutorial illustrates how you can bring your existing API under management control with {{site.data.keyword.apiconnect_full}} V5. In this tutorial, you will import an OpenAPI spec, and create a passthrough API proxy for an existing REST service.

## Prerequisites
{: #prereq_tut_import_openapi_rest_tk}

Before you begin, you will need to [set up your API Connect Instance](/docs/apiconnect?topic=apiconnect-tut_prereq_set_up_apic_instance) and [install the API Connect toolkit](/docs/apiconnect?topic=apiconnect-tut_prereq_install_toolkit).

---


## Explore the sample app and test the target endpoints
{: #explore_tut_import_openapi_rest_tk}

A sample _weather provider_ app has been created for this tutorial. The corresponding API specification (OpenAPI 2.0) is in the [weather-provider-api_1.yaml](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){: external} file.

1. To explore the app, go to [http://gettingstartedweatherapp.mybluemix.net/](http://gettingstartedweatherapp.mybluemix.net/){: external}.  
2. Enter a valid 5-digit U.S. zipcode to get the _**current weather**_ and _**today's forecast**_.  
![](images/explore-weatherapp-1.png)S

3. The above sample weather app was built using APIs that provide the weather data. The endpoint to get the **current** weather data is `https:// myweatherprovider.mybluemix.net/current?zipcode={zipcode}`. Test it out by visiting [https://myweatherprovider.mybluemix.net/current?zipcode=90210](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: external}.  

  ![](images/explore-weatherapp-2.png)

4. Similarly, the Endpoint to get **today's** forecast data is `https:// myweatherprovider.mybluemix.net/today?zipcode={zipcode}`. Test it out by going to [https://myweatherprovider.mybluemix.net/today?zipcode=90210](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: external}.  

  ![](images/explore-weatherapp-3.png)

---

## Import the sample app's OpenAPI spec to create a REST API proxy
{: #import_tut_import_openapi_rest_tk}

1. Launch the **API Designer**. In your terminal window, enter the following command: `apic edit`.
2. Log in using your IBMid.
    ![](images/screenshot_apic-edit_login.png)
3. In the **API Designer**, ensure that the navigation panel is open. If not, click >> to open it.
4. In the navigation panel, click **Drafts**.
5. Go to the **APIs** tab.
6. In the APIs tab, click **Add**.
7. From the drop-down menu, click **Import API from a file or URL**.
   ![](images/toolkit-import-1.png)
8. There is an OpenAPI 2.0 definition of the weather API that you will use for this tutorial. In the "Import OpenAPI (Swagger)" dialog box, enter this URL:
`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`.
9. Leave the _Add a product_ option unchecked and click **Import**.  
    ![](images/screenshot_import-url.png)  

After you import the OpenAPI spec, you are taken to the Design view of the API. Here you can view various sections of the OpenAPI definition. Scroll to explore, and especially note the Host value. Also you can view the OpenAPI under the Source tab. 
_You'll see that the Host value is set to _ `$(catalog.host)` _. This is the base URL for your API proxy._


## Conclusion
{: #conclusion_tut_import_openapi_rest_tk}

In this tutorial, you saw how an existing REST service can be invoked through an API passthrough proxy. You started by checking the availability of the sample service through the web browser. Then you created an API proxy in {{site.data.keyword.apiconnect_short}}, and linked the proxy to the sample service to be invoked. Finally, you tested this service with the {{site.data.keyword.apiconnect_short}} internal testing tools.

---

## Next step
{: #next_tut_import_openapi_rest_tk}

Secure your API using [rate limiting](/docs/apiconnect/tutorials?topic=apiconnect-tut_rate_limit), [client ID and secret](/docs/apiconnect/tutorials?topic=apiconnect-tut_secure_landing), or [securing using OAuth 2.0](/docs/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Create > **Manage** > Secure > Socialize > Analyze

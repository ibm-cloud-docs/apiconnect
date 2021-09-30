---

copyright:
   years: 2017, 2021
lastupdated: "2020-12-21"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial, API Connect V5

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Add a new API spec and invoke an existing REST service using the Developer Toolkit
{: #tut_add_openapi_rest_tk}

**Duration**: 15 mins  
**Skill level**: Beginner  

## Objective
{: #object_tut_add_openapi_rest_tk}

This tutorial helps you get started quickly with {{site.data.keyword.apiconnect_full}} V5 by illustrating how you can bring your existing API under management control. You'll start by creating a new OpenAPI spec, and then create a pass-through API proxy for an existing REST service.

## Prerequisite
{: #prereq_tut_add_openapi_rest_tk}

Before you begin, you need to [set up your API Connect Instance](/docs/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance) and [install the API Connect toolkit](/docs/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit).

---


## Explore the sample app and test the target endpoints
{: #expl_test_tut_add_openapi_rest_tk}

A sample _weather provider_ app was created for this tutorial.
1. To explore the app, go to [http://gettingstartedweatherapp.mybluemix.net/](http://gettingstartedweatherapp.mybluemix.net/){: external}.  
2. Enter a valid 5-digit US zip code to get the _**current weather**_ and _**today's forecast**_.  
![](images/explore-weatherapp-1.png)

3. The sample weather app was built with APIs that provide the weather data. The endpoint to get the **current** weather data is _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_. Test it out by visiting [https://myweatherprovider.mybluemix.net/current?zipcode=90210](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: external}.  

    ![](images/explore-weatherapp-2.png)

4. Similarly, the endpoint to get **today's** forecast data is `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`. Test it out by going to [https://myweatherprovider.mybluemix.net/today?zipcode=90210](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: external}.  

    ![](images/explore-weatherapp-3.png)

---

## Add a new OpenAPI spec and invoke an existing REST service
{: #add_spec_tut_add_openapi_rest_tk}

1. Launch the **API Designer**. In your terminal, enter `apic edit`.
2. Log in using your IBMid.
    ![](images/screenshot_apic-edit_login.png)
3.  In the API Designer, ensure that the navigation panel is open. If not, click >> to open it. In the **API Designer** navigation panel, select **Drafts > APIs**.
4. In the **APIs** panel, select **Add > New API**.
5. In the New API window, enter "Weather Provider API" for the title. _The Name and Base Path are auto-populated_.  
    ![](images/toolkit-add-new-api.png)   
6. Click **Create API** to complete the wizard.  

7. After your API is created, the **Design** tab is selected.

8. Scroll to the **Host** panel. Enter `$(catalog.host)` as the value if the field is not automatically completed.

9. Scroll to the **Security** tab and delete the "clientIDHeader (API Key)" that was auto-generated.  
_(We'll visit security with API Keys in the next tutorial.)_  

10. In the **Paths** panel, create a path by clicking **+**.
    a. Name the new path "**/current**".  
    b. In the same **Paths** panel, select the **GET /current** section.  
    c. In the **GET /current** section, add a **Parameter**. As you noticed while exploring the sample app, the weather service requires zipcode as a parameter.
      - Name: `zipcode`  
      - Located in: Query  
      - Required: Yes  
      - Type: string  
    ![](images/path-current-1.png)
  d. Save your API.

11. With your query parameters defined in the previous step, you are ready to define the response object, which is returned when you invoke the weather API. Scroll to the **Definitions** panel.

    1. Add a new definition. 
    2. Name the new definition _Current_.
    3. Set the Type of _Object_.
    4. Add new properties for the **Current** definition as shown in Table 1.
	   |    Name    |   Type   |
	   | ---------- | -------- |
	   |zip         |string    |
	   |temperature |integer   |
	   |humidity    |integer   |
	   |city        |string    |
	   |state       |string    |
	   {: caption="Table 1. Properties for the Current definition" caption-side="top"}

    ![](images/definition-current-1.png)

    5. Save your API.  

12. In the previous step, you defined the response object. Next you'll need to ensure the response object is associated with the **get /current** path. In the navigation, scroll back up to the **Paths** panel.
    a. Open the **GET /current** operation, and scroll to the **Responses** section.
    b. Change the schema of the 200OK response from "object" to "**Current**".
    c. Save your API.

13. The GET /current path and operation get the current weather data. Now you'll need to create a similar path and operation to get today's weather data. Similar to how you created the **/current** path in step 11, create a new path: **/today**. 

14. Add a Parameter to the **GET /today** operation.
    - Parameter Name: `zipcode`  
    - Located in: Query  
    - Required: Yes  
    - Type: string  

15. Create a new definition: **Today**.

16. Add new properties for the **Today** definition as shown in Table 2.

	   |    Name      |   Type   |
	   | ------------ | -------- |
	   |zip           |string    |
	   |hi            |integer   |
	   |lowe          |integer   |
	   |nighthumidity |integer   |
   	   |dayhumidity   |integer   |
	   |city          |string    |
	   |state         |string    |
	   {: caption="Table 2. Properties for the Today definition" caption-side="top"}

17. Update the response schema in the **GET /today** section to "Today".

18. Save your API.

19. Click the **Assemble** tab. You created two operations so far: **GET /current** and **GET /today**. To ensure that the correct target endpoint is invoked, create some logic that executes a conditional on the operation that's being called. Let's use the **Operation Switch** logic construct to do this.  

    a. If the _canvas_ displays a default **invoke** policy, delete the policy now.  
    b. From the _palette_, drag the **Operation Switch** and drop it on the canvas.  
      - To **case 0**, assign the **get /current** operation.
      - Add a new Case: **case 1**.
      - Assign the **get /today** operation to **case 1**.
    ![](images/assemble-1.png)
    The **Operation Switch** provides a decision point. Based on the verb and path pair, the appropriate operation must be invoked.  
    c. Drag the **invoke** policy from the palette and drop it on the canvas. Drop one in the **/get current** path and one in the **/get today** path.
    d. Select the **invoke** policy in the **/get current** path, and update its title to "**invoke-current**".  
    e. Update the URL field with: `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`.
    f. Select the **invoke** policy in the **/get today** path, and update its title to "**invoke-today**".  
    g. Update the URL field with: `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`.  

20. Save your API.

---

## Test your API proxy
{: #test_explore_tut_add_openapi_rest_tk}

1. To test your API proxy endpoints, select _Explore_.
2. Select the **GET /current** operation from the palette.
3. Enter a valid US zip code (for example, 90210) in the test box.
4. Click **Call operation** to see the response.  
    ![](images/screenshot_explore.png)  
  
---

## Conclusion
{: #conclusion_tut_add_openapi_rest_tk}

In this tutorial, you saw how an existing REST service can be invoked through an API pass-through proxy. You started by checking the availability of the sample service through the web browser. Then, you created a new OpenAPI spec in {{site.data.keyword.apiconnect_short}}, and linked it to the sample service to be invoked. Finally, you tested the API proxy with the built-in testing tool.

---

## Next step
{: #next_tut_add_openapi_rest_tk}

Secure your API using [rate limiting](/docs/apiconnect/tutorials?topic=apiconnect-tut_rate_limit), [client ID and secret](/docs/apiconnect/tutorials?topic=apiconnect-tut_secure_landing), or [securing using OAuth 2.0](/docs/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2).

Create > **Manage** > Secure > Socialize > Analyze

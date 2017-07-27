---
copyright:
  years: 2017
lastupdated: "2017-07-13"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Add a new API spec and invoke an existing REST service using the Developer Toolkit
**Duration**: 15 mins  
**Skill level**: Beginner  


## Objective
This tutorial helps you get started quickly with **API Connect**. Start by creating a new OpenAPI spec, and then proxy existing REST services used by the sample weather app.

---


## Explore the sample app and test the target endpoints
A sample _weather provider_ app was created for this tutorial.
1. To explore the app, go to http://gettingstartedweatherapp.mybluemix.net/.  
2. Enter a valid 5-digit US zip code to get the _**current weather**_ and _**today's forecast**_.  
![](images/explore-weatherapp-1.png)

  - The sample weather app was developed using APIs that provide the weather data. The endpoint to get the **current** weather data is _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}**_.
  - Test it out by going to https://myweatherprovider.mybluemix.net/current?zipcode=90210.  
  ![](images/explore-weatherapp-2.png)

  - Similary, the Endpoint to get the forecast data for **today** is _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_.
  - Test it out by going to https://myweatherprovider.mybluemix.net/today?zipcode=90210.  
  ![](images/explore-weatherapp-3.png)

---

## Add a new OpenAPI spec and invoke an existing REST service
1. Launch the **API Designer**. In your terminal, enter `apic edit`.
2. Log in using your IBMid.
    ![](images/screenshot_apic-edit_login.png)
3. In the **API Designer** navigation panel, select **Drafts > APIs**.
4. In the **APIs** panel, select **Add > New API**.
5. In the New API window, enter "Weather Provider API" for the title. _The Name and Base Path are auto-populated_.  
6. Select **Create API** to complete the wizard.  

7. After your API is created, the **Design** tab is selected.
    - Scroll down to the **Host** panel, and note the value that's filled in: ```$(catalog.host)```.  
    - In the **Base Path** panel, note the auto-populated value: ```/weather-provider-api```.  
    - Your API's target URL will be created from these values.  

8. Scroll to the **Security** tab and delete the "clientIDHeader (API Key)" that has been been auto-generated.  
_(We'll visit security with API Keys in the next tutorial.)_  

9. In the **Paths** panel, create a new path.
  - Name it "**/current**".  
  - In the same **Paths** panel, select the **GET /current** section.  
  - Add a new Parameter.  
      - Name: zipcode
      - Located in: Query
      - Required: Yes (check mark)
      - Type: string
    ![](images/path-current-1.png)
      - Save your API.

10. In the **Definitions** panel, add a new definition.
    - Name: Current  /  Type: Object
    - Add new properties for the **Current** definition.
      - Name: zip         /  Type: string
      - Name: temperature /  Type: integer
      - Name: humidity    /  Type: integer
      - Name: city        /  Type: string
      - Name: state       /  Type: string
      ![](images/definition-current-1.png)

11. Save your API.  

12. Scroll back up to the **Paths** panel.
    1. Open the **GET /current** operation, and scroll to the **Responses** section.
    2. Change the schema of the 200OK response from "object" to "**Current**".
    3. Save your API.
The path and operation you created was to get the current weather data. Next, you'll need to create the same to get today's weather data.  

13. Create a new path: **/today**.

14. Add a new Parameter under the **GET /today** operation.
    - Parameter Name: zipcode
    - Located in: Query
    - Required: Yes (check mark)
    - Type: string  

15. Create a new definition: **Today**.
    1. Add new properties for the **Today** definition.
        - Name: zip / Type: string
        - Name: hi / Type: integer
        - Name: lo / Type: integer
        - Name: nightHumidity / Type: integer
        - Name: dayHumidity / Type: integer
        - Name: city / Type: string
        - Name: state / Type: string
    2. Update the response schema in the **GET /today** section to "Today".
    3. Save your API.

14. Select the **Assemble** tab. You created two operations so far: **GET /current** and **GET /today**. To ensure the right target endpoint is invoked, you'll need to create some logic that will execute conditional on the operation that's being called. Let's use the **Operation Switch** logic construct to do this.  
    a. Delete the **invoke** policy that may already be added to the _canvas_.  
    b. From the _palette_, drag the **Operation Switch** and drop it on the canvas.  
        1. To **case 0**, assign the **get /current** operation.
        2. Add a new Case: **case 1**.
        3. Assign the **get /today** operation to **case 1**.
    ![](images/assemble-1.png)
    The **Operation Switch** provides a decision point. Based on the verb/path pair, the appropriate operation must be invoked.  
    c. Drag the **invoke** policy from the palette and drop it on the canvas. Drop one in the **/get current** path and one in the **/get today** path.
    d. Select the **invoke** policy in the **/get current** path, and update its title to "**invoke-current**".  
    e. Update the URL field with: _**https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode=$(request.parameters.zipcode)**_.
    f. Select the **invoke** policy in the **/get today** path, and update its title to "**invoke-today**".  
    g. Update the URL field with: _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode=$(request.parameters.zipcode)**_.  
    h. Save your API.

---

## Test your API proxy

### Test with the _API Manager test tool_.
1. In the **Assemble** tab, start the local test server by selecting the **Start servers** icon.
    ![](images/screenshot_start-server-1.png)

2. Click the play icon (►) to test your API proxy's target invocation.
    ![](images/screenshot_test-0.png)

3. In the test panel, select the **get /current** operation.  
  - Zipcode is a required parameter for this operation, so enter a valid U.S. zip code (for example, 90210).  
  - Select **invoke**, and verify that you see the following:
  ```
  200 OK response
  Current weather data for 90210  
  ```
    ![](images/screenshot_test-2.png)  

### Test with the _Explore tool_.  
1. To test your API proxy endpoints, select _Explore_.
2. Select the **GET /current** operation from the palette.
3. Enter a valid U.S. zip code (e.g. 90210) in the test box.
4. Select **Call operation** to see the response.  
  ![](images/screenshot_explore.png)  
  
---

## Conclusion

In this tutorial, you saw how an existing REST service can be accessed by building an API. You started by checking the availability of the sample service through the web browser. Then you created an API in API Connect, and built the connections in the API Design editor. Finally, you tested the API with the built-in testing tool.




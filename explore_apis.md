---

copyright:
   years: 2017, 2021
lastupdated: "2017-09-05"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Exploring APIs and Products
{: #explore_prods_apis}

1. To view APIs that have been shared with your {{site.data.keyword.cloud_notm}} org, go to the APIs landing screen and
click **Explore APIs**.

2. Expand the API to view more information about it.

3. To subscribe to an API, click an API product.
The Developer Portal opens and you can subscribe to a Plan to access an
API. 

   **Note**: If the Plan that you select has billing, you must provide a credit card number for your organization. That requires that you have owner privileges.

## Viewing and testing APIs in the Developer Portal
{: #view_test_apis_dev_port}

1. From the Developer Portal home screen, click **API Products**.

2. To see more details, click **APIs** for the Product that contains the
required API, then click the API.

3. More details of the individual operations associated with an API are available under the
**API Operations** heading.

4. To view the example code of an operation:
    - In the API Operations section, click **Paths**, and click the operation that
you want to see the example code for.
    - Click the operation's tab to expand and show its details, including code examples. You can view
the example code for your operation in several languages.

To test an API, complete the following steps.
1. Click **APIs**.
All of the APIs that can be used by application developers are displayed.

2. Click the name of the API that you want to test.

3. Find the operation you want to work with under the `API Operations` heading.

4. Click **Try this operation**.

5. Supply the values for required headers or parameters.

6. If the operation is secured with Basic Authentication, supply the credentials.

7. Click **Send Request**.
The result is displayed in the Response Body field. You can continue to test different
parameter values as necessary.

## Subscribing to use APIs
{: #subscrib_apis}

1. In the Developer Portal, click **API Products**.

2. Click the Product that contains the Plan that you want to work with.

3. In the Plan section of the Product, click the Plan that you want to use. The details of the
selected Plan are displayed.

4. After you have identified the plan that you want to use, click **Use this
plan**.
The Use this Plan dialog box is displayed.

5. Select the application that you want to use with this Plan, and click
**Save**.
The application details are displayed.

   **Note**: If the Plan that you select has billing, you must provide a credit card number for your organization. That requires that you have owner privileges.

6. To view the operations for the APIs that are included in the Plans to which the application is
subscribed, click the name of the API.

7. If the Plan is not restricted, you can use it immediately. If the Plan is restricted, the Plan
is shown as `Pending Approval`, and you cannot use the requested Plan until the administrator
approves your request.

---

copyright:
  years:  2019
lastupdated: "2019-12-31"

keywords: IBM Cloud, API Connect, authentication, IAM, access management, API Management, API key, token service, API Manager

subcollection: apiconnect

---

{:external: target="_blank" .external} 
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:download: .download}

# Calling APIs provided by {{site.data.keyword.apiconnect_short}}
{: #call_apim_apis}

The REST APIs provided by {{site.data.keyword.apiconnect_short}} must be accessed with token-based authentication. To generate the token, obtain an {{site.data.keyword.cloud_notm}} API key and use it to call the {{site.data.keyword.apiconnect_short}} token service. After you get a token, you can use it in the header when you invoke {{site.data.keyword.apiconnect_short}} APIs.

If you previously called these APIs with Basic authentication, you must update your code to use Token authentication instead. On 15 August, 2018, {{site.data.keyword.apiconnect_short}} discontinued the use of Basic authentication and began requiring the use of Token authentication to ensure that your API calls are secure. For more information, see [Changes to Authentication for API Connect on Cloud](https://developer.ibm.com/apiconnect/2018/08/07/changes-authentication-api-connect-management-apis-public-cloud-regions/){: external}.

This requirement applies only to the APIs that are provided by {{site.data.keyword.apiconnect_short}}. You do not need the token for calling APIs that you imported or created. The token is intended for use with the IBM ID and might not work with other user registries. 
{: note}


## Obtaining an {{site.data.keyword.cloud_notm}} API key
{: #obtain_apikey-call_apim_apis}

To obtain an {{site.data.keyword.cloud_notm}} API Key, complete the following steps.

1. Visit [ {{site.data.keyword.cloud_notm}} API Keys](https://cloud.ibm.com/iam/apikeys){: external}.

2. Click **Create an {{site.data.keyword.cloud_notm}} API key**.

3. In the "Create API key" dialog box, provide a name and description for the key, and then click **Create**.

4. **Important** In the "API key successfully created" message box, click **Download** to save a copy of the key as a file called `apikey.json`. 

   After you close the message box, you cannot access the key. If you lose it or failed to copy it, you must obtain a new key.
 
## Using the API key to invoke APIs
{: #use_apikey-call_apim_apis}

After you obtain an {{site.data.keyword.cloud_notm}} API key, use that key to generate a token that you can use to invoke the APIs provided by {{site.data.keyword.apiconnect_short}}.
 
### Using the API key to generate a token
{: #get_token-call_apim_apis}

Call the {{site.data.keyword.apiconnect_short}} token service with your {{site.data.keyword.cloud_notm}} API key.

Format the request as shown in the following example.

`POST https://login.service.<region>.apiconnect.ibmcloud.com/apikey?apikey=<api_key>`

The API responds with a JSON payload. Use the value of the `jwt` property as your token.
  
### Invoking APIs with the token
{: #invoke_api-call_apim_apis}

When you invoke an API provided by {{site.data.keyword.apiconnect_short}}, use the token as the authorization header; for example:

`curl https://us.apiconnect.ibmcloud.com/v1/me -H ‘Authorization: Bearer <token>’`

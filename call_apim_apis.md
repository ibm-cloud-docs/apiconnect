---

copyright:
  years: 2019, 2021
lastupdated: "2021-03-15"

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

# Calling APIs provided by {{site.data.keyword.apiconnect_short}} V5
{: #call_apim_apis}

The REST APIs provided by {{site.data.keyword.apiconnect_short}} must be accessed with token-based authentication. To generate the token, obtain an {{site.data.keyword.cloud_notm}} API key and use it to call the {{site.data.keyword.apiconnect_short}} token service. After you get a token, you can use it in the header when you invoke {{site.data.keyword.apiconnect_short}} APIs.

This requirement applies only to the APIs that are provided by {{site.data.keyword.apiconnect_short}}. You do not need the token for calling APIs that you imported or created. The token is intended for use with the IBM ID and might not work with other user registries. 

This topic applies only to {{site.data.keyword.apiconnect_short}} V5. For information on calling {{site.data.keyword.apiconnect_short}} APIs in the V10 Reserved edition, see [Calling APIs provided by V10 Reserved](/docs/apiconnect?topic=apiconnect-ri-call-apim-apis).
{: note}


## Obtaining an {{site.data.keyword.cloud_notm}} API key
{: #obtain-apikey_call_apim_apis}

To obtain an {{site.data.keyword.cloud_notm}} API Key, complete the following steps.

1. Visit [{{site.data.keyword.cloud_notm}} API Keys](https://cloud.ibm.com/iam/apikeys){: external}.

2. Click **Create an {{site.data.keyword.cloud_notm}} API key**.

3. In the "Create API key" dialog box, provide a name and description for the key, and then click **Create**.

4. **Important** In the "API key successfully created" message box, click **Download** to save a copy of the key as a file called `apikey.json`. 

   After you close the message box, you cannot access the key. If you lose it or failed to copy it, you must obtain a new key.
 
## Using the API key to invoke APIs
{: #use-apikey_call_apim_apis}

After you obtain an {{site.data.keyword.cloud_notm}} API key, use that key to generate a token that you can use to invoke the APIs provided by {{site.data.keyword.apiconnect_short}}.
 
### Using the API key to generate a token
{: #get-token_call_apim_apis}

Call the {{site.data.keyword.apiconnect_short}} token service with your {{site.data.keyword.cloud_notm}} API key.

Format the request as shown in the following example.

`POST https://login.service.<region>.apiconnect.ibmcloud.com/apikey?apikey=<api_key>`

The API responds with a JSON payload. Use the value of the `jwt` property as your token.
  
### Invoking APIs with the token
{: #invoke_api_call_apim_apis}

When you invoke an API provided by {{site.data.keyword.apiconnect_short}}, use the token as the authorization header; for example:

`curl https://apimanager.us-south.apiconnect.cloud.ibm.com/v1/me -H ‘Authorization: Bearer ’`

## API key best practices
{: #apikey-practices_call-apic-apis}

API keys are used as the method of authentication to your service, so they must be kept secure. The following best practices help you maintain a secure API key and reduce the chance of publicly exposing credentials that compromise your application.

- Use an API key with the role that is appropriate for the function that you are using.
  When you create an application, consider using an API key with the role Reader for all calls to GET API methods. The Reader role can't perform any destructive or additive functions to the service instance.

- Do not embed the API key directly in code.
  API keys that are embedded in code might be exposed to your users. Instead of embedding the API keys in your application code, consider storing them either in environment variables or in files outside of your source code control system.

- Do not store an API key in files inside your application's source code control system.
  If you store API keys in files, keep the files outside of your application's source code. This practice is important if you use a public source-code management system such as GitHub.

- Regenerate your API keys periodically.
  You can create new credentials at any time.

  1. From the resource list, select a service instance.
  2. In the navigation list, click **Service credentials**.

  When you migrate your application to the new credentials, don't forget to delete the old credentials by using the trashcan icon for the credentials that you want to delete.
  {: tip}

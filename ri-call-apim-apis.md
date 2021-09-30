---

copyright:
   years: 2021
lastupdated: "2021-03-15"

keywords: IBM Cloud, API Connect, Reserved, authentication, IAM, access management, API key, token service, CLI

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

# Calling APIs provided by V10 Reserved
{: #ri-call-apim-apis}

The REST APIs provided by {{site.data.keyword.apiconnect_short}} V10 Reserved require authentication for use. To call an API interactively, you can log into the toolkit CLI with an option to generate the API key. To call an API programmatically, you can generate an API key and then exchange it for an IBM Cloud IAM Bearer token. 
{: shortdesc}

This requirement applies only to the APIs that are provided by {{site.data.keyword.apiconnect_short}}. You do not need the API key for calling APIs that you imported or created. The API key is intended for use with the IBM ID and might not work with other user registries. 

This topic applies only to the V10 Reserved edition of {{site.data.keyword.apiconnect_short}}. For information on calling {{site.data.keyword.apiconnect_short}} APIs in V5, see [Calling APIs provided by API Connect V5](/docs/apiconnect?topic=apiconnect-call_apim_apis).
{: note}


## Calling an {{site.data.keyword.apiconnect_short}} API interactively in V10 Reserved
{: #cli_ri-call-apim-apis}

To call APIs interactively in the V10 Reserved CLI, log in to the {{site.data.keyword.apiconnect_short}} toolkit with the following command:

```
apic login --server {mgmt_endpoint_url} --sso
```

Follow the displayed instructions to generate an IBM Cloud API key, copy it from the IBM API Connect Reserved passcode page, and submit the API key on the command line to complete the login. The authentication lasts for the duration of your CLI session. You do not need to provide the API key with API calls during the session.

For more information on logging in to the toolkit, see [Setting up the toolkit for V10 Reserved](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.toolkit.doc/ri_toolkit.html#ri_tk_login) in the extended V10 Reserved documentation.


## Calling an {{site.data.keyword.apiconnect_short}} API programmatically in V10 Reserved
{: #program_ri-call-apim-apis}

To call an API programmatically, generate an API key and then use it to generate an IBM Cloud IAM access token. You can use the generated token for authentication in your API calls.

### Obtain an {{site.data.keyword.cloud_notm}} API key
{: #apikey_ri-call-apim-apis}

To obtain an {{site.data.keyword.cloud_notm}} API Key, complete the following steps.

1. Visit [{{site.data.keyword.cloud_notm}} API Keys](https://cloud.ibm.com/iam/apikeys){: external}.

2. Click **Create an {{site.data.keyword.cloud_notm}} API key**.

3. In the "Create API key" dialog box, provide a name and description for the key, and then click **Create**.

4. **Important** In the "API key successfully created" message box, click **Download** to save a copy of the key as a file called `apikey.json`. 

The API key does not expire; however, after you close the message box, you cannot access the key. If you lose the key or failed to copy it, you must obtain a new API key.
 
#### API key best practices
{: #apikey-practices_ri-call-apim-apis}

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

   When you migrate your application to the new credentials, don't forget to delete the old credentials.

### Exchange the API key for an IBM Cloud IAM access token
{: #iam-token_ri-call-apim-apis}

To exchange your API key for an IAM access token, use the following command:

```
curl -X POST \
   "https://iam.cloud.ibm.com/identity/token" \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Accept: application/json' \
   --data-urlencode 'grant_type=urn:ibm:params:oauth:grant-type:apikey' \
   --data-urlencode 'apikey={api_key}'
```
  
where `{api_key}` is the value of your API key. The response looks like the following example:

```
{"access_token":"[_access-token-value_]","refresh_token":"not_supported","token_type":"Bearer","expires_in":3600,"expiration":1615370557,"scope":"ibm openid"}
```

Now you can use the IAM access token in your API calls; for example:

```
curl https://{api_host}/api/orgs \
   -H "Accept: application/json" \
   -H "Content-Type: application/json" \
   -H "Authorization: Bearer _access-token-value_"

{
  "total_results": 2,
  "results": [
    {
      "type": "org",
      "org_type": "provider",
    ...
    }
  ]
}
```

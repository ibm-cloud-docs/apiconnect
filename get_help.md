---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-06"

keywords: IBM Cloud, API Connect, API management, support, help

subcollection: apiconnect

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Getting help
{: #get_help}

Need help with your {{site.data.keyword.appconservicefull}} service instance? Visit the {{site.data.keyword.cloud_notm}} [Support Center](https://cloud.ibm.com/unifiedsupport/supportcenter) to file a case. 
{: shortdesc}

1. On the Support Center page, look in the "Contact support" section and click **Create a case**. 

2. On the Create a Case page, look in the "Services" list and click {{site.data.keyword.apiconnect_short}}.

   It's important to create your case with the correct service so that IBM Support can track the case and assign the appropriate people to help you. The list of services depends on your {{site.data.keyword.cloud_notm}} account. If you don't see {{site.data.keyword.apiconnect_short}} in the "Services" list, you can locate it as follows:
   
   a. Locate the "What do you need help with?" section.
   b. Review the text in that section and click the **view all services** link.
   c. In the complete list of services, locate {{site.data.keyword.apiconnect_short}} and click it (services are listed in alphabetic order).

3. Describe your problem.

   Use the fields on the "Create a Case" page to explain your problem. The following list describes important information that will assist us with resolving issues that you are having in {{site.data.keyword.apiconnect_short}}:

   - For all issues, include the following information:

      - Region and customer service instance impacted
      - Component impacted: API Manager, API calls, Portal
      - URL where error is being seen
	  - For Dedicated, identify the customer environment
	  - For Reserved Instance, use a prefix in the Subject field to indicate the version and p-org. For more information, see [Getting help](https://www.ibm.com/support/knowledgecenter/SSMNED_cloud/com.ibm.apic.overview.doc/rapic_ibm_support_ri.html){: external} in the Reserved Instance documentation

   - For API Manager UI-based issues, additionally include:

      - All error codes returned
      - Time (including time zone) that the problem occurred

   - For Portal-based issues, additionally include the user name of person who encountered the problem

   - For issues invoking APIs, additionally include:

      - Full API URL impacted - the host name should contain apiconnect.ibmcloud.com
      - HTTP method used
      - Frequency and time (with timezone) of the issue
      - Expected result
      - Actual (incorrect) result
      - Evidence from analytics to show that the API issue is not a problem with the customer's down-stream system; for more information, see the _IBM Developer_ article [Why isn’t my API working](https://developer.ibm.com/apiconnect/why-isnt-my-api-working/){: external}
      - Complete cURL example for recreating the call (include all Information required for the call, including headers, client ID/secret)

   Optionally attach files to help explain your issue (for example, screen captures). Click the Information icon next to "Supported file types" to see the complete list of allowed file types. Helpful attachments include:
   
   - A (compressed) CSV file containing exported analytics for failing APIs, to ensure we see the correct calls and the failure patterns
   - A copy of the API YAML file, with personal data such as IDs, secrets, tokens, and passwords removed
   - A copy of a browser HAR trace file, if the problem is related to the behavior of the API Connect UI
    
4. Click **Create** to submit your new case.

To view a case's status, look in the "Recent cases" section of the Support Center page. If you don't see the case you're looking for, click **View all open cases**.

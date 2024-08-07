---

copyright:
  years: 2019, 2024
lastupdated: "2024-07-02"

keywords: IBM Cloud, API Connect, API management, support, help, Support Center

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Using the Support Center
{: #get_help}

Need help with your {{site.data.keyword.apiconnect_short}} service instance? Visit the {{site.data.keyword.cloud_notm}} [Support Center](https://cloud.ibm.com/unifiedsupport/supportcenter) to file a case.
{: shortdesc}

1. On the Support Center page, look in the "Contact support" section and click **Create a case**.

2. On the Create a Case page, look in the "Services" list and click {{site.data.keyword.apiconnect_short}}.

   It's important to create your case with the correct service so that IBM Support can track the case and assign the appropriate people to help you. The list of services depends on your {{site.data.keyword.cloud_notm}} account. If you don't see {{site.data.keyword.apiconnect_short}} in the "Services" list, you can locate it as follows:

   - Locate the **What do you need help with?** section.
   - Review the text in that section and click the **view all services** link.
   - In the complete list of services, locate {{site.data.keyword.apiconnect_short}} and click it (services are listed in alphabetic order).

3. Describe your problem.

   Use the fields on the **Create a Case** page to explain your problem. The following list describes important information that assists us with resolving issues that you are having in {{site.data.keyword.apiconnect_short}}.

   Important: Do not include your private key in the support request.

   - For all issues, include the following information:

      - Region and customer service instance impacted
      - Component impacted: API Manager, API calls, Portal
      - URL where error is being seen

   - For Dedicated, identify the customer environment
      - Use a prefix in the Subject field to indicate the version and provider-org; for example: "[v10 providerOrg]"

   - For API Manager UI-based issues, additionally include:

      - All error codes returned
      - Time (including time zone) that the problem occurred

   - For Portal-based issues, additionally include the user name of person who encountered the problem

   - For issues with invoking APIs, additionally include:

      - Full API URL impacted - the host name should contain `apiconnect.ibmcloud.com`
      - HTTP method used
      - Frequency and time (with time zone) of the issue
      - Expected result
      - Actual (incorrect) result
      - Evidence from analytics to show that the API issue is not a problem with the customer's down-stream system. For more information, see the IBM Integration Community article [Why isn’t my API working](https://community.ibm.com/community/user/middleware/blogs/ricky-moorhouse1/2018/09/27/why-isnt-my-api-working){: external}
      - Complete cURL example for recreating the call (include all information required for the call, including headers, client ID, and client secret)

   Optionally attach files to help explain your issue (for example, screen captures). Click the Information icon next to **Supported file types** to see the complete list of allowed file types. Helpful attachments include:

   - A (compressed) CSV file that contains exported analytics for failing APIs, to ensure we see the correct calls and the failure patterns
   - A copy of the API YAML file, with personal data such as IDs, secrets, tokens, and passwords removed
   - A copy of a browser HAR trace file, if the problem is related to the behavior of the API Connect UI

4. Click **Create** to submit your new case.

To view a case's status, look in the "Recent cases" section of the Support Center page. If you don't see the case you're looking for, click **View all open cases**.

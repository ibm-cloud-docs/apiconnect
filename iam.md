---

copyright:
  years:  2020
lastupdated: "2020-10-19"

keywords: IBM Cloud, API Connect, API management, Reserved plan, authentication, IAM, access management, service ID, API key, user roles, user actions

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

# Managing access
{: #iam}

{{site.data.keyword.apiconnect_short}} V10 Reserved uses {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) to securely authenticate users and control access to service instances on the {{site.data.keyword.cloud_notm}} platform.

{{site.data.keyword.apiconnect_short}} V5 does not support IAM roles and actions. You can still use the IAM site to obtain an {{site.data.keyword.cloud_notm}} API key, which is needed for generating a token for use when [Calling APIs provided by {{site.data.keyword.apiconnect_short}}](/docs/apiconnect?topic=apiconnect-call-apic-apis).
{: note}


## Identity and Access Management roles and actions
{: #apic-roles-actions_iam}

Access to Reserved plans for users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). 

Every user in your account that accesses a Reserved plan must be assigned an access policy with an IAM user role defined. The policy determines what actions a user can perform within the context of the Reserved plan. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that can be performed on the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels. Options include the following access levels: 

* Access across all Reserved plans in your account
* Access to an individual Reserved plan in your account
* Access to a Reserved plan contained in a specific resource group

After you define the scope of the access policy, you assign a role. The role determines the user's level of access. The following tables outline what actions each role allows within the {{site.data.keyword.apiconnect_short}} V10 Reserved service.

Table 1 details actions that are mapped to platform management roles, and which {{site.data.keyword.apiconnect_short}} role corresponds to each platform role. Platform management roles enable users to perform tasks on service resources at the platform level; for example: assign user access for the service, create or delete instances, and bind instances to applications.

| IAM Platform role            | Maps to {{site.data.keyword.apiconnect_short}} role | Summary of allowed actions |
| ---------------------------- | ------------------------ | ----------------------------------------------------------------------------------- |
| Viewer                       | Viewer                   | View (but not edit) APIs, members, settings, and organizations. |
| Operator                     | Community Manager        | View data and settings. Edit Products and APIs. Manage Consumer organizations, apps, subscriptions, and analytics. |
| Editor                       | API Administrator        | View data and settings. Edit Products and APIs. Manage Consumer organizations, apps, subscriptions, and analytics. |
| Administrator                | Administrator            | View data and settings. Manage members, settings, and Provider organizations. Edit Products and APIs. Manage Consumer organizations, apps, subscriptions, and analytics. Manage the service instance and plan. Manage users in the cloud account. |
{: caption="Table 1. IAM user roles and actions" caption-side="top"}


Table 2 details actions that are mapped to service access roles, and which {{site.data.keyword.apiconnect_short}} role corresponds to each service role. Service access roles enable users to access {{site.data.keyword.apiconnect_short}} as well as call the {{site.data.keyword.apiconnect_short}} API.

| IAM Service role        | Maps to {{site.data.keyword.apiconnect_short}} role | Summary of allowed actions | 
| ----------------------- | ------------------------ | --------------------------------------------------------------- |
| Reader                  | Viewer                   | View (but not edit) APIs, members, settings, and organizations. |
| Writer                  | Developer                | View data and settings. Edit Products and APIs. Manage apps, subscriptions, and analytics. | 
| Manager                 | API Administrator        | View data and settings. Edit Products and APIs. Manage Consumer organizations, apps, subscriptions, and analytics. | 
{: caption="Table 2. IAM service access roles and actions" caption-side="top"}

For more information about assigning user roles in the IAM service, see [Managing access to resources](/docs/account?topic=iam-iammanidaccser#iammanidaccser).

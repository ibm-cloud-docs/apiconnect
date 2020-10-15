---

copyright:
  years:  2020
lastupdated: "2020-10-15"

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

Table 1 details actions that are mapped to platform management roles. Platform management roles enable users to perform tasks on service resources at the platform level; for example: assign user access for the service, create or delete instances, and bind instances to applications.

| Platform management role | Description of actions | Example actions                                                 |
| ------------------------ |----------------------- | --------------------------------------------------------------- |
| Viewer                   | Can view data within the instance, but cannot edit or alter any data. | View API, View analytics |
| Editor                   | Same abilities as Operators, but can also modify the instance itself (change name, change plan, delete instance, and so on). | Create API, Publish API, Delete API |                    |
| Operator                 | Full control of creating, editing, and publishing APIs | Create API, Publish API, Delete API  |
| Administrator            | Full control of the service | Create API, Publish API, Delete API, Delete instance, Add users to instance  |
{: caption="Table 1. IAM user roles and actions" caption-side="top"}


Table 2 details actions that are mapped to service access roles. Service access roles enable users access to {{site.data.keyword.apiconnect_short}} Developer Experience Trial as well as the ability to call the {{site.data.keyword.apiconnect_short}} Developer Experience Trial API.

| Service access role | Description of actions | Example actions                                                 |
| ------------------- |----------------------- | --------------------------------------------------------------- |
| Reader              | Can view data within the instance, but cannot edit or alter any settings. | View API, View analytics |
| Writer              | Full control of creating, editing, and publishing APIs | Create API, Publish API, Delete API |
| Manager             | Full control over data within the service (such as administering APIs and other resources), but cannot modify the instance itself. | Create OAuth provider, Create resource, Create API, Publish API, Delete API  |
{: caption="Table 2. IAM service access roles and actions" caption-side="top"}

For more information about assigning user roles in the IAM service, see [Managing access to resources](/docs/account?topic=iam-iammanidaccser#iammanidaccser).

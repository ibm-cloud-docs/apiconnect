---

copyright:
  years: 2020
lastupdated: "2020-12-22"

keywords: IBM Cloud, API Connect, V10, Reserved plan, lifecycle, develop, create, manage, API, user, role, access, group

subcollection: apiconnect

---

{:external: target="_blank" .external} 
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}

# Managing users
{: #ri-mng-users} 
 
Create provider organizations to manage {{site.data.keyword.apiconnect_short}}, and map them to IAM access groups to specify user permissions.
{: shortdesc}

In {{site.data.keyword.apiconnect_short}} V10 Reserved, user access is managed with the {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) service. Create a provider organization in {{site.data.keyword.apiconnect_short}}, and then use the IAM service to define access groups that represent the members of your provider organization.

Complete the following steps to grant members of your {{site.data.keyword.cloud_notm}} account the appropriate access to your {{site.data.keyword.apiconnect_short}} Reserved service.


## Creating provider organizations
{: #porg_ri-mng-users}

In {{site.data.keyword.apiconnect_short}} Reserved, users are grouped into _provider organizations_. Each provider organization owns a set of assets including APIs, products, catalogs, and developer portals. You can create a single provider organization (for example, in a small company) or create multiple provider organizations (for example, different departments in a large company). Some users might belong to multiple provider organizations, and might receive different levels of access with each.


### Decide how many provider organizations you need
{: #porg-decide_ri-mng-users}

In {{site.data.keyword.apiconnect_short}} Reserved, all of the members of a provider organization receive the same level of access to {{site.data.keyword.apiconnect_short}}. Review the members of your company's {{site.data.keyword.cloud_notm}} account and the descriptions of [who does what in {{site.data.keyword.apiconnect_short}}](/docs/apiconnect?topic=apiconnect-ri-user-over#whodoeswhat_ri-user-over), and determine how many provider organizations you need to create.

### Create your provider organizations in {{site.data.keyword.apiconnect_short}}
{: #porg-create_ri-mng-users}

Use the {{site.data.keyword.apiconnect_short}} administration console to create a provider organization and map it to the new IAM access group.

1. Open the {{site.data.keyword.apiconnect_short}} Reserved service's administration console.

   a. [Log in](https://cloud.ibm.com/login/){: external} to {{site.data.keyword.cloud_notm}}.
  
   b. On the Dashboard, click ![Menu icon](images/icon_cloud_menu.png "Menu icon") and select **API Management**.

   c. In the navigation list, expand **API Connect** and click **Services**.
  
   d. On the "Services" page, click your Reserved service's name to open its administration console.
	    
2. On the administration console's home page, click the **Provider organizations** tile.

3. On the "Provider organizations" page, click **Create provider organization**.

4. On the "Create provider organization" page, provide a **Title**, select a **Resource group**, and then click **Create**.

   The title is the display name of your provider organization; a lowercase version of the title is automatically generated as the provider organization's name for internal use.
   
Repeat steps 3 and 4 for each additional provider organization. Then, create an IAM access group that will map to each provider organization and define user permissions.


## Creating IAM access groups
{: #access_ri-mng-users}

After you create a provider organization in {{site.data.keyword.apiconnect_short}}, use the {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) service to set permissions for it. You can define IAM access groups with policies that determine permissions within each provider organization in {{site.data.keyword.apiconnect_short}}, and then you can add members of your company's {{site.data.keyword.cloud_notm}} account to the appropriate access groups, which map users to provider organizations. 

### Determine access needs for users
{: #access-needs_ri-mng-users}

For each provider organization, you need to create an IAM access group and assign the appropriate permissions. To decide what type of permissions each access group (provider organization) requires, review Table 1 to see how suggested jobs in {{site.data.keyword.apiconnect_short}} map to access roles in IAM. 

| {{site.data.keyword.apiconnect_short}} job | Needs this IAM role | Allowed actions |
| ----------------- | ------------------------------------------- |
| API Developer     | Service: Writer                    | Create, edit, and publish APIs                              |
| API Administrator	| Service: Manager, Platform: Editor | Create, edit, and publish APIs; Full control over data within the service; Modify the service instance |
| Product Manager	| Platform: Operator                 | Create, edit, and publish APIs |
| Administrator	    | Platform: Administrator            | Full control of the service instance |
{: caption="Table 1. Mapping {{site.data.keyword.apiconnect_short}} jobs to IAM roles" caption-side="top"}

IAM provides roles for both the platform (the service instance itself) and the service (the product features provided in the service instance). {{site.data.keyword.apiconnect_short}} administrators and API administrators perform tasks that use the platform roles; for example, provisioning a service instance and managing user access to it. Other users perform tasks that use the service roles; for example, creating an API or viewing event analytics.

Table 1 suggests IAM roles for typical {{site.data.keyword.apiconnect_short}} jobs. You might want to assign different IAM roles to a job, or to create custom roles. For a complete list of the IAM roles and how they are used in {{site.data.keyword.apiconnect_short}}, see [Managing access](/docs/apiconnect?topic=apiconnect-iam).
{: note}


### Create access groups in IAM
{: #access-create-group_ri-mng-users}

In IAM, an access group contains a set of users that are assigned to the same access roles for the same {{site.data.keyword.cloud_notm}} resource. For your purposes, each access group represents a provider organization and should be assigned to the appropriate access roles for those users.

1. [Log in](https://cloud.ibm.com/login/){: external} to {{site.data.keyword.cloud_notm}}.
  
2. On the {{site.data.keyword.cloud_notm}} Dashboard, locate the "User access" tile and click **Manage users**.

   The IAM service dashboard opens to the [Access (IAM)](https://cloud.ibm.com/iam) page.

3. On the "Access (IAM)" page, look in the navigation menu and click **Access groups**.

4. On the "Access groups" page, click **Create**.

5. In the "Create access group" box, provide a name and description for the new access group, and then click **Create**.

Repeat steps 4 and 5 for each access group. 

### Assign access policies to the access groups
{: #access-assign-policies_ri-mng-users}

An IAM access policy assigns roles (each role represents a set of permissions) to an access group. You can add one or more roles to each access group in IAM, and you can map one or more access groups to each of your {{site.data.keyword.apiconnect_short}} provider organizations. 

1. On the page for your access group, click the **Access policies** tab.
   
2. On the "Access policies" tab, click **Assign access**.
  
3. On the "Assign access" page, select the following options to assign access roles to your provider organization:

   a. Select **IAM services**.

      You are only defining access to {{site.data.keyword.apiconnect_short}}, which is an IAM-enabled service.  

   b. For "What type of access do you want to assign?" select **API Connect** from the list.
   
      Your provider organizations only apply to {{site.data.keyword.apiconnect_short}} Reserved.

   c. For "Which services do you want to assign access to?", select **Services based on attributes**.
   
   d. For "Add attributes" select **Service Instance**, plus:
   
      - In the first list, select **string equals**.  
	  
      - In the "Service Instance" list, select the name of the provider organization where you want to apply the access policy.

      The new access group applies only to the specified provider organization. Mapping the policy directly to a provider organization ensures that you don't accidentally grant users a wider range of permissions to the Reserved service.

   e. Select the roles that you want to assign to the members of this access group. 
  
      Click the number next to each role to see the detailed list of permissions that are available with that role.
	  
   f. Select **Add** to add the selected roles to the access group.
   
   g. Review the access in the "Access summary" section and click **Assign** to save the access groups with the access policies.
   
Next, add users to the access group so that the permissions you just configured can be assigned to them.

### Add users to the access group
{: #access-add-users_ri-mng-users}

Adding users to an access group maps them to the provider organization that is associated with that access group, and determines their permissions in {{site.data.keyword.apiconnect_short}} when they log in with that provider organization.

1. On the page for your access group, click the **Users** tab.

2. On the "Users" tab, click **Add users**.

   The names of all of the users who belong to your company's {{site.data.keyword.cloud_notm}} account display.

3. Select users to be added to the access group.

   You can quickly add all of the users in the list by clicking the checkbox next to **Users** at the beginning of the table.
{: tip}

4. At the beginning of the table, click **Add to group**.


## Notifying users that the provider organization is available
{: #invite-porg_ri-mng-users}

When you set up IAM access for your users, there is no automatic notification. After you finish configuring access for a provider organization, you should notify its members so they can start working with {{site.data.keyword.apiconnect_short}}. For example, you could send an email or post a message where your users will see it. You should tell users the following information:

- The name of the Reserved service (especially if you provisioned more than one)
- The name of the provider organization that the user is assigned to
- Where to find documentation: https://cloud.ibm.com/docs/apiconnect


## Managing provider organizations
{: #mng-porg_ri-mng-users}

Use IAM to add and remove users, and to manage their permissions.

### Assigning ownership of a provider organization
{: #mng-porg-owner_ri-mng-users}

Instead of managing all provider organizations yourself, you can designate other users as owners and give them the appropriate access. To assign owner-level access to a provider organization, create an IAM access group that has administrative access to the provider organization, and add the user to that access group.

### Manage user permissions
{: #mng-porg-user-perms_ri-mng-users}

To change a user's permissions in {{site.data.keyword.apiconnect_short}}, either change the roles assigned to the IAM access group containing that user, or move the user to a different access group.

### Remove users from a provider organization
{: #mng-porg-remove-user_ri-mng-users}

To remove a user from a provider organization, delete that user from the corresponding access role in IAM. The next time that the user attempts to log in to the provider organization, the login will not be allowed.

A user who is already logged in to {{site.data.keyword.apiconnect_short}} when you remove them from the access group remains logged in and still has access to the provider organization's assets. To stop the user from working with assets immediately, remove them from all catalog and space memberships within the Reserved service.
{: note}

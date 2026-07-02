---

copyright:
   years: 2024, 2026
lastupdated: "2026-07-02"

keywords: IBM Cloud, API Connect, V12 Reserved instance, users, provider organizations, access

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Managing users in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #mng-users}

Manage users and provider organizations in your {{site.data.keyword.apiconnect_short}} V12 Reserved instance.
{: shortdesc}

## User roles in V12 Reserved
{: #roles_v12ri-mng-users}

In {{site.data.keyword.apiconnect_short}}, users are grouped into _provider organizations_ and assigned roles that control their access to resources. The key roles are:

- **Administrator** — Has full access to the administration console and all provider organizations. Responsible for provisioning, managing users, and configuring services such as gateways.
- **API Developer** — Creates and manages APIs, products, and related assets within a provider organization.
- **API Administrator** — Manages catalogs and publication within a provider organization.
- **Product Manager** — Manages the lifecycle of products and APIs, including publication decisions.

## Managing provider organizations
{: #porg_v12ri-mng-users}

Provider organizations are the organizational units in {{site.data.keyword.apiconnect_short}}. Each provider organization owns its own APIs, products, catalogs, and developer portals. As an administrator, you create provider organizations and assign users to them.

To create a provider organization:

1. Log in to your V12 Reserved administration console.
2. Navigate to **Provider Organizations**.
3. Click **Add** and enter the organization name and owner details.
4. Click **Create**.

## Adding users to a provider organization
{: #add_users_v12ri-mng-users}

In V12 Reserved, user access is managed through {{site.data.keyword.iamlong}} (IAM). To add a user to a provider organization:

1. In {{site.data.keyword.cloud_notm}}, navigate to **Manage** > **Access (IAM)**.
2. Create an access group with the appropriate API Connect service policies for the provider organization.
3. Invite the user to your {{site.data.keyword.cloud_notm}} account and add them to the access group.

For detailed instructions on configuring IAM access for {{site.data.keyword.apiconnect_short}}, see [Managing access with IAM](/docs/apiconnect?topic=apiconnect-vri-iam).

## Managing user roles within a provider organization
{: #manage_roles_v12ri-mng-users}

Once a user is a member of a provider organization, you can manage their roles from within the API Manager:

1. Log in to the API Manager in your V12 Reserved instance.
2. Navigate to **Members**.
3. Find the user you want to update and click the edit icon.
4. Assign or change the user's role.
5. Click **Save**.

## Transferring ownership of a provider organization
{: #transfer_v12ri-mng-users}

To transfer ownership of a provider organization to another user, contact your {{site.data.keyword.apiconnect_short}} administrator. The new owner must already be a member of the provider organization.

## Extended user management documentation
{: #extended_docs_v12ri-mng-users}

For complete user management documentation including advanced scenarios, see [Managing users](https://www.ibm.com/docs/en/SSCL05_12.1.x){: external} in the complete V12 Reserved documentation.

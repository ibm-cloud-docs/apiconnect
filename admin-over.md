---

copyright:
   years: 2024, 2026
lastupdated: "2026-07-02"

keywords: IBM Cloud, API Connect, V12 Reserved instance, administer, overview
subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Administering your {{site.data.keyword.apiconnect_short}} V12 Reserved instance
{: #admin-over}

Use the administration console to manage users, configure gateways, and administer your {{site.data.keyword.apiconnect_short}} V12 Reserved instance
{: shortdesc}

## Managing users
{: #admin-over}

In {{site.data.keyword.apiconnect_short}}, users are grouped into _provider organizations_. Each provider organization owns a set of assets including APIs, products, catalogs, and developer portals. You can create a single provider organization or multiple provider organizations for different departments or teams.

In {{site.data.keyword.cloud_notm}}, user access is managed with the Identity and Access Management (IAM) service. You can define access groups with policies that determine permissions within each provider organization, and then add members of your company's {{site.data.keyword.cloud_notm}} account to the appropriate access groups.

For more information, see [Managing users in V12 Reserved](/docs/apiconnect?topic=apiconnect-mng-users).

## Adding and managing gateways
{: #gwys_v12ri-admin-over}

{{site.data.keyword.apiconnect_short}} uses gateways to manage API traffic. A gateway hosts published APIs and provides the API endpoints used by client applications. Gateways execute API proxy invocations to back-end systems and enforce API policies that manage client identification, security, and rate limiting.

{{site.data.keyword.apiconnect_short}} V12 Reserved deploys with the IBM DataPower API Gateway by default. You can deploy additional self-managed DataPower gateways and integrate with the webMethods API Gateway (available on demand).

For more information, see [Managing gateways in V12 Reserved](/docs/apiconnect?topic=apiconnect-gateways).

## Using the toolkit
{: #toolkit_v12ri-admin-over}

The toolkit provides a CLI for working with assets such as APIs and developer portals. In V12, TLS verification is enabled by default during the login handshake. Ensure that you have the correct CA certificate or configure TLS flags before using the toolkit.

For information on setting up the toolkit, see [Developing APIs in V12 Reserved](/docs/apiconnect?topic=apiconnect-develop-api).

## Configuring Federated API Management
{: #fed_api_v12ri-admin-over}

V12 Reserved includes Federated API Management, which lets you centrally manage distributed API runtimes and data planes from a single interface. You can connect and monitor runtimes across different regions and platforms.

For more information, see [Federated API Management](/docs/apiconnect?topic=apiconnect-fam-api-mgmt).

## Enhancing security
{: #security_v12ri-admin-over}

Use {{site.data.keyword.iamlong}} to configure fine-grained access control for your V12 Reserved instance. For more information, see [Managing access with IAM](/docs/apiconnect?topic=apiconnect-vri-iam).

## Observability
{: #observability_v12ri-admin-over}

Monitor your V12 Reserved instance using the following tools:

- **Activity Tracker**: Track administrative events in your instance. See [Activity Tracker events](/docs/apiconnect?topic=apiconnect-vri-at_events) for the list of tracked events.
- **Logging**: Monitor operational logs. See [Logging for V12 Reserved](/docs/apiconnect?topic=apiconnect-logs).
- **Analytics offloading**: Route API event analytics to external systems. See [Offloading analytics data](/docs/apiconnect?topic=apiconnect-offload-analytics).

## Reference
{: #reference_v12ri-admin-over}

- [Responsibilities for managing resources in API Connect](/docs/apiconnect?topic=apiconnect-responsibilities)
- [High availability and disaster recovery](/docs/apiconnect?topic=apiconnect-ha-dr)
- [Complete V12 Reserved documentation](https://www.ibm.com/docs/en/SSCL05_12.1.x){: external}

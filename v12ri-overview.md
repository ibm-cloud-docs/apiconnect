---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-29"

keywords: IBM Cloud, API Connect, V12 Reserved instance, overview, what's new

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# What is {{site.data.keyword.apiconnect_short}} V12 Reserved?
{: #v12ri-overview}

{{site.data.keyword.apiconnect_short}} V12 Reserved is a single-tenant API management environment hosted on IBM-managed infrastructure, offering expanded capabilities including Federated API Management, a new IBM Developer Portal, AI Gateway, and webMethods API Gateway integration.
{: shortdesc}

## Overview
{: #overview_v12ri-overview}

{{site.data.keyword.apiconnect_short}} V12 Reserved provides an individual {{site.data.keyword.apiconnect_short}} instance that runs on an infrastructure managed by IBM. It provides a single-tenant environment at a lower cost, and with more control over your environment, than a traditional cloud-based offering.

V12 Reserved includes all the core capabilities of V10 Reserved and adds the following key capabilities:

- **Federated API Management** — Centrally manage, govern, and monitor distributed API runtimes and data planes from a single interface, regardless of where they are deployed.
- **IBM Developer Portal** — A new web-based portal that supports API providers and API consumers, with hackathon support and built-in analytics.
- **IBM AI Gateway** — Manage AI services and LLM providers through a governed, policy-driven gateway.
- **webMethods API Gateway** — A secure, policy-driven runtime for managing and exposing APIs to external consumers (available on demand).
- **IBM API Studio** — An AI-powered tool for API design and management that replaces API Designer.
- **Dark Mode** — Available across all supported user interfaces.

## What's new in V12 Reserved
{: #whatsnew_v12ri-overview}

V12 Reserved introduces the following new features and enhancements:

### IBM API Studio replaces API Designer
{: #api_studio_v12ri-overview}

IBM API Studio is an AI-powered tool for API design and management. It replaces API Designer as the primary tool for creating, editing, and managing APIs in your reserved instance. For more information, see the [complete IBM API Studio documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

### Federated API Management
{: #fed_api_mgmt_v12ri-overview}

Federated API Management introduces a centralized way to manage distributed API environments. You can connect, manage, and monitor multiple API runtimes and data planes from a single interface, even when they are deployed across different regions, cloud platforms, or vendors.

Key benefits include:
- Unified policy templates for consistent governance across all environments
- Cross-platform visibility into performance, security, compliance, and subscription management
- Simplified management of gateway and portal runtimes from one place

### IBM Developer Portal
{: #dev_portal_v12ri-overview}

The new IBM Developer Portal provides an enhanced experience for API providers, API consumers, and administrators:
- API providers can publish APIs and related assets, run engagement programs such as hackathons, and track API usage through built-in analytics.
- API consumers can discover, test, and subscribe to APIs, and collaborate through the developer community.
- Administrators can configure and manage the portal, oversee user communities, and set up marketplaces.

### IBM AI Gateway
{: #ai_gateway_v12ri-overview}

IBM AI Gateway enables you to manage AI services, including LLM providers such as Watsonx.ai, OpenAI, and Azure OpenAI, through a governed, policy-driven gateway. You can also create and expose MCP tools and servers from existing APIs.

### webMethods API Gateway (on demand)
{: #wm_gateway_v12ri-overview}

webMethods API Gateway provides a secure, policy-driven runtime for managing and exposing APIs to external consumers. It enforces authentication, authorization, traffic management, and mediation policies. This capability is available on demand.

### TLS verification in Toolkit
{: #tls_toolkit_v12ri-overview}

The Toolkit now validates the server certificate signer during the TLS handshake. If you are upgrading from V10, review the updated login flags and certificate configuration requirements. For details, see the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

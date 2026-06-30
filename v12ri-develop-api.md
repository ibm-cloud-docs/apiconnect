---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-30"

keywords: IBM Cloud, API Connect, V12 Reserved instance, develop API, API Studio, toolkit

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Developing APIs in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v12ridevelop-api}

Use IBM API Studio and the API Connect toolkit to develop, test, and publish APIs in your {{site.data.keyword.apiconnect_short}} V12 Reserved instance.
{: shortdesc}

## Using IBM API Studio
{: #api_studio_v12ri-develop-api}

IBM API Studio is an AI-powered tool for API design and management that replaces API Designer. API Studio integrates with your version control system and connects to your API Connect instance, enabling you to create, edit, test, and manage APIs in a streamlined environment.

Key capabilities of IBM API Studio:
- Create REST and SOAP APIs in code view or form view
- Author and manage API policies including global policies
- Integrate with Git for version-controlled API projects
- Use the built-in linting engine to validate APIs against governance rulesets
- Connect to API Manager to publish APIs directly from the Studio

To get started with IBM API Studio:
1. Download and install IBM API Studio. For installation instructions, see the [IBM API Studio documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.
2. Configure your API Studio to connect to your V12 Reserved instance.
3. Create an API project and start designing your first API.

## Setting up the toolkit
{: #toolkit_v12ri-develop-api}

The API Connect toolkit provides a CLI for working with assets such as APIs, products, and catalogs. In V12 Reserved, TLS verification is enabled by default. Before you log in, ensure that you have the correct CA certificate available or configure the appropriate TLS flags.

### Logging in with TLS verification
{: #toolkit_tls_v12ri-develop-api}

Use the following command to log in to your V12 Reserved instance:

```bash
apic login --server <management-server-endpoint> \
           --username <username> \
           --password <password> \
           --realm <realm> \
           --ca <path-to-ca-certificate>
```
{: pre}

Where `<path-to-ca-certificate>` is the path to the CA certificate file for your management server. If your server uses a self-signed certificate, extract the ingress CA certificate from your cluster:

```bash
kubectl get secret ingress-ca \
  -n <namespace> \
  -o jsonpath='{.data.ca\.crt}' | base64 --decode > ingress-ca.pem
```
{: pre}

For certificates issued by well-known certificate authorities already in your system's trust store, you can omit the `--ca` flag.

### Toolkit configuration (one-time setup)
{: #toolkit_config_v12ri-develop-api}

Instead of passing TLS-related flags with every command, configure them once:

```bash
apic config:set --ca <path-to-ca-certificate>
```
{: pre}

## Developing APIs with API Manager
{: #api_mgr_v12ri-develop-api}

After developing your API in API Studio or using the toolkit, you can manage the API lifecycle using the API Manager web interface:

1. Log in to your V12 Reserved instance and navigate to the API Manager.
2. Create or import your API definition.
3. Package the API into a product and publish it to a catalog.
4. Configure plans, rate limits, and security policies.

For full API development and management documentation, see the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

## Using the AI Agent assistant
{: #assistant_v12ri-develop-api}

The Conversational API Agent (Public Preview) helps you create, manage, and discover APIs using natural language commands in VS Code. It integrates with API Studio to automate repetitive tasks and accelerate API development.

To learn more, see the [API Agent documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-29"

keywords: IBM Cloud, API Connect, V12 Reserved instance, AI Gateway, LLM, MCP, Watsonx

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# IBM AI Gateway in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v12ri-ai-gateway}

IBM AI Gateway enables you to manage AI services, including large language model (LLM) providers, through a governed, policy-driven gateway. You can register LLM providers, create MCP tools and servers from existing APIs, and monitor AI service usage.
{: shortdesc}

## Overview
{: #overview_v12ri-ai-gateway}

IBM AI Gateway lets you govern and manage access to AI services including:
- Watsonx.ai
- OpenAI
- Azure OpenAI
- Google Gemini
- Other OpenAI-compatible providers

Key capabilities include:
- **Governed LLM access** — Apply API Connect policies to LLM API calls, including rate limiting, authentication, and traffic management.
- **MCP tools and servers** — Generate MCP (Model Context Protocol) tools and servers from existing API definitions, enabling AI agents to call your APIs.
- **AI view in API Studio** — Manage AI services directly from IBM API Studio using the AI view.
- **Policy enforcement** — Apply gateway-specific policies for each supported LLM provider.

## Registering LLM providers
{: #llm_providers_v12ri-ai-gateway}

To register an LLM provider in your V12 Reserved instance:

1. Open IBM API Studio and navigate to the **AI** view.
2. Click **Register LLM provider**.
3. Select the LLM provider type (Watsonx.ai, OpenAI, Azure OpenAI, Google Gemini, or OpenAI-compatible).
4. Provide the required connection details and API keys.
5. Configure secrets for API key storage.

For step-by-step tutorials, see the following topics in the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}:
- Registering Watsonx.ai LLM provider
- Registering OpenAI LLM provider
- Registering Azure OpenAI LLM provider
- Registering Google Gemini LLM provider

## Working with MCP tools and servers
{: #mcp_v12ri-ai-gateway}

You can generate MCP tools and MCP servers from your existing API definitions. This allows AI assistants and agents to invoke your APIs through the MCP protocol.

To generate MCP tools from an existing API:

1. Open your API project in IBM API Studio.
2. Navigate to **AI** > **MCP tools**.
3. Select the API operations you want to expose as MCP tools.
4. Configure the MCP server settings.
5. Publish the MCP server.

For more information, see the MCP tools documentation in the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

## Configuring secrets for LLM provider API keys
{: #secrets_v12ri-ai-gateway}

IBM AI Gateway integrates with IBM Secrets Manager to securely store LLM provider API keys. To configure secrets for your LLM provider:

1. Create a secret in IBM Secrets Manager containing the LLM provider API key.
2. In API Studio, when registering the LLM provider, reference the secret instead of providing the API key directly.

For instructions, see the [Configuring secrets for LLM provider API keys](https://www.ibm.com/docs/en/api-connect/saas){: external} topic in the V12 Reserved documentation.

## Supported policies
{: #policies_v12ri-ai-gateway}

Each supported LLM provider has a set of supported AI Gateway policies. For the list of supported policies for each provider, see the [complete V12 Reserved documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.

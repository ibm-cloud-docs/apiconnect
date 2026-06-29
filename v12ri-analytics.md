---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-29"

keywords: IBM Cloud, API Connect, V12 Reserved instance, analytics

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Viewing API event analytics in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v12ri-analytics}

Use the Analytics feature to track API usage and performance, which helps you determine when APIs should be updated or retired.
{: shortdesc}

When you view analytics data in the API Manager, you see metrics about the APIs that your provider organization developed and shared with customers. Information is collated from API events, which occur each time an API is invoked by a consumer application. The ability to visualize API analytics in different styles and combinations helps you understand how your APIs are used. Use this insight when making decisions about which APIs to offer, when to replace or retire an API, and who is consuming your APIs.

## Accessing analytics in V12 Reserved
{: #access_v12ri-analytics}

To view analytics in your V12 Reserved instance:

1. Log in to your V12 Reserved instance.
2. Navigate to the **API Manager**.
3. Select your provider organization.
4. Click **Analytics** in the left navigation.

## Analytics dashboards
{: #dashboards_v12ri-analytics}

The Analytics feature provides several pre-built dashboards:
- **API Traffic** — View the total number of API calls over time.
- **Response Codes** — Analyze the distribution of HTTP response codes.
- **Latency** — Monitor average response latency for your APIs.
- **Application Activity** — View API usage broken down by consuming application.

You can customize dashboards by filtering by time range, API, product, catalog, or consumer application.

## Extended analytics documentation
{: #extended_docs_v12ri-analytics}

For the complete analytics documentation including advanced configuration, see the following topics in the extended V12 Reserved documentation:

- [Key concepts of API Connect analytics](https://www.ibm.com/docs/en/api-connect/saas){: external}
- [Accessing analytics](https://www.ibm.com/docs/en/api-connect/saas){: external}
- [Analytics dashboards](https://www.ibm.com/docs/en/api-connect/saas){: external}
- [Understanding your API usage](https://www.ibm.com/docs/en/api-connect/saas){: external}

## Offloading analytics data
{: #offload_v12ri-analytics}

You can configure V12 Reserved to offload analytics event data to external systems such as Kafka or HTTP endpoints for use with other analytics platforms. For instructions, see [Offloading analytics data](/docs/apiconnect?topic=apiconnect-v12ri-offload-analytics).

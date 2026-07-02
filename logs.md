---

copyright:
   years: 2024, 2026
lastupdated: "2026-07-02"

keywords: IBM Cloud, API Connect, V12 Reserved instance, logging, monitoring, logs

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Logging for {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #logs}

Monitor the operational logs for your {{site.data.keyword.apiconnect_short}} V12 Reserved instance using {{site.data.keyword.la_full_notm}}.
{: shortdesc}

## Configuring log monitoring
{: #configure_v12ri-logs}

{{site.data.keyword.apiconnect_short}} V12 Reserved forwards operational logs to {{site.data.keyword.la_full_notm}}. To monitor the logs for your instance:

1. Provision an instance of {{site.data.keyword.la_full_notm}} in the same region as your V12 Reserved instance.

   For information on provisioning the service, see [Provisioning an instance](/docs/log-analysis?topic=log-analysis-provision).

1. Configure your V12 Reserved instance to send logs to your {{site.data.keyword.la_short}} instance.

   For instructions on connecting the services, see the [Logging documentation](/docs/apiconnect?topic=apiconnect-vri-logging).

1. Use the {{site.data.keyword.la_short}} dashboard to view and filter logs for your V12 Reserved instance.

## Log types
{: #log_types_v12ri-logs}

V12 Reserved generates operational logs that include:
- API gateway request and response logs
- Administration activity logs
- System health and component status logs

## Searching and filtering logs
{: #search_v12ri-logs}

Use the {{site.data.keyword.la_short}} search and filtering capabilities to find specific events or patterns in the logs. You can:
- Filter by severity level (ERROR, WARN, INFO, DEBUG)
- Search for specific API names or request IDs
- Set up alerts for specific log patterns

## Activity Tracker events
{: #at_events_v12ri-logs}

In addition to operational logs, V12 Reserved generates Activity Tracker events that record administrative actions. For the complete list of tracked events, see [Activity Tracker events](/docs/apiconnect?topic=apiconnect-vri-at_events).

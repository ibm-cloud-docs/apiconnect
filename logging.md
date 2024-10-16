---

copyright:
  years: 2020, 2024
lastupdated: "2024-10-10"

keywords: platform logs, log analysis, log routing, API Connect
subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Logging for {{site.data.keyword.apiconnect_short}} Reserved
{: #logging}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.apiconnect_short}} Reserved, generate platform logs that you can use to investigate abnormal activity and critical actions in your account, and to troubleshoot problems.
{: shortdesc}

You can use {{site.data.keyword.logs_routing_full_notm}}, a platform service, to route platform logs in your account to a destination of your choice by configuring a tenant that defines where platform logs are sent. For more information, see [About Logs Routing](/docs/logs-router?topic=logs-router-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on platform logs that are generated in your account and routed by {{site.data.keyword.logs_routing_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.



As of 28 March 2024, the {{site.data.keyword.la_full_notm}} service is deprecated and will no longer be supported as of 30 March 2025. Customers will need to migrate to {{site.data.keyword.logs_full_notm}} before 30 March 2025. During the migration period, customers can use {{site.data.keyword.la_full_notm}} along with {{site.data.keyword.logs_full_notm}}. Logging is the same for both services. For information about migrating from {{site.data.keyword.la_full_notm}} to {{site.data.keyword.logs_full_notm}} and running the services in parallel, see [migration planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).
{: important}

## Locations where platform logs are generated
{: #log-locations}

{{site.data.keyword.apiconnect_short}} Reserved generates platform logs in all regions where the {{site.data.keyword.apiconnect_short}} Reserved service is available.

### Locations where logs are sent to {{site.data.keyword.la_full_notm}}
{: #la-legacy-locations}



{{site.data.keyword.apiconnect_short}} Reserved sends platform logs to {{site.data.keyword.la_full_notm}} in all regions where the {{site.data.keyword.apiconnect_short}} Reserved service is available.

## Locations where logs are sent by {{site.data.keyword.logs_routing_full_notm}}
{: #lr-locations}



{{site.data.keyword.apiconnect_short}} Reserved sends logs by {{site.data.keyword.logs_routing_full_notm}} in all regions where the {{site.data.keyword.apiconnect_short}} Reserved service is available.

## Platform logs that are generated
{: #log-platform}




{{site.data.keyword.apiconnect_short}} Reserved sends platform logs generated by IBM&reg; DataPower&reg;. For more information on the auditing events in {{site.data.keyword.apiconnect_short}} Reserved, see [Activity tracking events for {{site.data.keyword.apiconnect_short}} Reserved](/docs/apiconnect?topic=apiconnect-at_events).

## Enabling logging
{: #log-enable}

Logging is automatically enabled in your {{site.data.keyword.apiconnect_short}} Reserved service instance.

## Viewing logs
{: #log-viewing}


You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}



For more information about launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

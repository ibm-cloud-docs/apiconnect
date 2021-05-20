---

copyright:
  years: 2020, 2021
lastupdated: "2020-10-15"

keywords: API management, HA, high availability, disaster recovery, downtime, down time, failure, catasrophe, region, multizone region, MZR

subcollection: apiconnect

---

{:external: target="_blank" .external} 
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .note}

# Understanding high availability and disaster recovery for {{site.data.keyword.apiconnect_short}}
{: #ha-dr}

{{site.data.keyword.cloud_notm}} provides high-availability and disaster-recovery solutions to ensure that your APIs remain accessible.
{: shortdesc}

{{site.data.keyword.apiconnect_short}} instances are deployed in either a multi-zone region (e.g. Dallas, Frankfurt, London, Sydney, Tokyo, and Washington), or a single zone region / point-of-presence (e.g. Oslo, Seoul, and Chennai). Each instance is deployed in a highly-available configuration. That is, configuration data is replicated onto more than one server and multiple instances of each component are simultaneously active. This provides resiliency in the event of failures within a datacenter or rack.

In multi-zone regions, instance members are distributed across different data centers, or zones.
In single-zone regions, instance members are distributed across different hosts within the same data center.
In the case of a single zone failure in a multi-zone region or a hardware failure in any region, your instance is still accessible as it is replicated across other fully functioning servers. Such issues will be addressed by {{site.data.keyword.cloud_notm}} Specialists in place.

In addition to the high-availability configuration, your data is snapshotted and backed up daily by the {{site.data.keyword.apiconnect_short}} platform and stored in cross-region Cloud Object Storage buckets.

In the case of a complete region failure, the instance servers and APIS in the region may not be accessible, but the backup data will remain available. IBM will initiate internal disaster recovery procedures to restore your instance into the next nearest available region with enough capacity. IBM will also re-route managed DNS configuration to the recovered instance. This is typically completed within 24 hours of failure. When the original region is restored, IBM will migrate the instance back to the primary region.

For critical API traffic, IBM recommends that you deploy an API in at least two regions and globally load balance the regions. You can configure global load balancing with a technology such as {{site.data.keyword.cis_full}} ({{site.data.keyword.cis_short}}). {{site.data.keyword.cis_short}} provides health checking and routing rules to ensure that API traffic is automatically routed to the nearest healthy region. For more information about global load balancing, see the [Global Load Balancer (GLB) documentation](/docs/infrastructure/cis?topic=cis-global-load-balancer-glb-concepts).

For information about high availability and disaster recovery standards in {{site.data.keyword.Bluemix_notm}}, see [How IBM Cloud ensures high availability and disaster recovery](/docs/overview?topic=overview-zero-downtime#zero-downtime). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-zero-downtime#SLAs).


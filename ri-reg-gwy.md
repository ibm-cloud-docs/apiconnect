---

copyright:
  years: 2020
lastupdated: "2020-10-15"

keywords: management, Reserved plan, administer

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

# Adding a remote gateway
{: #ri-reg-gwy}

{{site.data.keyword.apiconnect_short}} V10 Reserved plan deploys with the IBM DataPower API gateway by default. You can deploy additional DataPower API gateways for use with your Reserved plan.
{: shortdesc}

{{site.data.keyword.apiconnect_short}} V10 Reserved plan deploys with the IBM DataPower API gateway already configured. The gateway hosts published APIs and provides the API endpoints used by client applications. The gateways also executes API proxy invocations to back-end systems and enforce API policies that manage client identification, security, and rate limiting.

You might want to deploy additional API Gateways for your Reserved plan; for example, to distribute API endpoints for different purposes. And gateways that you deploy are considered _remote_ because they are external to your Reserved plan.

To register a remote API Gateway with your Reserved plan, complete the following tasks:

1. [Install the API Gateway](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/tapic_install_datapower_files.html){: external}

2. [Set up certificates for the new gateway](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_certs.html){: external}

3. [Configure the gateway](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/tapic_install_datapower_gateway_apigwy..html){: external}

4. [Register the gateway](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_reg.html){: external}

After the gateway is registered, it is available for use in your Reserved plan. You can manage the gateways availability to users as explained in [Managing gateways](/docs/apiconnect?topic=apiconnect-ri-mng-gwy).

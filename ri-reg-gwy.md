---

copyright:
  years: 2020
lastupdated: "2020-10-30"

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

To register a remote API Gateway with your Reserved plan, click the **Download Gateway** tile on the administration Home page, and complete the following steps:

Step 1: Download - Select your environment and download the package. 

Step 2: Install - Select your environment to see the installation instructions for the gateway.

Step 3: Configure - Follow the instructions in [Adding remote gateways in V10 Reserved](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_intro.html){: external} to set up certificates and configure the new gateway.

Step 4: Register - Click the link to register the new gateway with your API Connect Reserved plan. For instructions, see  [Registering a gateway with V10 Reserved](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_reg.html){: external}

After the gateway is registered, it is available for use in your Reserved plan. You can manage the gateways availability to users as explained in [Managing gateways](/docs/apiconnect?topic=apiconnect-ri-mng-gwy).

---

copyright:
   years: 2020, 2021
lastupdated: "2020-10-30"

keywords: IBM Cloud, API Connect, V10, Reserved instance, lifecycle, develop, create, manage, API, user, role, access, group, administer

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

# Adding a customer-managed remote gateway
{: #ri-reg-gwy}

{{site.data.keyword.apiconnect_short}} V10 Reserved deploys with the IBM DataPower API gateway by default. You can deploy additional DataPower API gateways, which you manage, for use with your Reserved instance.
{: shortdesc}

{{site.data.keyword.apiconnect_short}} V10 Reserved deploys with the IBM DataPower API gateway already configured. The gateway hosts published APIs and provides the API endpoints used by client applications. The gateways also executes API proxy invocations to back-end systems and enforce API policies that manage client identification, security, and rate limiting. This default gateway is managed by IBM.

You might want to deploy additional API Gateways for your Reserved instance; for example, to distribute API endpoints for different purposes. Any gateways that you deploy are considered _remote_ because they are external to your Reserved service. You are responsible for deploying and managing your remote gateway.

To register a remote API Gateway with your Reserved instance, click the **Download Gateway** tile on the administration Home page, and complete the following steps:

Step 1: Download - Select your environment and download the package. 
If you use VMware and don't have a Passport Advantage contract, contact IBM Cloud Support to obtain the package.

Step 2: Install - Select your environment to see the installation instructions for the gateway. 

Step 3: Configure - Follow the instructions in [Adding remote gateways in V10 Reserved](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_intro.html){: external} to set up certificates and configure the new gateway.

Step 4: Register - Click the link to register the new gateway with your {{site.data.keyword.apiconnect_short}} Reserved instance. For instructions, see  [Registering a gateway with V10 Reserved](https://www.ibm.com/support/knowledgecenter/SSMNED_v10cloud/com.ibm.apic.install.doc/ri_gwy_reg.html){: external}

After the gateway is registered, it is available for use in your Reserved service. You can manage the gateways availability to users as explained in [Managing gateways](/docs/apiconnect?topic=apiconnect-ri-mng-gwy).

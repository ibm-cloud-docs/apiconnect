---

copyright:
   years: 2020, 2021
lastupdated: "2020-10-30"

keywords: IBM Cloud, API Connect, V10, Reserved instance, remote gateway, upgrade

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

# Upgrading a customer-managed remote gateway
{: #ri-upgrade-gwy}

If you deployed a customer-managed remote gateway for your {{site.data.keyword.apiconnect_short}} V10 Reserved instance, you must upgrade that gateway before upgrading the Reserved instance.
{: shortdesc}


To upgrade a remote API Gateway, complete the following steps:

1. In {{site.data.keyword.apiconnect_short}} V10 Reserved, click the **Download Gateway** tile on the administration Home page and download the gateway installation package for your environment. 

2. Proceed to the "Upgrade" section of the IBM DataPower Gateway [Installation Operations](https://www.ibm.com/support/knowledgecenter/SS9H2Y_10.0/com.ibm.dp.doc/installationoperations.html#upgradeoperation) documentation for instructions on upgrading your existing remote gateway with the newer package.

After the gateway is upgraded, it is available for use in your Reserved instance. You do not need to modify the gateway's registration information.

---

copyright:
  years: 2019
lastupdated: "2019-3-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Setting up an API Connect instance
{: #tut_prereq_set_up_apic_instance}

**Duration**: 15 mins  
**Skill level**: Beginner  


## Prerequisites
{: #prereq_tut_prereq_set_up_apic_instance}

1. An IBMid
2. A {{site.data.keyword.Bluemix_short}} account
3. An {{site.data.keyword.apiconnect_full}} instance with at least a _Lite_ plan


<table>
  <tr><td><b>IBMid</b>: Used to access all of IBM's apps, communities, support and more
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>: IBM's cloud platform that hosts {{site.data.keyword.apiconnect_short}} along with other apps and services<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>: A free version of {{site.data.keyword.apiconnect_short}} hosted on {{site.data.keyword.Bluemix_notm}}</td></tr>
  </table>  


---


1. Sign up for your IBM Cloud ID at the following URL: [https://cloud.ibm.com/registration/ ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/registration/){: #new_window}.

	Already have an IBMid? Then skip the registration, and just create your free {{site.data.keyword.Bluemix_short}} account at the following URL: [https://cloud.ibm.com/ ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/){: #new_window}.  

2. When you have your IBMid and {{site.data.keyword.Bluemix_notm}} account, create your {{site.data.keyword.apiconnect_short}} instance.  
  a. Log in to {{site.data.keyword.Bluemix_notm}}: [https://cloud.ibm.com/login ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/login){: #new_window}.  
  ![](images/cloud_login_page.png)  
  b. Create your _organization_ in {{site.data.keyword.Bluemix_notm}}. You will be prompted to do this the first time that you log in.  
  ![](images/prereqs-2.png)
  c. Create your _space_.  
  ![](images/prereqs-3.png)
  d. Go to [https://console.ng.bluemix.net/catalog/services/api-connect ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}.  
  ![](images/prereqs-4.png)  
  e. Select the _Lite_ pricing plan (free), and click **Create** to get started.  
  ![](images/lite-plan.png)  
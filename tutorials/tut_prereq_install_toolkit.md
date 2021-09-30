---

copyright:
   years: 2017, 2021
lastupdated: "2017-10-31"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials, API Connect V5

subcollection: apiconnect

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Installing the API Connect V5 Toolkit
{: #tut_prereq_install_toolkit}

**Duration**: 15 mins  
**Skill level**: Beginner  

## Prerequisites
{: #prereq_tut_prereq_install_toolkit}

1. Node.js: An asynchronous, event-driven JavaScript runtime that is used to build and run scalable network applications.
2. Node package manager (npm): A JavaScript package manager and software registry.
3. {{site.data.keyword.apiconnect_full}} _Lite_: A free version of {{site.data.keyword.apiconnect_short}} that is hosted on your laptop.


## Install node.js
{: #nodejs_tut_prereq_install_toolkit}

1. Download and install node.js from one of the following sources:
   * [https://nodejs.org/en/download/](https://nodejs.org/en/download/){: external} (Note: Download the LTS version for your platform, not the latest, or you might experience errors.)
   * [https://developer.ibm.com/node/sdk/v6/)](https://developer.ibm.com/node/sdk/v6/){: external}  

    _Installing node.js also installs the **npm** (Node Package Manager)_.

2.  Make sure that node.js is in your _PATH_.
    ![](images/verify-path.png)  

3. Update **npm** by running the following commnad: `npm install -g npm` 
   Setting npm `--engine-strict` or `npm config set engine-strict true` prevents the installation from completing.
   {: note}

4. Check the installed version and path.
   ![](images/screenshot_install_apic-1.png)  



## Install the API Connect toolkit and Microgateway
{: #tk_micro_tut_prereq_install_toolkit}

1. Update the npm config to allow use of untrusted certificates.  
   `npm config -g set strict-ssl false`  

2. Install the {{site.data.keyword.apiconnect_short}} toolkit from **npm**.  
    `npm install -g apiconnect`

3. Check the installed version.  
    `apic -v`

4. Run the following command: `npm install -g microgateway`

The Microgateway functions as a local test server.

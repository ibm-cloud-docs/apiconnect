---
copyright:
  years: 2017
lastupdated: "2017-09-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Installing the API Connect Toolkit
**Duration**: 15 mins  
**Skill level**: Beginner  

## What you'll need
1. Node.js
2. Node Product Manager (NPM)
3. {{site.data.keyword.apiconnect_short}} _Lite_

<table>
  <tr><td><b>Node.js</b>: An asychronous event driven JavaScript runtime used to build and run scalable network applications
    <br>
    <b>Node Product Manager</b>: JavaScript package manager and software registry<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>: A free version of {{site.data.keyword.apiconnect_short}} that is hosted on your laptop</td></tr>
  </table>  


## Install node.js
1. Download and install node.js from one of the two sources:
   * [https://nodejs.org/en/download/ ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://nodejs.org/en/download/){:new_window} (Note: Download the LTS version for your platform, not the latest, or you might experience errors.)
      **OR**
   * [https://developer.ibm.com/node/sdk/v6/ ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _Installing node.js also installs **npm** (Node Package Manager)_.

2.  Once Node.js is downloaded and install, check to make sure it is in your _PATH_.
    ![](images/verify-path.png)  

3. Update **npm**. In a command line, enter `npm install -g npm`.  
   **Note:** Setting npm `--engine-strict` or `npm config set engine-strict true` prevents installation from completing.


4. Check the installed version and path.
   ![](images/screenshot_install_apic-1.png)  



## Install the API Connect toolkit and Microgateway
1. Update the npm config to allow use of untrusted certificates.  
   `npm config -g set strict-ssl false`  

2. Install the {{site.data.keyword.apiconnect_short}} toolkit from **npm**.  
    `npm install -g apiconnect`

3. Check the installed version.  
    `apic -v`

4. Enter the following command on the command line: `npm install -g microgateway`.

We will use the Microgateway as a local test server.

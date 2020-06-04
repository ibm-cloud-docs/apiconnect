---

copyright:
  years: 2017, 2019
lastupdated: "2019-12-31"

keywords: IBM Cloud, API Connect, API management, API, APIs, lifecycle, troubleshooting, trouble, troubleshoot, API Connect Enterprise, API Connect Hybrid

subcollection: apiconnect

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Troubleshooting
{: #apic_troubleshoot}

Here are the answers to common troubleshooting questions about using {{site.data.keyword.apiconnect_long}}.
{:shortdesc}

## Username and password required when adding the {{site.data.keyword.apiconnect_short}} service
{: #user_pw-apic_troubleshoot}

After you add the service to your {{site.data.keyword.cloud_notm}} Dashboard, you are prompted for a username and password when you try to open it. 

### Symptoms
{: #ts_sym_usernamepw-apic_troubleshoot}

Instead of accessing the {{site.data.keyword.cloud_notm}} service directly when you open a new {{site.data.keyword.apiconnect_short}}, it requires you to log in to the API Manager.

### Cause
{: #ts_cause_usernamepw-apic_troubleshoot}

Your browser is set to block cookies, or the level is set to a more restricted level than {{site.data.keyword.apiconnect_short}} requires.

### Resolution
{: #ts_res_usernamepw-apic_troubleshoot}

Enable or increase the permission level of cookies in your browser settings until it opens the {{site.data.keyword.cloud_notm}} service.

## Incorrect permissions after logging in to {{site.data.keyword.apiconnect_short}}
{: ts_permissions-apic_troubleshoot}

You log in to {{site.data.keyword.apiconnect_short}} successfully but have no permissions.

### Symptoms
{: ts_sym_permissions-apic_troubleshoot}

You are unable to complete tasks that you normally have permissions to execute.

### Cause
{: #ts_cause_permissions-apic_troubleshoot}

Possible issue with the server, which might be corrected with a fresh login.

### Resolution
{: #ts_res_permissions-apic_troubleshoot}

1. Log out.
2. Wait several minutes to ensure the logout operation completes.
3. Log in again and try to complete the tasks.

If the permissons issue still persists, contact [{{site.data.keyword.apiconnect_short}} Support](https://cloud.ibm.com/docs/get-support?topic=get-support-getting-customer-support){: external}.

## Unable to install the developer toolkit
{: #unable_tk-apic_troubleshoot}

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the developer toolkit and
the installation fails.

### Symptoms
{: #ts_sym_noinstalltk-apic_troubleshoot}

The following errors are displayed during the developer toolkit
installation:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Cause
{: #ts_cause_noinstalltk-apic_troubleshoot}

You don't have the required rights to create files or directories.

### Resolution
{: #ts_res_noinstalltk-apic_troubleshoot}

Change the rights for the specified directories, or run the command using
`sudo`. On a local development system, it is better to fix the directory rights as
follows:
```
sudo chown -R $USER /usr/local
```
{:codeblock}

This command makes your user account the owner of the `/usr/local` directory. Then, you will not need to use sudo to
install Node or install packages globally with npm. 
    **Note:** Changing directory ownership is appropriate only on a local development system. Never do this on a server system.

Also, do not use the previous
`chown` command on the `/usr/bin` directory;
doing so can seriously misconfigure your system.

If you have to use `sudo`, use
the following command:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Unable to install the developer toolkit on Windows
{: #unable_tk_win-apic_troubleshoot}

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the
developer toolkit and the installation fails.

### Symptoms
{: #ts_sym_noinstalltk_path-apic_troubleshoot}

You are trying to install the developer toolkit on Windows and you receive an error message that states your *path should be less than 248 characters*.

### Cause
{: #ts_cause_noinstalltk_path-apic_troubleshoot}

On Windows systems, there is a maximum path length,
which is exceeded when you try to install all of the dependencies in a deep level folder.

### Resolution
{: #ts_res_noinstalltk_path-apic_troubleshoot}

You can fix this problem in one of the following ways:

- Ensure that you have installed the correct version of Node.js. For more information, see [Installing the Developer Toolkit](/docs/apiconnect?topic=apiconnect-creating_apis).

- If you had to upgrade a program, try the installation again.

If that does not work, install {{site.data.keyword.apiconnect_short}} at a level higher than the likely `C:/program files/nodejs/bin/node_modules...` folder. If you install at a top-level directory, you will not see this error.

## Unable to install the developer toolkit on Mac OS X
{: #unable_tk_mac-apic_troubleshoot}

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the developer toolkit and the installation fails.

### Symptoms
{: #ts_sym_noinstalltk_mac-apic_troubleshoot}

The following errors are displayed during the developer toolkit installation:
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### Cause
{: #ts_cause_noinstalltk_mac-apic_troubleshoot}

You recently upgraded or installed Xcode and have not agreed to the license yet.

### Resolution
{: #ts_res_noinstalltk_mac-apic_troubleshoot}

1. Enter the following command to validate your Xcode license:
```
sudo xcode-select
```
{:codeblock}

2. Reinstall the developer toolkit.


## Unable to install the developer toolkit on Ubuntu
{: #unable_tk_ubu-apic_troubleshoot}

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the
developer toolkit and the installation fails.

### Symptoms
{: #ts_sym_noinstalltk_ubu-apic_troubleshoot}

The following errors are displayed during the developer toolkit
installation:
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### Resolution
{: #ts_res_noinstalltk_ubu-apic_troubleshoot}

Enter the following command to resolve the
problem:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Unable to debug the npm installation failure
{: #unable_nmp-apic_troubleshoot}

When you follow the steps to install the developer toolkit, the npm installation
fails.

### Symptoms
{: #ts_sym_npmfail-apic_troubleshoot}

The npm installation fails without providing any useful information to
debug.

### Resolution
{: #ts_res_npmfail-apic_troubleshoot}

When an installation fails, npm writes a line in the `npm-debug.log</filepath>`
file to show where the error is located. Use the `npm-debug.log` file to determine
the cause.

## Unable to open the API Designer
{: #unable_apid-apic_troubleshoot}

You enter the command `apic edit` and the API Designer does not
open.

### Symptoms
{: #ts_sym_noopenapid-apic_troubleshoot}

You are unable to open an instance of the API Designer after you enter the command:
```
apic edit
```
and the following message is displayed:
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### Cause
{: #ts_cause_noopenapid-apic_troubleshoot}

You have already started an instance of the API Designer from another command
window.

### Resolution
{: #ts_res_noopenapid-apic_troubleshoot}

To fix this problem, you need to close the other command window as described in the
following steps:

1. In the other command window, press **Ctrl + C**.

2. The following message is displayed.
```
Terminate Batch job (Y/N)?
```

3. Type `Y` and press Enter.

## Cannot configure billing information for a Product
{: #cannot_bill-apic_troubleshoot}

Some of the billing information is not available to configure or commit to production. 

### Symptoms
{: #ts_sym_nobill-apic_troubleshoot}

  - When you look at the Admin section of your Product, the Billing tab is not displayed.
  - When you try to publish a Product with the billing information specified, you get an error. 

### Cause
{: #ts_cause_nobill-apic_troubleshoot}

You must have the correct {{site.data.keyword.apiconnect_short}} account and permissions to enable billing information.

## Cannot subscribe to a billing Plan with a Product
{: #cannot_bill_plan-apic_troubleshoot}

Stripe limits each customer to a maximum of 25 subscriptions. Ensure that you have not exceeded
this limit. If so, you can only add this subscription if you remove another subscription.

### Symptoms
{: #ts_sym_nosubscribe-apic_troubleshoot}

You see an error when you try to subscribe to a Plan with billing, though you have other Plans configured.

### Cause
{: #ts_cause_nosubscribe-apic_troubleshoot}

The Stripe credit card processing service allows a maximum of 25 subscriptions per account.

### Resolution
{: #ts_res_nosubscribe-apic_troubleshoot}

Ensure that you have an Enterprise level account for your {{site.data.keyword.apiconnect_short}} service, and that there are fewer than 25 instances. If you already have the maximum number of instances, remove an instance.

## Getting help and support for API Connect
{: #get_help-apic_troubleshoot}

If you have problems or questions when using {{site.data.keyword.apiconnect_short}}, you can get help by searching for information or by asking questions through a forum. You can also open a support ticket.

When using the forums to ask a question, tag your question so that it is seen by the {{site.data.keyword.cloud_notm}} development teams. 

- If you have technical questions about developing or deploying an app with {{site.data.keyword.apiconnect_short}}, post your question on Stack Overflow and tag your question with "ibm-cloud" and "api connect."

- For questions about the service and getting stated instructions, use the IBM DeveloperWorks dW Answers forum. Include the "ibm cloud" and "api connect" tags.
See Getting help for more details about using the forums. 

For information about opening an IBM support ticket, or about support levels and ticket severities, see Contacting support.

---
copyright:
  years: 2017
lastupdated: "2017-07-10"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Troubleshooting
{: #troubleshoot}

Here are the answers to common troubleshooting questions about using {{site.data.keyword.apiconnect_long}} on {{site.data.keyword.Bluemix_short}}.
{:shortdesc}

## Unable to install the developer toolkit

After you provision the API Connect service, you try to install the developer toolkit and
the installation fails.

### Symptoms

The following errors are displayed during the developer toolkit
installation:
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### Cause

You don't have the required rights to create files or directories.

### Resolution

Change the rights for the specified directories, or run the command using
```sudo```. On a local development system, it is better to fix the directory rights as
follows:

```
sudo chown -R $USER /usr/local
```
{:codeblock}

This command makes your user account the owner of the ```/usr/local``` directory. Then, you will not need to use sudo to
install Node or install packages globally with npm. For more information, see [How to Node](http://howtonode.org/introduction-to-npm). **Note:** Changing directory ownership is appropriate only on a local development system.
Never do this on a server system.

Also, do not use the previous
```chown``` command on the ```/usr/bin``` directory;
doing so can seriously misconfigure your system.

If you have to use ```sudo```, use
the following command:
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Unable to install the developer toolkit on Windows

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the
developer toolkit and the installation fails.

### Symptoms

You are trying to install the developer toolkit on Windows and you receive an error message that states your *path should be less than 248 characters*.

### Cause

On Windows systems, there is a maximum path length,
which is exceeded when you try to install all of the dependencies in a deep level folder.

### Resolution

You can fix this problem in one of the following ways:

- Ensure that you have installed the correct version of Node.js. For more information, see [***link](apic_001.html).

- If you had to upgrade a program, try the installation again.

If that does not work, install {{site.data.keyword.apiconnect_short}} at a level
higher than the likely ```C:/program files/nodejs/bin/node_modules...``` folder. If you
install at a top-level directory, you will not see this error.

## Unable to install the developer toolkit on Mac OS X

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the
developer toolkit and the installation fails.

### Symptoms

The following errors are displayed during the developer toolkit
installation:
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### Cause

You recently upgraded or installed Xcode and have not agreed to the license
yet.

### Resolution

1. Enter the following command to validate your Xcode license:
```
sudo xcode-select
```
{:codeblock}

2. Reinstall the developer toolkit.


## Unable to install the developer toolkit on Ubuntu

After you provision the {{site.data.keyword.apiconnect_short}} service, you try to install the
developer toolkit and the installation fails.

### Symptoms

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

Enter the following command to resolve the
problem:
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## Unable to debug the npm installation failure

When you follow the steps to install the developer toolkit, the npm installation
fails.

### Symptoms

The npm installation fails without providing any useful information to
debug.

### Resolution

When an installation fails, npm writes a line in the ```npm-debug.log</filepath>```
file to show where the error is located. Use the ```npm-debug.log``` file to determine
the cause.

## Unable to open the API Designer

You enter the command ```apic edit``` and the API Designer does not
open.

### Symptoms

You are unable to open an instance of the API Designer after you enter the command:
```
apic edit
```
and the following message is displayed:

```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### Cause

You have already started an instance of the API Designer from another command
window.

### Resolution

To fix this problem, you need to close the other command window as described in the
following steps:

1. In the other command window, press **Ctrl + C**.

2. The following message is displayed.
```
Terminate Batch job (Y/N)?
```

3. Type ```Y``` and press Enter.

## Getting help and support for {{site.data.keyword.apiconnect_short}}

If you have problems or questions when using {{site.data.keyword.apiconnect_short}}, you can get help by searching for information or by asking questions through a forum. You can also open a support ticket.

When using the forums to ask a question, tag your question so that it is seen by the {{site.data.keyword.Bluemix_short}} development teams. 

- If you have technical questions about developing or deploying an app with {{site.data.keyword.apiconnect_short}}, post your question on Stack Overflow and tag your question with "ibm-bluemix" and "api connect."

- For questions about the service and getting stated instructions, use the IBM DeveloperWorks dW Answers forum. Include the "bluemix" and "api connect" tags.
See Getting help for more details about using the forums. 

For information about opening an IBM support ticket, or about support levels and ticket severities, see Contacting support.
 


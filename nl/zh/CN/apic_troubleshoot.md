---
copyright:
  years: 2017
lastupdated: "2017-10-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 故障诊断
{: #troubleshoot}

下面是有关在 {{site.data.keyword.Bluemix_short}} 上使用 {{site.data.keyword.apiconnect_long}} 的常见故障诊断问题的回答。
{:shortdesc}

## 添加 API Connect Bluemix 服务时需要用户名和密码

将服务添加到 {{site.data.keyword.Bluemix_short}}“仪表板”后，在尝试打开该服务时，系统会提示您输入用户名和密码。 

### 症状
{: #ts_sym_usernamepw}

打开新的 {{site.data.keyword.apiconnect_short}} 时无法直接访问 {{site.data.keyword.Bluemix_short}} 服务，而需要登录到 API Manager。

### 原因
{: #ts_cause_usernamepw}

浏览器设置为阻止 cookie，或者级别设置为比 {{site.data.keyword.apiconnect_short}} 所需级别限制更严的级别。

### 解决方法
{: #ts_res_usernamepw}

在浏览器设置中启用或增加 cookie 的许可权级别，直至打开 {{site.data.keyword.Bluemix_short}} 服务为止。

## 无法安装开发者工具箱

供应 API Connect 服务后，您尝试安装开发者工具箱，但安装失败。

### 症状
{: #ts_sym_noinstalltk}

开发者工具箱安装期间，显示以下错误：
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### 原因
{: #ts_cause_noinstalltk}

您不具有创建文件或目录所需的权限。

### 解决方法
{: #ts_res_noinstalltk}

更改指定目录的权限，或使用 `sudo` 运行命令。在本地开发系统上，最好按如下所示修正目录权限：
```
sudo chown -R $USER /usr/local
```
{:codeblock}

此命令使您的用户帐户成为 `/usr/local` 目录的所有者。然后，您将不需要使用 sudo 来安装节点或使用 npm 全局安装软件包。有关更多信息，请参阅[如何使用 Node ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://howtonode.org/introduction-to-npm){: new_window}。**注：**您只能在本地开发系统上更改目录所有权。永远不要对服务器系统执行此操作。

此外，请勿在 `/usr/bin` 目录上使用先前的 `chown` 命令；执行此操作可能会导致系统配置严重错误。

如果必须使用 `sudo`，请使用以下命令：
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## 无法在 Windows 上安装开发者工具箱

供应 {{site.data.keyword.apiconnect_short}} 服务后，您尝试安装开发者工具箱，但安装失败。

### 症状
{: #ts_sym_noinstalltk_path}

您是尝试在 Windows 上安装开发者工具箱，但收到一条错误消息，声明*路径长度应该短于 248 个字符*。

### 原因
{: #ts_cause_noinstalltk_path}

在 Windows 系统上，存在最大路径长度，您尝试在某个深层文件夹中安装所有依赖项时，该文件夹的路径超过了最大路径长度。

### 解决方法
{: #ts_res_noinstalltk_path}

您可以使用以下某种方法来解决此问题：

- 确保已安装正确版本的 Node.js。有关更多信息，请参阅[安装开发者工具箱](creating_apis.html)。

- 如果必须升级程序，请重试安装。

如果无效，请在比可能的文件夹 `C:/program files/nodejs/bin/node_modules...` 更高的级别安装 {{site.data.keyword.apiconnect_short}}。如果在顶级目录中进行安装，那么不会看到此错误。

## 无法在 Mac OS X 上安装开发者工具箱

供应 {{site.data.keyword.apiconnect_short}} 服务后，您尝试安装开发者工具箱，但安装失败。

### 症状
{: #ts_sym_noinstalltk_mac}

开发者工具箱安装期间，显示以下错误：
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### 原因
{: #ts_cause_noinstalltk_mac}

您最近升级或安装了 Xcode，但尚未同意许可证。

### 解决方法
{: #ts_res_noinstalltk_mac}

1. 输入以下命令以验证 Xcode 许可证：
```
sudo xcode-select
```
{:codeblock}

2. 重新安装开发者工具箱。


## 无法在 Ubuntu 上安装开发者工具箱

供应 {{site.data.keyword.apiconnect_short}} 服务后，您尝试安装开发者工具箱，但安装失败。

### 症状
{: #ts_sym_noinstalltk_ubu}

开发者工具箱安装期间，显示以下错误：
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3
node-pre-gyp install --fallback-to-build
/usr/bin/env: node: No such file or directory
npm WARN This failure might be due to the use of legacy binary "node"
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian
npm ERR! weird error 127
npm ERR! not ok code 0
```

### 解决方法
{: #ts_res_noinstalltk_ubu}

输入以下命令以解决此问题：
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## 无法调试 npm 安装故障

遵循提供的步骤安装开发者工具箱时，npm 安装失败。

### 症状
{: #ts_sym_npmfail}

npm 安装失败，并且未提供任何有用信息进行调试。

### 解决方法
{: #ts_res_npmfail}

安装失败时，npm 会在 `npm-debug.log </filepath>`
文件中写入一行以显示错误所在位置。请使用 `npm-debug.log` 文件确定错误原因。

## 无法打开 API Designer

输入 `apic edit` 命令后，API Designer 并未打开。

### 症状
{: #ts_sym_noopenapid}

输入以下命令后，无法打开 API Designer 的实例：
```
apic edit
```
并且会显示以下消息：
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### 原因
{: #ts_cause_noopenapid}

您已经在其他命令窗口中启动 API Designer 的实例。

### 解决方法
{: #ts_res_noopenapid}

要解决此问题，您需要关闭其他命令窗口，如以下步骤中所述：

1. 在其他命令窗口中，按 **Ctrl + C**。

2. 这将显示以下消息。
```
Terminate Batch job (Y/N)?
```

3. 输入 `Y` 并按 Enter 键。

## 无法配置产品的帐单信息

部分帐单信息不可用，无法配置或落实到生产。 

### 症状
{: #ts_sym_nobill}

  - 查看产品的“管理”部分时，不会显示“帐单”选项卡。
  - 尝试发布指定有帐单信息的产品时，收到错误。 

### 原因
{: #ts_cause_nobill}

您必须有正确的 {{site.data.keyword.apiconnect_short}} 帐户和许可权才能启用帐单信息。

## 无法预订产品的收费套餐

Stripe 将每个客户的最大预订数限制为 25 个。请确保您未超过此限制。如果超过，那么仅当除去另一个预订后，才能添加此预订。

### 症状
{: #ts_sym_nosubscribe}

虽然配置了其他套餐，但在尝试预订收费套餐时，您会看到错误。

### 原因
{: #ts_cause_nosubscribe}

Stripe 信用卡处理服务允许每个帐户最多有 25 个预订。

### 解决方法
{: #ts_res_nosubscribe}

确保您有 {{site.data.keyword.Bluemix_short}} {{site.data.keyword.apiconnect_short}} 服务的企业级别帐户，并且实例数少于 25 个。如果您已经有最大数量的服务，请除去某个服务。

## 获取 API Connect 的帮助和支持

如果您在使用 {{site.data.keyword.apiconnect_short}} 时有任何疑问或遇到任何问题，您可以在论坛中搜索相关信息或进行提问来获取帮助。
还可以提交支持凭单。

使用论坛进行提问时，请使用适当的标记来标注您的问题，以方便 {{site.data.keyword.Bluemix_short}} 开发团队识别。 

- 如果您有关于使用 {{site.data.keyword.apiconnect_short}} 开发或部署应用程序的技术问题，请将您的问题发布到 Stack
Overflow 上，并使用“ibm-bluemix”和“api connect”标记您的问题。

- 有关服务的问题和入门指示信息，请使用 IBM DeveloperWorks dW Answers 论坛。请加上“bluemix”和“api connect”标记。有关使用论坛的更多详细信息，请参阅“获取帮助”。 

有关开具 IBM 支持凭单的信息，或有关支持级别和凭单严重性的信息，请参阅“联系支持人员”。




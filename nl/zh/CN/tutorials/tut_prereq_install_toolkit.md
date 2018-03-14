---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 安装 API Connect 工具箱
**持续时间**：15 分钟  
**技能级别**：初学者  

## 所需项目
1. Node.js
2. Node Product Manager (NPM)
3. {{site.data.keyword.apiconnect_full}} _Lite_

<table>
  <tr><td><b>Node.js</b>：事件驱动的异步 JavaScript 运行时，用于构建和运行可扩展网络应用程序<br>
    <b>Node Product Manager</b>：JavaScript 软件包管理器和软件注册表<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>：在笔记本电脑上托管的 {{site.data.keyword.apiconnect_short}} 免费版本</td></tr>
  </table>  


## 安装 node.js
1. 从以下两个源之一下载并安装 node.js：
   * [https://nodejs.org/en/download/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://nodejs.org/en/download/){:new_window}（注：请下载适用于您平台的 LTS 版本，而不是最新版本，否则可能会遇到错误。）**或**
   * [https://developer.ibm.com/node/sdk/v6/ ![外部链接图标](../../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _安装 node.js 还会安装 **npm** (Node Package Manager)_。

2.  一旦下载并安装 Node.js 后，请检查以确保它位于 _PATH_ 中。
![](images/verify-path.png)  

3. 更新 **npm**。在命令行中，输入 `npm install -g npm`。  
   **注：**设置 npm `--engine-strict` 或 `npm config set engine-strict true` 将阻止安装完成。


4. 检查已安装的版本和路径。
![](images/screenshot_install_apic-1.png)  



## 安装 API Connect 工具箱和 Micro Gateway
1. 更新 npm 配置以允许使用不可信证书。  
   `npm config -g set strict-ssl false`  

2. 通过 **npm** 安装 {{site.data.keyword.apiconnect_short}} 工具箱。  
    `npm install -g apiconnect`

3. 检查已安装的版本。  
    `apic -v`

4. 在命令行上输入以下命令：`npm install -g microgateway`。

我们将使用 Micro Gateway 作为本地测试服务器。

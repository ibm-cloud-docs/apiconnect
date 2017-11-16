---

copyright:
  years: 2017
lastupdated: "2017-09-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 创建 API
{: #creating_apis}

您可以通过下载开发者工具箱并使用命令行界面 (CLI) 或 API Designer 来创建 API。

## 开发者工具箱 CLI
{: #dev_tk_cli notoc}

开发者工具箱提供了可用于将 API 发布到 {{site.data.keyword.apiconnect_long}} 的命令行界面。通过将 API 包含在产品中，然后发布该产品，就可以发布这些 API。通过在本地文件系统中创建和验证 YAML 定义文件来定义 API 和产品。这样，您就可以使用工具箱命令来与 {{site.data.keyword.apiconnect_long}} 交互。

## API Designer
{: #designer notoc}

API Designer 是开发者工具箱中的脱机图形用户界面，提供了用于创建和配置 API 的功能。API Designer 通过命令行界面使用 edit 命令来运行。使用 edit 命令时，API Designer 会在缺省浏览器中打开，或者可通过运行该命令时显示的本地主机端口进行访问。

## 安装开发者工具箱
{: #install_dev_tk}

### 先决条件
{: #prereq_install_dev_tk}

开始之前，您必须在要使用工具箱的机器上安装 [Node.js ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://nodejs.org/en/){:new_window}，并确保 `node` 位于您的 `PATH` 中。

安装开发者工具箱时，会安装以下各项。

- {{site.data.keyword.apiconnect_short}} 命令行工具
- {{site.data.keyword.apiconnect_short}} 图形编辑器
- 本地 {{site.data.keyword.apiconnect_short}} Micro Gateway


1. 要安装工具箱，请以管理员身份打开命令提示符并输入以下命令。

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **注：**安装期间，您可能会看到来自 `node-gyp` 模块的错误。这些错误来自可选依赖关系，安装将会成功完成。


2. 要查看所有工具箱命令的用法帮助汇总信息，请输入以下命令：

    ```
    apic
    ```
	{: codeblock}

3. 要查看任何命令的用法帮助，请使用 `--help` 选项。例如：

    ```
    apic validate --help
    ```
	{: codeblock}
	
## 安装 LoopBack 连接器
{: #install_lb_conn}

您必须安装数据源连接器，才能使用 LoopBack 数据源，来访问后端系统（如数据库）中的数据。
内存中和电子邮件连接器内置于 LoopBack 中，所以无需进行安装。

### 先决条件
{: #prereq_install_lb_conn}

Oracle、DB2 和 SQLLite 连接器需要 C 编译器工具，才能构建和安装二进制扩展。
确切的需求取决于操作系统，如下表所述。

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>表 1. 特定于操作系统的安装需求</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.microsoft.com/en-us/download/details.aspx?id=17851) <a href="https://www.microsoft.com/en-us/download/details.aspx?id=17851" rel="external" target="blank" title="（在新选项卡或窗口中打开）" >Microsoft .NET Framework 4</a></td>
<td style="width: 33.3%">Python V2.7（不支持 V3.x）</td>
<td style="width: 33.3%" > [针对 Mac OS X 的 Python 发行版 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.python.org/downloads/mac-osx/)<a href="https://www.python.org/downloads/mac-osx/" rel="external" target="blank" title="（在新选项卡或窗口中打开） " >针对 Mac OS X 的 Python 发行版</a></td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.visualstudio.com/downloads/download-visual-studio-vs) <a href="https://www.visualstudio.com/downloads/download-visual-studio-vs" rel="external" target="blank" title="（在新选项卡或窗口中打开）" >Visual Studio</a></td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716) <a href="https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716" rel="external" target="blank" title="（在新选项卡或窗口中打开）" >Xcode</a></td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python V2.7.10 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.python.org/downloads/release/python-2710/) <a href="https://www.python.org/downloads/release/python-2710/" rel="external" target="blank" title="（在新选项卡或窗口中打开）" >Python V2.7.10</a></td>
<td style="width: 33.3%">C/C++ 编译器工具链，例如 GCC V4.2 或更高版本。</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279) <a href="https://www.microsoft.com/en-gb/download/details.aspx?id=8279" rel="external" target="blank" title="（在新选项卡或窗口中打开）">Microsoft Windows SDK for Windows 7</a></td>
<td style="width: 33.3%">在 Debian 和 Debian 派生的分发版（Ubuntu、Mint 等）上，使用以下命令：<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm V3。请参阅以下注释。</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**注：**对于 Windows 安装：

- 除非您想购买 Visual Studio Enterprise，否则请使用 Visual Studio Community。运行安装程序，在“编程语言”下选中“Visual C++”，然后接受缺省安装位置。

- 对于 Node.js 和本机模块的 64 位构建，您还需要 Windows&trade; 7 64 位 SDK。如果安装失败，请先尝试卸载任何您已安装的 C++ 2010 x64&amp;x86 可再分发包。如果您收到错误称未安装 64 位编译器，那么您还可能需要针对 Windows&trade; SDK 7.1 编译器更新。
- 输入以下命令，以安装 npm V3：
  ```
  npm install -g npm
  ```
  {: codeblock}
然后，确保 npm 命令使用正确的版本：
  ```
  npm -v
  ```
  {: codeblock}
如果所显示的版本不是 3.x.x，请编辑您的系统 PATH，以确保 `C:\Users\username\AppData\Roaming\npm` 取代任何其他条目。
1. **可选**：如果使用的是 API Designer，请打开新的 shell 窗口。

2. 当您已安装操作系统所需的编译器工具时，请输入以下命令以在项目根目录中安装连接器。

```
npm install --save <connector-package>
```
{: codeblock}
其中，`<connector-package>` 是 LoopBack 连接器的 npm 软件包的名称，如表中所示。
<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>表 3. LoopBack 连接器</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">数据源</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">连接器包</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web Service</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web Service</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## 使用 CLI 创建 LoopBack API
{: #create_lb_api}

以下过程描述了如何使用命令行界面来创建 LoopBack&reg; API。


### 先决条件
{: #prereq_create_lb_api}

开始之前，请准备好要使用的目录的目录标识。要获取目录标识，请完成以下步骤：  

1. 转至 {{site.data.keyword.apiconnect_short}} **仪表板**。

2. 对于要使用的目录，单击**显示目录标识**图标 <img alt="“链链接”图标，用于显示目录标识" src="images/chain_link_icon.png">。

3. 复制目录标识。例如：  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    其中：

    - `<region>` 是 {{site.data.keyword.Bluemix_short}} 区域。

    - `<username_string>` 是不带任何符号的 {{site.data.keyword.Bluemix_short}} 组织标识。例如，`joe@mycompany.com` 会是 `joemycompanycom`

    - `<catalog>` 是您的目录名称  

要使用 CLI 创建 LoopBack API，请完成以下步骤：

1. 要创建项目，请打开命令行并输入：
  ```
  apic loopback
  ```
  {: codeblock}

2. 在随后的提示中，将要求您为应用程序命名。输入名称，然后按 **Enter** 键。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    工具将提示您输入要在其中创建项目的目录的名称。

    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. 按 **Enter** 键以使用先前输入的名称，或者输入新名称并按 **Enter** 键。工具将提示您选择要创建的应用程序的类型：
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 选择要使用的应用程序，然后按 **Enter** 键。工具在创建项目目录并向其添加多个目录和文件时，将显示多条消息。工具还将运行 `npm install` 以安装 `package.json` 中所指定的所有项目依赖项。此过程可能需要一些时间。

5. 需要确保当前工作目录为项目顶级目录，然后才能创建模型。为此，请输入以下命令：
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. 要创建模型，请输入以下命令：
    ```
    apic create --type model
    ```
    {: codeblock}

    工具将提示您输入模型的名称。



    ```
    ? Enter the model name:
    ```

7. 输入模型的名称。通常，可以在模型名称中使用任何字母数字字符以及连字符和下划线。这将列出您添加到项目的所有数据源，并且工具将提示您选择要使用的数据源：

    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. 选择要使用的数据源，然后按 **Enter** 键。工具将提示您选择模型的基类：

    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
有关每个选项的更多信息，请参阅[使用内置模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}。
9. 选择基类，然后按 **Enter** 键。工具将询问您是否要公开模型的 REST API。

```
? Expose branch via the REST API? (Y/n)
```
如果模型通过 REST 公开，那么可以通过 REST 端点使用所有标准的创建、读取、更新和删除操作。

10. 输入您的选择，然后按 **Enter** 键。如果您选择通过 REST 公开模型，那么工具会提示您输入模型名称的复数形式。
```
? Custom plural form (used to build REST URL):
```

11. 按 **Enter** 键，以使用复数的缺省标准英文规则。
工具将提示您选择是要创建仅服务器模型，还是创建可以同时在服务器和客户机 LoopBack&reg; API 中使用的通用模型。
```
? Common model or server only? (Use arrow keys)
```

12. 使用方向键进行选择，然后按 **Enter** 键。工具将提示您向模型添加属性：

```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. 输入属性名称。工具将提示您选择属性的数据类型：

```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. 选择字符串类型，然后按 **Enter** 键。工具将询问该属性是否为必需：

```
? Required? (y/N)
```

15. 输入 `y` 或 `n`，然后按 **Enter** 键。工具将提示您添加其他属性：

```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. 如果需要，请添加其他属性名称。如果不需要更多属性，请按 **Enter** 键以完成添加模型的过程。

缺省情况下，LoopBack&reg; 项目配置有内存中数据源，适用于开发和测试。但是，在某个时候，您会希望将模型连接到实际数据源，例如数据库服务器。要添加数据源，请完成以下步骤：

1. 输入以下命令：
```
apic create --type datasource
```
{: codeblock}
工具将提示您输入数据源的名称。

```
? Enter the data-source name:
```

2. 输入数据源的名称。可以在数据源名称中使用任何字母数字字符、连字符和下划线。工具将提示您选择要用于数据源的连接器：

```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. 使用方向键选择要使用的连接器，然后按 **Enter** 键。随后工具会将数据源添加到项目。

4. 输入主机、端口、用户、密码和数据库凭证。工具将提示您安装 LoopBack&reg; 连接器。
```
Install loopback-connector-<connector>?
```

5. 输入 `Yes`。工具将安装该连接器。

注：如果您已选择 Oracle 连接器，那么必须在 {{site.data.keyword.Bluemix_short}} 中设置环境变量，以便 Oracle 应用程序能够启动。为此，请完成以下步骤：

1. 在 {{site.data.keyword.Bluemix_short}} UI 中，选择**计算**。

2. 在“CF 应用程序”中，选择要使用的应用程序。

3. 单击**运行时**。

4. 选择**环境变量**。

5. 在“用户定义”部分中，单击**添加**。

6. 在**名称**字段中，输入 `LD_LIBRARY_PATH`。

7. 在**值**字段中，输入 `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`。

8. 单击**保存**。

### 测试 LoopBack 项目
{: #test_lb_proj}

要测试 LoopBack&reg; 项目，请完成以下步骤。

1. **可选**：确保当前工作目录为项目顶级目录。输入以下命令：
```
cd <loopback-project-dir>
```
其中，`<loopback-project-dir>` 是包含项目的目录的名称。
2. 输入以下命令：
```
apic start
```
这将在本地运行 LoopBack&reg; 项目 (API) 和 Micro Gateway。将显示以下消息：
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
其中：`<loopback-project>` 是包含项目的目录的名称。

例如，随后可以使用 `curl` 来测试任何 API 端点。如果要使用 Web 浏览器装入 API，请在浏览器中打开
`http://localhost:4001`。对于缺省 LoopBack&reg;（为空或为 hello-world）项目，将看到类似于以下内容的内容：
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### 通过 CLI 将 LoopBack 应用程序发布到 Bluemix
{: #pub_lb_app_cli}

要通过命令行将 LoopBack 应用程序发布到 {{site.data.keyword.Bluemix_short}}，请完成以下步骤：

1. 输入以下命令，以确保您处于 Loopback 项目目录。
```
cd <loopback-project-dir>
```
2. 输入以下命令以登录到 {{site.data.keyword.apiconnect_short}} 和 {{site.data.keyword.Bluemix_short}}。
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
其中：
  * `<username>` 是您的 {{site.data.keyword.apiconnect_short}} 组织标识。
  * `<password>` 是您的 {{site.data.keyword.apiconnect_short}} 密码。
3. 按空格键，以自动打开“**一次性密码**”浏览器页面。
4. 单击**重新生成**并复制一次性密码。
5. 回到 CLI，粘贴密码以完成登录。这将显示以下消息：
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. 输入以下命令：
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
其中：
  * `<region>` 是 {{site.data.keyword.Bluemix_short}} 区域。例如：
  * `eu`（如果使用的是 {{site.data.keyword.Bluemix_short}} 伦敦）。
  * `us`（如果使用的是 {{site.data.keyword.Bluemix_short}} 达拉斯）。
  * `au`（如果使用的是 {{site.data.keyword.Bluemix_short}} 悉尼）。

  如果您不确定，那么可以通过单击菜单栏中的 {{site.data.keyword.avatar}} 图标 <img src="images/i-avatar-icon.svg" alt="“头像”图标"/> 以打开“帐户和支持”窗口小部件并检查区域字段，从而找到您的区域。
7. 输入以下命令以将应用程序发布到 {{site.data.keyword.Bluemix_short}}。
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
其中：
  * `<app>` 是您的应用程序的名称
  * `<org>` 是您的 {{site.data.keyword.Bluemix_short}} 组织的名称
  * `<region>` 是 {{site.data.keyword.Bluemix_short}} 区域
这将返回以下输出：
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. 接下来，必须使用发布期间返回的值来修改产品定义。为此，请完成以下步骤：

    1. 在 API Designer UI 中，单击 **API**。
    2. 选择您的 API。
    3. 单击**组合**。
    4. 在组合件编辑器中，单击**过滤策略**图标。
    5. 选择 **DataPower Gateway 策略**。
    6. 双击**调用**。
    7. 使用在步骤 7 中检索到的值来更新以下字段。
        - **调用 URL**：插入 API 目标 URL。必须指定安全协议 HTTPS。例如：
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        如果您未记下此值，那么可以通过转至步骤 7 中返回的管理 URL 来进行检索。您还可以通过登录到 {{site.data.keyword.Bluemix_short}} 并查看应用程序信息来检索此值。
        - **TLS 概要文件**：插入 API 调用 tls-profile。例如：
        ```
        client:Loopback-client
        ```
    8. 单击**保存**以保存 API。

## 使用 API Designer 创建 LoopBack API
{: #create_lb_api_design}

以下过程描述了如何使用 API Designer 来创建 LoopBack&reg; API。
{:shortdesc}

### 先决条件
{: #prereq_create_lb_api_design}

**注**：以下指示信息假设您使用的是最新版本的开发者工具箱。要检查最新的版本，请参阅 [npm ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.npmjs.com/package/apiconnect){:new_window} 软件包页面。

首先，需要使用 CLI 创建 LoopBack&reg; 项目。为此，请完成以下步骤：

1. 要创建项目，请打开命令行并输入：
  ```
  apic loopback
  ```
  {: codeblock}

2. 在随后的提示中，将要求您为应用程序命名。输入名称，然后按 **Enter** 键。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    工具将提示您输入要在其中创建项目的目录的名称。

    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. 按 **Enter** 键以使用先前输入的名称，或者输入新名称并按 **Enter** 键。工具将提示您选择要创建的应用程序的类型：
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 选择要使用的应用程序，然后按 **Enter** 键。工具在创建项目目录并向其添加多个目录和文件时，将显示多条消息。工具还将运行 `npm install` 以安装 `package.json` 中所指定的所有项目依赖项。此过程可能需要一些时间。

5. 在创建模型之前，需要确保当前工作目录为项目顶级目录。为此，请输入以下命令：
```
cd <project directory name>
```

**注**：使当前工作目录成为项目顶级目录可确保在打开 API Designer 时，可以使用添加模型和数据源的选项。如果打开 API Designer 而不更改目录，那么将无法添加模型和数据源。


要打开 API Designer，请完成以下步骤：
1. 打开命令行并输入：
```
apic edit
```
在短暂停顿后，将显示以下消息。
```
    Express server listening on http://127.0.0.1:9000
    ```
    API Designer 将在缺省 Web 浏览器中打开。

2. 在登录页面中，输入您的 Bluemix&reg; 标识和密码。单击**登录**。

3. 单击**模型**。

4. 单击**添加**。这将打开“LoopBack&reg; **模型**”窗口。

5. 输入模型名称。通常，可以在模型名称中使用任何字母数字字符以及连字符和下划线。

6. 单击**新建**。

7. 在模型编辑器页面中，转至“属性”，然后单击**添加**。

8. 输入“属性名称”，然后选择“类型”。

9. 输入完模型的属性后，单击**保存**。

缺省情况下，空的 LoopBack&reg; 项目未定义任何数据源。要定义数据源，请完成以下步骤：
1. 单击**数据源**。

2. 单击**添加**图标。这将打开“新建 LoopBack&reg; **模型**”窗口。

3. 输入数据源名称。可以在数据源名称中使用任何字母数字字符、连字符和下划线。

4. 单击**新建**。该数据源会显示在数据源列表中，并且编辑器会使用新数据源的设置来更新 `server/datasources.json` 文件。

5. 单击数据源以查看其设置。

6. 将“连接器”设置更改为所需的连接器。

7. 返回到在其中启动了 API Designer 的控制台，然后通过输入以下命令来安装连接器：
```
npm install --save <connector-package>
```
其中，`<connector-package>` 是所选 LoopBack&reg; 连接器的 npm 软件包的名称。请参阅下表以获取连接器包的列表。

**注：**内存中和电子邮件连接器内置于 LoopBack&reg; 中，所以无需进行安装。

<table>
<caption>表 3. LoopBack 连接器</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">数据源</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">连接器包</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web Service</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web Service</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

有关更多信息，请参阅 [LoopBack 文档 - 构建连接器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://http://loopback.io//doc/en/lb3/Defining-data-sources.html){:new_window}。

**注：**如果您已选择 Oracle 连接器，那么必须在 {{site.data.keyword.Bluemix_short}} 中设置环境变量，以便 Oracle 应用程序能够启动。为此，请完成以下步骤：

1. 在 {{site.data.keyword.Bluemix_short}} UI 中，选择**计算**。

2. 在“CF 应用程序”中，选择要使用的应用程序。

3. 单击**运行时**。

4. 选择**环境变量**。

5. 在“用户定义”部分中，单击**添加**。

6. 在**名称**字段中，输入 `LD_LIBRARY_PATH`。

7. 在**值**字段中，输入 `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`。

8. 单击**保存**。

要测试 LoopBack&reg; 项目，请完成以下步骤：
1. 单击**启动服务器**图标。这将显示以下消息：
```
http://localhost:<4001/>Running
```
根据项目配置以及是否有其他进程在运行，可能会显示不同的端口号。

2. 单击 **localhost:4001** 以显示 API 根端点。对于缺省 LoopBack&reg;（为空或为 hello-world）项目，将看到类似于以下内容的内容：
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

接下来，需要创建产品。有关更多信息，请参阅[创建产品](managing_products.html#create_products)。
**提示**：无论何时启动新命令提示符，都要确保当前工作目录为项目顶级目录。为此，请输入以下命令：
```
cd <project directory name>
```

## 卸载开发者工具箱
{: #uninstall_dev_tk}

### 先决条件
{: #prereq_uninstall_dev_tk}

开始之前，必须通过输入以下命令来停止正在本地运行的所有应用程序：
```
apic stop --all
```

要卸载开发者工具箱，请请完成以下步骤：

1. 输入以下命令：
```
npm rm -g apiconnect
```
{: codeblock}

2. 清除 npm 高速缓存：
```
npm cache clean
```
{:codeblock}
  
如果使用的是 Windows：

3. 请删除 `C:\Users\username\AppData\Local\Temp` 中名称以 `npm-` 开头的所有文件
4. 删除目录 `<home_dir>\.apiconnect`，其中 `<home_dir>` 是先前安装了工具箱的用户帐户的主目录。

---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 建立 API
{: #creating_apis}

您可以透過下載 Developer Toolkit，以及使用指令行介面 (CLI) 或 API Designer，來建立 API。

## Developer Toolkit CLI
{: #dev_tk_cli_creating_apis notoc}

Developer Toolkit 提供可用來將 API 發佈至 {{site.data.keyword.apiconnect_long}} 的指令行介面。發佈 API 的方式是將它們包含在「產品」中，然後發佈「產品」。在本端檔案系統中建立及驗證 YAML 定義檔，以定義 API 及「產品」。您接著可以使用 Toolkit 指令，以與 {{site.data.keyword.apiconnect_long}} 互動。

## API Designer
{: #designer_creating_apis notoc}

API Designer 是 Developer Toolkit 內的離線圖形使用者介面，並提供建立及配置 API 的功能。API Designer 的執行方式是使用指令行介面中的 edit 指令。使用 edit 指令時，會在您的預設瀏覽器中開啟 API Designer，而且可以透過執行指令時顯示的本端主機埠進行存取。

## 安裝 Developer Toolkit
{: #install_dev_tk_creating_apis}

### 必要條件
{: #prereq_install_dev_tk_creating_apis}

開始之前，您必須在要使用 Toolkit 的機器上安裝 [Node.js ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://nodejs.org/en/){: #new_window}，並確定 `node` 在您的 `PATH` 中。

當您安裝 Developer Toolkit 時，會安裝下列項目。

- {{site.data.keyword.apiconnect_short}} 指令行工具
- {{site.data.keyword.apiconnect_short}} 圖形編輯器
- 本端 {{site.data.keyword.apiconnect_short}} 微型閘道


1. 若要安裝 Toolkit，請以管理者身分開啟命令提示字元，然後輸入下列指令。

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **附註：**在安裝期間，您可能會看到來自 `node-gyp` 模組的錯誤。這些錯誤是來自於選用性的相依關係，安裝將順利完成。

2. 若要檢視所有 Toolkit 指令的摘要用法說明，請輸入下列指令：

    ```
    apic
    ```
	{: codeblock}

3. 若要檢視任何指令的用法說明，請使用 `--help` 選項。例如：

    ```
    apic validate --help
    ```
	{: codeblock}
	
## 安裝 LoopBack 連接器
{: #install_lb_conn_creating_apis}

您必須先安裝資料來源連接器，才能使用 LoopBack 資料來源存取後端系統的資料，例如資料庫。記憶體內及電子郵件連接器都已內建到 LoopBack，因此您不需要安裝。

### 必要條件
{: #prereq_install_lb_conn_creating_apis}

Oracle、DB2 及 SQLLite 連接器需要 C 編譯器工具才能建置及安裝二進位延伸。確切的需求視您的作業系統而定，如下列清單中所說明。

**Linux**
- Python 2.7 版（不支援 3.x 版）

- <code>make</code>

- C/C++ 編譯器工具鏈，例如 GCC 4.2 版或更新版本。

- 在 Debian 及 Debian 衍生的發行套件（Ubuntu、Mint 等）上，使用下列指令：
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>

**Mac OS X**
- [適用於 Mac OS X 的版本 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.python.org/downloads/mac-osx/){: #new_window}

- [Xcode ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716){: #new_window}

**Windows**
- [Microsoft .NET Framework 4 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.microsoft.com/en-us/download/details.aspx?id=17851){: #new_window}

- [Visual Studio ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.visualstudio.com/downloads/download-visual-studio-vs){: #new_window}

- [Python v2.7.10 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.python.org/downloads/release/python-2710/){: #new_window}

- [Microsoft Windows SDK for Windows 7 ![外部鏈結圖示External link icon](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279){: #new_window}

- npm 第 3 版：請參閱附註。

**附註**：除非您要購買 Visual Studio Enterprise，否則請使用 Visual Studio Community。請執行安裝程式、勾選「程式設計語言」下的 "Visual C++"，然後接受預設安裝位置。

針對 64 位元建置的 Node.js 及原生模組，您還需要 Windows&trade; 7 64 位元 SDK。如果安裝失敗，請嘗試解除安裝您已先安裝的所有 C++ 2010 x64&amp;x86 可轉散發套件。如果您收到未安裝 64 位元編譯器的錯誤，則可能還需要 Windows&trade; SDK 7.1 的編譯器更新。

輸入下列指令以安裝 npm 第 3 版：
  ```
  npm install -g npm
  ```
  {: codeblock}
  然後確定 npm 指令使用正確的版本：
  ```
  npm -v
  ```
  {: codeblock}
  如果顯示的版本不是 3.x.x，則請編輯您的系統 PATH，確定 `C:\Users\username\AppData\Roaming\npm` 在任何其他項目之前。





1. **選用**：如果您使用 API Designer，請開啟新的 Shell 視窗。

2. 當您已安裝作業系統所需的編譯器工具時，請在專案根目錄輸入下列指令安裝連接器。

```
npm install --save <connector-package>
```
{: codeblock}
其中 `<connector-package>` 是 LoopBack 連接器的 npm 套件名稱，如表 1 中所示：

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>表 1. LoopBack 連接器</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">資料來源</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">連接器套件</th>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web 服務</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web 服務</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>


## 使用 CLI 建立 LoopBack API
{: #create_lb_api_creating_apis}

下列程序說明如何使用指令行介面來建立 LoopBack&reg; API。


### 必要條件
{: #prereq_create_lb_api_creating_apis}

開始之前，請備妥您要使用的型錄的型錄 ID。若要取得型錄 ID，請完成下列步驟：  

1. 移至 {{site.data.keyword.apiconnect_short}} **儀表板**。

2. 針對您想要使用的型錄，按一下**顯示型錄 ID** 圖示 <img alt="顯示型錄 ID 的鏈結圖示" src="images/chain_link_icon.png">。

3. 複製型錄 ID。例如：  
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
其中：


    - `<region>` 是 {{site.data.keyword.Bluemix_notm}} 地區。

    - `<username_string>` 是不含任何符號的 {{site.data.keyword.Bluemix_notm}} 組織 ID。例如 `joe@mycompany.com` 將是 `joemycompanycom`

    - `<catalog>` 是您的型錄名稱  

若要使用 CLI 來建立 LoopBack API，請完成下列步驟：

1. 若要建立專案，請開啟指令行，然後輸入：
  ```
  apic loopback
  ```
  {: codeblock}

2. 在後面的提示中，系統會要求您命名您的應用程式。請鍵入名稱，然後按 **Enter** 鍵。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    此工具會提示您輸入要在其中建立專案的目錄名稱。
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. 按 **Enter** 鍵使用您先前輸入的名稱，或鍵入新名稱，然後按 **Enter** 鍵。此工具會提示您選取要建立的應用程式類型：
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 選取您要使用的應用程式，然後按 **Enter** 鍵。此工具會在建立專案目錄並在其中新增一些目錄及檔案時顯示一些訊息。它也會執行 `npm install` 來安裝所有專案相依關係（如 `package.json` 中所指定）。此處理程序可能需要一些時間。

5. 建立模型之前，需要確定您的現行工作目錄是專案最上層目錄。若要這麼做，請輸入下列指令：
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. 若要建立模型，請輸入下列指令：
    ```
    apic create --type model
    ```
    {: codeblock}

    此工具會提示您輸入模型名稱。

    ```
    ? Enter the model name:
    ```

7. 輸入模型的名稱。一般而言，您可以在模型名稱中使用任何英數字元以及橫線和底線。會列出您已新增至專案的所有資料來源，而且此工具會提示您選取要使用的資料來源：
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. 選取您要使用的資料來源，然後按 **Enter** 鍵。此工具會提示您選取模型的基礎類別：
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
如需每一個選項的相關資訊，請參閱[使用內建模型 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){: #new_window}。

9. 選取基礎類別，然後按 **Enter** 鍵。此工具會詢問您是否要公開模型的 REST API。
```
? Expose branch via the REST API? (Y/n)
```
如果透過 REST 公開模型，則可以透過 REST 端點進行所有標準建立、讀取、更新及刪除作業。

10. 輸入您的選擇，然後按 **Enter** 鍵。如果您選擇透過 REST 公開模型，此工具會提示您輸入模型名稱的複數形式。
```
? Custom plural form (used to build REST URL):
```

11. 按 **Enter** 鍵，以使用適用於複數化的預設標準英文規則。此工具會提示您是要建立僅伺服器模型，還是可在伺服器或用戶端 LoopBack; API 兩者中使用的一般模型。
```
? Common model or server only? (Use arrow keys)
```

12. 使用方向鍵進行您的選擇，然後按 **Enter** 鍵。此工具會提示您將內容新增至模型：
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. 輸入內容名稱。此工具會提示您選取內容的資料類型：
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

14. 選取字串類型，然後按 **Enter** 鍵。此工具會詢問此內容是否為必要項目：
```
? Required? (y/N)
```

15. 鍵入 `y` 或 `n`，然後按 **Enter** 鍵。此工具會提示您新增另一個內容：
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. 視需要新增另一個內容名稱。如果您不需要任何其他內容，請按 **Enter** 鍵來完成新增模型。

依預設，LoopBack; 專案已配置適用於開發與測試的記憶體內資料來源。不過，您有時會想要將模型連接至實際資料來源（例如資料庫伺服器）。請完成下列步驟，以新增資料來源：

1. 輸入下列指令：
```
apic create --type datasource
```
{: codeblock}
此工具會提示您輸入資料來源名稱。
```
? Enter the data-source name:
```

2. 輸入資料來源的名稱。您可以在資料來源名稱中使用任何英數字元、橫線及底線。此工具會提示您選取要用於資料來源的連接器：
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

3. 使用方向鍵來選取您要使用的連接器，然後按 **Enter** 鍵。此工具接著會將資料來源新增至專案。

4. 輸入您的主機、埠、使用者、密碼及資料庫認證。此工具會提示您安裝 LoopBack 連接器。
```
Install loopback-connector-<connector>?
```

5. 鍵入 `Yes`。此工具即會安裝連接器。

**附註**：如果您已選取 Oracle 連接器，則必須在 {{site.data.keyword.Bluemix_notm}} 中設定環境變數，Oracle 應用程式才會啟動。若要執行此作業，請完成下列步驟：

1. 在 {{site.data.keyword.Bluemix_notm}} 使用者介面中，選取**運算**。

2. 在 CF 應用程式中，選取您要使用的應用程式。

3. 按一下**運行環境**。

4. 選取**環境變數**。

5. 在「使用者定義」區段中，按一下**新增**。

6. 在**名稱**欄位中，輸入 `LD_LIBRARY_PATH`。

7. 在**值**欄位中，輸入 `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`。

8. 按一下**儲存**。

### 測試 LoopBack 專案
{: #test_lb_proj_creating_apis}

若要測試 LoopBack 專案，請完成下列步驟。

1. **選用**：確定您的現行工作目錄是專案最上層目錄。輸入下列指令：
```
cd <loopback-project-dir>
```
其中 `<loopback-project-dir>` 是包含專案的目錄名稱。
2. 輸入下列指令：
```
apic start
```
這會在本端執行 LoopBack 專案 (API) 及「微型閘道」。會顯示下列訊息：
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
其中：`<loopback-project>` 是包含專案的目錄名稱。


例如，您接著可以使用 `curl` 來測試任何 API 端點。如果您要使用 Web 瀏覽器來載入 API，請在瀏覽器中開啟 `http://localhost:4001`。針對預設 LoopBack（空的或 hello-world）專案，您會看到與下列類似的內容：

```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### 從 CLI 將 LoopBack 應用程式發佈至 {{site.data.keyword.Bluemix_notm}}
{: #pub_lb_app_cli_creating_apis}

若要從指令行將 LoopBack 應用程式發佈至 {{site.data.keyword.Bluemix_short}}，請完成下列步驟。

1. 輸入下列指令，以確保您位在 Loopback 專案目錄中。
```
cd <loopback-project-dir>
```
2. 輸入下列指令，以登入 {{site.data.keyword.apiconnect_short}} 及 {{site.data.keyword.Bluemix_notm}}。
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
其中：
  * `<username>` 是您的 {{site.data.keyword.apiconnect_short}} 組織 ID。
  * `<password>` 是您的 {{site.data.keyword.apiconnect_short}} 密碼。
3. 按空格鍵，以自動開啟「**一次性密碼**」瀏覽器頁面。
4. 按一下**重新產生**，然後複製一次性密碼。
5. 回到 CLI，貼上密碼以完成登入。下列是顯示的訊息：
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. 輸入下列指令：
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
其中：
  * `<region>` 是 {{site.data.keyword.Bluemix_notm}} 地區。例如：
  * 如果您是使用 {{site.data.keyword.Bluemix_notm}} 倫敦，則為 `eu`。
  * 如果您是使用 {{site.data.keyword.Bluemix_notm}} 達拉斯，則為 `us`。
  * 如果您是使用 {{site.data.keyword.Bluemix_notm}} 雪梨，則為 `au`。

  如果不確定，您可以尋找所在地區，方法為按一下功能表列中的「{{site.data.keyword.avatar}}」圖示 <img src="images/i-avatar-icon.svg" alt="虛擬人像圖示"/>，以開啟「帳戶及支援」小組件並檢查地區欄位。
7. 輸入下列指令，以將您的應用程式發佈至 {{site.data.keyword.Bluemix_notm}}。
```
apic apps:publish –app <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
其中：
  * `<app>` 是您的應用程式名稱
  * `<org>` 是您的 {{site.data.keyword.Bluemix_notm}} 組織名稱
  * `<region>` 是 {{site.data.keyword.Bluemix_notm}} 地區。傳回下列輸出：
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. 接下來，您必須使用發佈期間所傳回的值來修改「產品」定義。若要這麼做，請完成下列步驟：

    1. 在 API Designer 使用者介面中，按一下 **API**。
    2. 選取您的 API。
    3. 按一下**組合**。
    4. 在「組合」編輯器中，按一下**過濾器原則**圖示。
    5. 選取 **DataPower Gateway 原則**。
    6. 按兩下 **invoke**。
    7. 使用您在步驟 7 所擷取的值，來更新下列欄位。
        - **呼叫 URL**：插入 API 目標 URL。您必須指定安全通訊協定 HTTPS。例如：
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        如果您未記下這個值，可以移至步驟 7 所傳回的管理 URL 來進行擷取。您也可以透過登入 {{site.data.keyword.Bluemix_notm}} 並檢視應用程式資訊來進行擷取。
        - **TLS 設定檔**：插入 API invoke tls-profile。例如：
        ```
        client:Loopback-client
        ```
    8. 按一下**儲存**，以儲存 API。

## 使用 API Designer 建立 LoopBack API
{: #create_lb_api_design_creating_apis}

下列程序說明如何使用 API Designer 來建立 LoopBack API。
{:shortdesc}

### 必要條件
{: #prereq_create_lb_api_design_creating_apis}

**附註**：下列指示假設您使用的是最新版的 Developer Toolkit。若要檢查最新版本，請參閱 [npm ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.npmjs.com/package/apiconnect){: #new_window} 套件頁面。

首先，您需要使用 CLI 來建立 LoopBack 專案。若要這麼做，請完成下列步驟：

1. 若要建立專案，請開啟指令行，然後輸入：
  ```
  apic loopback
  ```
  {: codeblock}

2. 在後面的提示中，系統會要求您命名您的應用程式。請鍵入名稱，然後按 **Enter** 鍵。
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    此工具會提示您輸入要在其中建立專案的目錄名稱。
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. 按 **Enter** 鍵使用您先前輸入的名稱，或鍵入新名稱，然後按 **Enter** 鍵。此工具會提示您選取要建立的應用程式類型：
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 選取您要使用的應用程式，然後按 **Enter** 鍵。此工具會在建立專案目錄並在其中新增一些目錄及檔案時顯示一些訊息。它也會執行 `npm install` 來安裝所有專案相依關係（如 `package.json` 中所指定）。此處理程序可能需要一些時間。

5. 建立模型之前，您需要確定您的現行工作目錄是專案最上層目錄。若要這麼做，請輸入下列指令：
```
cd <project directory name>
```

**附註**：讓您的現行工作目錄成為專案最上層目錄，將確保在您開啟 API Designer 時，可以使用新增模型及資料來源的選項。如果您開啟 API Designer 且未變更目錄，將無法新增模型及資料來源。

若要開啟 API Designer，請完成下列步驟：
1. 開啟指令行，然後輸入：
```
apic edit
```
    短暫暫停之後，會顯示下列訊息。
    ```
        Express server listening on http://127.0.0.1:9000
    ```
    即會在預設 Web 瀏覽器中開啟 API Designer。

2. 在登入頁面中，輸入您的 {{site.data.keyword.Bluemix_notm}} ID 及密碼。按一下**登入**。

3. 按一下**模型**。

4. 按一下**新增**。即會開啟「LoopBack **模型**」視窗。

5. 輸入模型名稱。一般而言，您可以在模型名稱中使用任何英數字元以及橫線和底線。

6. 按一下**新建**。

7. 在模型編輯器頁面中，移至「內容」，然後按一下**新增**。

8. 輸入「內容名稱」，然後選取一個「類型」。

9. 完成輸入模型的「內容」時，請按一下**儲存**。

依預設，空的 LoopBack 專案未定義任何資料來源。若要定義資料來源，請完成下列步驟：
1. 按一下**資料來源**。

2. 按一下**新增**圖示。即會開啟「新建 LoopBack **模型**」視窗。

3. 輸入資料來源名稱。您可以在資料來源名稱中使用任何英數字元、橫線及底線。

4. 按一下**新建**。資料來源即會出現在資料來源清單中，而且編輯器會使用新資料來源的設定來更新 `server/datasources.json` 檔案。

5. 按一下資料來源，以檢視其設定。

6. 將「連接器」設定變更為您需要的連接器。

7. 回到您啟動 API Designer 用的主控台，然後輸入下列指令來安裝「連接器」：
```
npm install --save <connector-package>
```
    其中 `<connector-package>` 是所選取 LoopBack 連線器的 npm 套件名稱。如需連接器套件的清單，請參閱下表。

**附註：**記憶體內及電子郵件連接器都已內建到 LoopBack，因此您不需要安裝它們。

<table>
<caption>表 2. LoopBack 連接器</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">資料來源</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">連接器套件</th>
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
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP Web 服務</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST Web 服務</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

如需相關資訊，請參閱 [LoopBack 文件 - 建置連接器 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://loopback.io/doc/en/lb3/Defining-data-sources.html){: #new_window}。

**附註：**如果您已選取 Oracle 連接器，則必須在 {{site.data.keyword.Bluemix_notm}} 中設定環境變數，Oracle 應用程式才會啟動。若要執行此作業，請完成下列步驟：

1. 在 {{site.data.keyword.Bluemix_notm}} 使用者介面中，選取**運算**。

2. 在 CF 應用程式中，選取您要使用的應用程式。

3. 按一下**運行環境**。

4. 選取**環境變數**。

5. 在「使用者定義」區段中，按一下**新增**。

6. 在**名稱**欄位中，輸入 `LD_LIBRARY_PATH`。

7. 在**值**欄位中，輸入 `$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`。

8. 按一下**儲存**。

若要測試 LoopBack 專案，請完成下列步驟：
1. 按一下**啟動伺服器**圖示。下列是顯示的訊息：
```
http://localhost:<4001/>Running
```
根據您的專案配置以及是否執行其他處理程序，可能會顯示不同的埠號。

2. 按一下 **localhost:4001**，以顯示 API root 端點。針對預設 LoopBack（空的或 hello-world）專案，您會看到與下列類似的內容：
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

接下來，您需要建立「產品」。如需相關資訊，請參閱[建立產品](/docs/services/apiconnect?topic=apiconnect-managing_products#create_product_managing_products)。
**提示**：每次啟動新的命令提示字元時，請確定您的現行工作目錄是專案最上層目錄。若要這麼做，請輸入下列指令：
```
cd <project directory name>
```

## 解除安裝 Developer Toolkit
{: #uninstall_dev_tk_creating_apis}

### 必要條件
{: #prereq_uninstall_dev_tk_creating_apis}

開始之前，您必須輸入下列指令來停止任何在本端執行的應用程式：
```
apic stop --all
```

若要解除安裝 Developer Toolkit，請完成下列步驟：

1. 輸入下列指令：
```
npm rm -g apiconnect
```
{: codeblock}

2. 清除您的 npm 快取：
```
npm cache clean
```
{:codeblock}
  
如果您是使用 Windows，請執行下列動作：

3. 刪除 `C:\Users\username\AppData\Local\Temp` 中名稱開頭為 `npm-` 的所有檔案
4. 刪除目錄 `<home_dir>\.apiconnect`，其中 `<home_dir>` 是先前安裝 Toolkit 的使用者帳戶的起始目錄。

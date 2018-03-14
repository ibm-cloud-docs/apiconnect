---

copyright:
  years: 2017
lastupdated: "2017-11-28"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 在 Node.js 中建立 API

**持續時間**：20 分鐘  
**技能水準**：初學者  

---
## 目標

本指導教學會引導您使用 LoopBack 架構在 Node.js 中建立 API。本指導教學說明如何進行下列作業：
1. 建立新的 LoopBack 專案。
2. 使用 {{site.data.keyword.apiconnect_full}} Toolkit 中的 API Designer，將新的資料來源及模型新增至 LoopBack 專案。
3. 使用 API Designer「探索」工具來測試 API 端點。

---
## 必要條件

開始之前，請[安裝 {{site.data.keyword.apiconnect_short}} Toolkit](tut_prereq_install_toolkit.html)。如果已經安裝工具箱，請確定您執行的是 5.0.8.1 版或更新版本。您可以在指令行上輸入下列指令來進行此驗證：
	```
	apic -v
	```

---
## 建立 Loopback 專案

您可以使用 {{site.data.keyword.apiconnect_short}} Developer Toolkit 指令行介面或 API Designer 介面來建立 Loopback 專案。 
 
### 使用 Toolkit 指令行來建立 LoopBack 專案

若要使用 {{site.data.keyword.apiconnect_short}} Toolkit 指令行來建立 LoopBack 專案，請完成下列步驟：
1.  從指令行介面中，輸入下列指令。它用來建立及管理 LoopBack 應用程式。
	```bash 
	apic loopback
	```
	>![info]
	>在本指導教學中，您將建立稱為 weather-data 的專案。
2.  在提示中，輸入 `weather data` 作為專案名稱，然後按 **Enter** 鍵。
	```bash
	? What's the name of your application? weather-data
	```
  	>![important]
  	>一般而言，專案名稱可以包含任何字元，但空格 (" ")、正斜線 ("/")、＆ 符號 ("&")、at 符號 ("@")、加號 ("+")、百分比 ("%") 和冒號 (":") 除外。
3.  輸入要在其中建立專案的目錄名稱。按 **Enter** 鍵以使用與專案同名的目錄，或鍵入新名稱並按 **Enter** 鍵。
	```bash
	? Enter name of the directory to contain the project: weather-data
	```
4.  選取要使用的 LoopBack 版本。選擇現行正式作業版本：3.x。
	```bash
	? Which version of LoopBack would you like to use? 
  	2.x (long term support) 
	? 3.x (current) 
	```
5.  使用方向鍵來選取 **empty-server**，指定您要建立的應用程式類型。
	```bash
	? What kind of application do you have in mind? (Use arrow keys)
	? empty-server (An empty LoopBack API, without any configured models or datasources) 
  	hello-world (A project containing a basic working example, including a memory database) 
  	notes (A project containing a basic working example, including a memory database)
	```
6.  按 **Enter** 鍵，以建立空的 LoopBack API。 

此工具會在建立專案目錄並在其中新增一些目錄及檔案時顯示一些訊息。它也會執行 npm install 來安裝所有專案相依關係（如 package.json 中所指定）。此處理程序會建立 node_modules 目錄，可能需要一些時間。

空的 LoopBack 專案包含下列目錄：
- server：包含伺服器模型和資料來源定義，以及其他伺服器程式碼
- definitions：包含 YAML 定義檔
- node_modules：由 node.js 建立


### 使用 API Designer 介面來建立 LoopBack 專案

若要使用 API Designer 來建立 LoopBack 專案，請完成下列步驟：
1.  從指令行介面中，輸入下列指令來啟動 API Designer：
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	>![info]
	>上述指令會起始設定 {{site.data.keyword.apiconnect_short}} 工具箱，並在完成時使用預設瀏覽器啟動 API Designer。
	>![info]
	>在本指導教學中，您將建立稱為 weather-data 的專案。
2.  如果您先前未固定使用者介面導覽窗格，請按一下「導覽至」圖示 ![](images/navigate-to.png)。即會開啟 API Manager 使用者介面導覽窗格。若要固定使用者介面導覽窗格，請按一下「固定」功能表圖示 ![](images/pinned.png)。
3.  在資訊看板中，按一下「專案」的「加號」圖示 ![](images/add-icon.png)。
4.  按一下**建立 LoopBack 專案**。您將看到**新增 LoopBack 專案**對話框。
5.  選取 **empty-server** 作為專案範本。
6.  針對 **LoopBack 版本**，選取 3.x 版（現行版本）。
7.  在「顯示名稱」及「名稱」欄位中，輸入 `weather-data`。
8.  針對**專案目錄**，按一下**瀏覽**按鈕 ![](images/api-designer-2.png)，以選取步驟 1 中建立的 `weather-data` 資料夾。
9. 按一下**新增**，以新增專案。
	>![info]
	>**新增 LoopBack 專案**視窗中將會在建立專案目錄並在其中新增一些目錄及檔案時顯示一些訊息。它也會執行 npm install 來安裝所有專案相依關係（如 package.json 中所指定）。此處理程序會建立 node_modules 目錄，可能需要一些時間。
	
	>空的 LoopBack 專案包含下列目錄：
	- server：包含伺服器模型和資料來源定義，以及其他伺服器程式碼
	- definitions：包含 YAML 定義檔
	- node_modules：由 node.js 建立
10. 按一下**已完成**，關閉**新增 LoopBack 專案**對話框。
11. 結束 **API Designer**，方法是回到步驟 1 中的指令行，並輸入 `Ctrl+C`。鍵入 `Y`，確認結束。
12. 關閉瀏覽器階段作業。

---
## 新增資料來源及模型

若要使用 API Designer 將新的模型及資料來源新增至 LoopBack 專案，請完成下列步驟：

### 新增資料來源
若要使用 API Designer 將新的資料來源新增至 LoopBack 專案，請完成下列步驟。
1. 您也必須建立 LoopBack 專案（"weather-data" 專案）（如`從指令行建立 LoopBack 專案`所述），並確定現行工作目錄是專案根目錄：
	```bash
	cd weather-data
	```
2. 從指令行中，輸入下列指令：
	```bash
	apic edit
	```
	短暫暫停之後，主控台會顯示以下訊息：
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	即會在預設 Web 瀏覽器中開啟 API Designer，如果您最近沒有登入，則一開始會顯示登入頁面。  
	>![info]
	>您可以使用 {{site.data.keyword.Bluemix}} 帳戶登入，或建立一個帳戶。
3. 按一下**資料來源**圖示 ![](images/datasource-icon.png)。
4. 按一下**新增**。即會開啟「新建 LoopBack 資料來源」視窗。
5. 在**名稱**文字欄位中，輸入 `weatherDS`。
	>![info]
	>您可以在資料來源名稱中使用任何英數字元、橫線及底線。
6. 按一下**新建**。
7. 依預設，**連接器**設定會顯示 **In-memory db**，其他設定則為空白。保留現在的預設值，API Designer 會自動儲存新的資料來源。
	>![info]
	>記憶體內資料來源建置於 LoopBack 中，並且只適用於開發及起始測試。當您準備好將模型連接至實際資料來源（例如資料庫伺服器）時，請相應地變更**連接器**設定，並遵循[安裝 LoopBack 連接器 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv){:new_window} 中的指示來安裝資料來源連接器。在「連接器類型」中，視情況輸入連接器設定（主機名稱、埠、資料庫名稱、使用者名稱、密碼），然後按一下**儲存**圖示 ![](images/save-icon.png)。API Designer 會自動測試與資料來源的連線。如果測試成功，則會顯示此訊息：**成功 - 資料來源連線測試成功**。
8. 按一下「測試連線」圖示 ![](images/db-test-icon.png)，測試資料來源連線。即會顯示此訊息：「資料來源連線測試成功」。
9. 按一下**所有資料來源**。資料來源將會出現在資料來源清單中，而且編輯器會將 server/datasources.json 檔案更新為新資料來源的設定。

### 新增模型

若要使用 API Designer 將新的模型新增至 LoopBack 專案，請完成下列步驟：
1. 按一下**模型**圖示 ![](images/models-icon.png)。
2. 按一下**新增**。即會開啟「新建 LoopBack 模型」視窗。
3. 在**名稱**文字欄位中，輸入 `weather`，然後按一下**新建**。
4. 在**資料來源**欄位中，選取 **weatherDS**。![](images/new-model-1.png)
5. 在**內容**中，按一下**新增內容**圖示 ![](images/add-icon.png)。
6. 在**內容名稱**文字欄位中，輸入 `zip_code`。
7. 在**類型**中，選取 **number**。
8. 選取**必要**，將內容設為必要項目。這表示在您新增或更新模型實例時，它必須要有值。 
9. 選取 **ID** 以確定內容具有唯一 ID。現在，會保留其他設定的預設值：
	- **是陣列**：內容是否為具有已指定類型之元素的 JavaScript 陣列。
	- **索引**：內容是否代表作為資料庫索引的直欄（欄位）。
	- **說明**：內容的文字說明。
9. 再按一下**新增內容**圖示 ![](images/add-icon.png)，新增另一個內容。請參照下表來完成其餘內容：
	![](images/new-model-property-1.png)
10. 按一下**儲存**圖示 ![](images/save-icon.png)，儲存變更。
11. 按一下**所有模型**，完成模型的編輯。

這會完成將新的資料來源及模型新增至 weather-data LoopBack 專案。

---

## 測試 LoopBack 專案

>![info]
	>如果您在完成「新增模型及資料來源」小節之後未結束 {{site.data.keyword.apiconnect_short}} 設計程式，則可以直接移至下面的步驟 2。
	
若要使用 API Designer「探索」工具來測試 API 端點，請完成下列步驟：
1. 從指令行中，輸入下列指令：
	```bash
	apic edit
	```
	短暫暫停之後，主控台會顯示以下訊息：
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	即會在預設 Web 瀏覽器中開啟 API Designer，如果您最近沒有登入，則一開始會顯示登入頁面。
	
2. 啟動本端測試伺服器。
	a. 在畫面底端的測試主控台中，按一下**啟動伺服器**圖示 ![](images/test-icon.png)：
	![](images/start-server-1.png)
	b. 等待顯示「執行中」訊息：
	![](images/running-server-1.png)

	>![info]
	>根據您的專案配置以及是否執行其他處理程序，可能會顯示不同的埠號。
3. 按一下 **http://127.0.0.1:port_number**，以顯示 API 根端點。針對預設 LoopBack（空的或 hello-world）專案，您將看到與下列類似的內容：
	```bash
	{"started":"2017-05-24T19:21:47.807Z","uptime":80.876}
	```
	>![info]
	>若要停止專案，請按一下**停止伺服器**圖示 ![](images/stop-icon.png)：
	>![](images/stop-server-1.png)
	
	>若要將它重新啟動，請按一下**重新啟動伺服器**圖示 ![](images/restart-icon.png)：
	>![](images/restart-server-1.png)
	
4. 按一下**探索**圖示 ![](images/explore-icon.png)，以查看 API Designer「探索」工具。資訊看板會顯示 API 中 LoopBack 模型的所有 REST 作業。依預設，基於 PersistedModel 的模型具有[一組標準的建立、讀取、更新及刪除作業 ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](http://loopback.io/doc/en/lb2/PersistedModel-REST-API){:new_window}。

5. 在左窗格中按一下 **weather.create** 作業，以顯示端點。
![](images/explore-test-1.png)
中心窗格會顯示有關端點的摘要資訊，其中包括其參數、安全、模型實例資料及回應碼。右窗格提供使用 curl 指令呼叫端點的範本程式碼，以及 Ruby、Python、Java 及 Node 這類語言。

6. 若要在 API Designer「探索」工具中測試 REST 端點，請完成下列步驟：
    1. 在右窗格上，按一下**試用**。 
	
	2. 向下捲動至**參數**，然後按一下**產生**以產生一些虛擬資料。依預設，產生的資料包括 `zip_code`、`current_temperature`、`current_humidity`、`tonight_temperature_low`、`tonight_temperature_high`、`tonight_humidity_low`，以及 `tonight_humidity_high` 內容。
	
	3. 按一下**呼叫作業**。![](images/explore-test-2.png)
	
>![troubleshooting]
>如果您看到由於 localhost 的未受信任憑證而發出的錯誤訊息，請按一下 API Designer「探索」工具的錯誤訊息中所提供的鏈結來接受憑證，然後繼續在 Web 瀏覽器中呼叫作業。確切的程序取決於您使用的 Web 瀏覽器。如果您直接在瀏覽器中載入 REST 端點，則會看到此訊息：{"name":"PreFlowError","message":"無法處理要求"}。您必須使用 API Designer「探索」工具在瀏覽器中測試 REST 端點，因為它包括必要的標頭及其他要求參數。
>
>![troubleshooting]
>如果您收到回應碼 **422 - 無法處理的實體**與下列有效負載：
>![](images/explore-test-3.png)
>
>確定沒有尚未從產生的資料移除的 `id` 資料元素。如果有 ID 元素，請移除該元素然後重新執行測試。
>![troubleshooting]
>如果您收到**無法剖析要求內文**錯誤，則必須移除最後一個 `humidity_high` 數字後面的逗點。
7. 編輯 **data** 區段中顯示的 JSON 值。請嘗試變更產生的虛擬資料，然後再按一下**呼叫作業**。您應該會看到要求和回應參數，以及您所輸入的 JSON 實例資料。
![](images/explore-test-4.png)

8. 若要確認作業已新增模型實例，請按一下 **weather.find**。按一下**呼叫作業**，以顯示所有天氣實例。例如（具有兩個模型實例）：

	![](images/explore-test-5.png)
---

### 您在本指導教學中達成的作業
在本指導教學中，您已完成下列作業：
1. 使用 {{site.data.keyword.apiconnect_short}} Toolkit 指令行建立新的 LoopBack 專案。
2. 使用 {{site.data.keyword.apiconnect_short}} Toolkit 中的 API Designer，將新的模型及資料來源新增至 LoopBack 專案。
3. 使用 API Designer「探索」工具測試 API 端點。


---

## 下一步

[管理 REST 服務](tut_rest_landing.html)或[管理 SOAP 服務](tut_manage_soap_api.html)。

建立 > **管理** > 安全 > 社交化 > 分析

 
[important]: ./images/important.png "重要事項！"
[info]: ./images/info.png "資訊"
[troubleshooting]: ./images/troubleshooting.png "疑難排解" 


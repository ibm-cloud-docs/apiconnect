---

copyright:
  years: 2017
lastupdated: "2017-12-15"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 從基本分析瞭解
{: #tut_insights_analytics}

持續時間：30 分鐘  
技能水準：初學者

## 目標
{: #object_tut_insights_analytics}

這是 {{site.data.keyword.apiconnect_full}} 中 API 分析的基本簡介。我們將導覽可用的分析儀表板，而且您可以追蹤自己的 API。


## 必要條件
{: #prereq_tut_insights_analytics}

為了能夠檢視您自己的 API 分析，您必須已建立及發佈「API 產品」。此外，您還需要多次呼叫 API 來產生一些分析資料，最好是使用已登錄應用程式中的用戶端 ID（而不是預先佈建的測試應用程式）。

為了在本指導教學中產生資料，我們已使用 Postman 的*集合執行器* 多次呼叫 API（使用不同的資料及用戶端 ID）。您可以使用類似的工具（例如 HttpRequester for Firefox），或只是使用 cURL 從指令行多次呼叫 API。您可以按一下 {{site.data.keyword.apiconnect_short}} 中的**探索**鏈結，來取得 API 的範例要求。

## 型錄分析簡介
{: #intro_tut_insights_analytics}

身為 API 擁有者，您需要一種用來評量所提供之 API 的成功及效能的方式。您要進行分析的主要位置是在型錄層次。如果您尚未引進型錄，請參閱 IBM Knowledge Center 中的[使用型錄 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/conref_working_with_env.html){: #new_window}，以取得簡介。 

您及應用程式開發人員也可以在「開發人員入口網站」中存取應用程式特定分析，但我們將焦點放在本指導教學中的「型錄分析」。

您最多可以存取 90 天有關 API 以及發佈至該型錄之「產品」的即時和歷程資訊。它也會顯示誰正在呼叫它們。如果型錄具有多個空間，您可以導覽至「空間」層次。

本指導教學包含四個活動，顯示如何完成下列作業：
* 檢視分析
* 檢視事件記錄詳細資料
* 建置新的儀表板
* 建立新的視覺化


## 活動 1：檢視預設分析
{: #act1_tut_insights_analytics}

1. 在 {{site.data.keyword.Bluemix_short}} 的 {{site.data.keyword.apiconnect_short}} 服務中，啟動您的「儀表板」，然後選取您要開啟的「型錄」。 
2. 按一下*分析* 標籤。

   ![](./images/analyticstab.png) 
  
您將看到預設「概觀」儀表板，其中顯示包含過去 7 天下列資料的兩個長條圖視覺化：
* 前 5 大熱門產品 
* 前 5 大熱門 API 

3. 將游標移至任何條欄上方，以查看其他詳細資料（例如 API 計數、API 名稱等等）。

   ![](./images/defaultoverview.png) 

4. 使用搜尋列來過濾顯示的資料。您也可以選取不同的時間過濾器及（或）自動重新整理頻率。視覺化會更新，以反映您的選擇。

預設還會提供其他儀表板。

5. 按一下資料夾圖示以載入已儲存的儀表板，並從下拉清單中選取 **api_default**。

   ![](./images/api_default.png) 

此儀表板有一組不同的視覺化，其中顯示 API 狀態、錯誤、回應時間、總呼叫次數及每天呼叫次數。

   ![](./images/sandbox-api_default.png) 


## 活動 2：檢視事件詳細資料
{: #act2_tut_insights_analytics}

視覺化是取得有用資料概觀的好方法，但您也需要導覽至事件記錄（將資料移入圖表）的方式。

1. 將游標移至任何視覺化左下角的箭頭圖示上方。即會出現一個小型箭頭。
2. 按一下箭頭，以查看該視覺化中所使用的資料表格。 
3. 按一下**檢視事件**標籤，以導覽至最多 100 筆記錄的個別事件詳細資料。

   ![](./images/statuscodetable.png) 

您可以在儀表板上編輯、移動及刪除視覺化。

## 活動 3：建置新的儀表板
{: #act3_tut_insights_analytics}

現在，讓我們建立新的儀表板來檢視 API 資料流量型樣。這些都可以使用內建視覺化。 

1. 按一下「新建儀表板」圖示，然後按一下**從現有視覺化中選擇**鏈結。 

   ![](./images/newdashboard.png) 
    即會顯示可用的視覺化清單。



2. 選取一些視覺化來新增至儀表板。例如：
  * 已訂閱的應用程式
  * 每個方案的應用程式 
  * 成功率
  * 每天的 API 呼叫次數
  
  **提示**：選取每一個視覺化時，選取標籤會封鎖您的儀表板視圖，因此您可能不瞭解視覺化已新增至儀表板。一次選取一個視覺化，並且每次都關閉選取標籤，以查看對儀表板所做的變更。

3. 按一下**儲存**，並且提供儀表板的名稱：`Subscriber Dashboard`。

   ![](./images/savedashboard.png)

   ![](./images/namedashboard.png) 


## 活動 4：建立新的視覺化
{: #act4_tut_insights_analytics}

在我們建立的 Subscriber Dashboard 上，已併入可顯示每天 API 呼叫次數的內建視覺化。當我們查看一起呈現的整個這項資訊時，是真的想要查看應用程式的使用情形。請建立新的視覺化來顯示這項資訊。

1. 按一下**新建視覺化**，然後選取**建立視覺化**鏈結。
   ![](./images/newvisualization.png) 

2. 選取**折線圖**作為視覺化類型。已起始設定折線圖的 Y 軸已設定 API 呼叫計數。這適用於我們的圖表。

3. 選取下列項目：
	* 儲存區類型：**X 軸**
	* 聚集：**日期直方圖**
	* 自訂標籤：**時間** 
4. 按一下**執行**，以查看圖表。**提示**：您可能需要調整時間範圍來查看資料。

   ![](./images/apichart1.png)

此圖表（到目前為止）顯示 API 呼叫的時間序列。我們想要依應用程式名稱來查看 API 呼叫。

5. 按一下**新增子儲存區**按鈕。
6. 選取下列項目：
	* 儲存區類型：**分割明細行**
	* 子聚集：**期限**
	* 欄位：**app_name**
	* 自訂標籤：**應用程式**
	
   ![](./images/subbucket.png)
8. 按一下**執行**，以查看圖表。
9. 按一下**儲存**，並且提供圖表的名稱：`API Calls by App`。
10. 若要在環境定義中查看您的視覺化，請將它新增至「訂閱者」儀表板。

   ![](./images/apichartfinal.png)
 
還有其他資訊可用來視覺化 API 呼叫、呼叫者等相關詳細資料。您可在 API Connect Knowledge Center 中取得 API 事件的完整清單，或者，在建立視覺化時，於「期限」清單中取得此清單。

## 結論
{: #conclusion_tut_insights_analytics}

透過不同樣式和組合來視覺化 API 分析的能力，讓您有機會做出結論或更深入瞭解 API 資料。您可以使用此見解來決定要提供哪些 API、何時取代或棄用 API、取用 API 的人員等等。

例如，名為 "ACME" 的提供者的 API 第 1 版及第 2 版已執行數年。在發行第 2 版時已淘汰第 1 版。同時也會確保現有第 1 版消費者注意到，他們有移至第 2 版的特定時間表。在到達這個截止時間時，ACME 想要看到消費者可快速地離開第 1 版，因此，可對重要的夥伴提供協助。 

使用與剛建置的視覺化類似的視覺化，ACME 就可以提供此資訊的概覽。

在本指導教學中，我們會透過許多活動來協助您建立有用的 API 與消費者資料組合。使用視覺化及儀表板，我們可快速建立用來提供資料的工具，以協助確保提供正確的混合 API。

---

## 下一步
{: #next_tut_insights_analytics}
學習[如何管理 API 及版本化](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_version_landing)。

建立 > 管理 > 安全 > 社交化 > **分析**  

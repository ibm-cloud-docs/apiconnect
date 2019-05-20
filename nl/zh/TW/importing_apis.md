---

copyright:
  years: 2017
lastupdated: "2017-12-15"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 匯入 API
{: #importing_apis}

您可以使用 Swagger 定義檔來新增 REST API。
{:shortdesc}

## 必要條件
{: #prereq_import_swagger_importing_apis}

開始之前，請確定您的檔案符合 2.0 版的 Swagger 規格。此檔案的格式可以是 JSON 或 YAML。

若要載入 Swagger 檔案來新增 REST API，請完成下列步驟：

1. 在 API Manager 使用者介面導覽窗格中，按一下**草稿**，然後按一下 **API**。即會開啟 API 標籤。

2. 按一下 **+ 新增**，然後從**匯入**區段中選取 **Swagger 2.0**。即會開啟「**匯入 Swagger API**」視窗。

3. **選用**：若要從本端檔案系統中上傳檔案，請按一下**選取檔案**，然後在檔案系統中選取您要使用的檔案。如果 `.json`、`.yml` 及 `.yaml` 檔案包含有效的 Swagger 定義，則予以支援。

4. **選用**：若要從 URL 上傳檔案，請按一下**或從 URL 匯入**，然後在出現的 **URL** 欄位中提供正確的 URL。如果需要鑑別才能存取 URL，請提供使用者名稱及密碼。如果 `.json`、`.yml` 及 `.yaml` 檔案包含有效的 Swagger 定義，則予以支援。

5. 按一下**匯入**。即會建立新的 REST API 定義（包括路徑及 HTTP 作業）。

API 定義在匯入之後，會顯示在「**草稿**」頁面的 **API** 標籤的 API 定義清單中。接下來，您可以編輯您的 API 定義，就像編輯任何其他 REST API 定義一樣。

## 從 IBM Integration Bus 匯入 API
{: #tut_import_iib_apic_importing_apis}

使用此指導教學，您可以將使用 IBM Integration Bus 建立的 REST API 匯入至 {{site.data.keyword.apiconnect_full}}，這樣會比較容易進行管理及發佈。
{: shortdesc}

開始之前，請確定您的 REST API 檔案符合 2.0 版的 Swagger 規格。此檔案的格式可以是 JSON 或 YAML。

您可以使用 IBM Integration Bus 建立 REST API，這些特殊化應用程式可以用來將整合公開為 RESTful Web 服務，且可以由 HTTP 用戶端進行呼叫。建立 API 之後，您可以將它們匯入到 {{site.data.keyword.apiconnect_short}} 以便管理和發佈它們。

下列清單包含在 {{site.data.keyword.apiconnect_short}} 管理 API 的一些優點：
* 您可以監視 API 的呼叫數目。
* 您可以控制 API 的呼叫數目。
* 您可以維護多個版本的 API。

如需瞭解更多優點，請參閱[管理 API](/docs/services/apiconnect?topic=apiconnect-managing_apis)。

若要在 IBM Integration Bus 建立 REST API 並將它匯入至 {{site.data.keyword.apiconnect_short}}，請完成下列步驟：
1. 使用 IBM Integration Bus 建立 REST API。限制：您只能使用已安裝 IBM Integration Bus 版本隨附的 IBM Integration Toolkit 來建立 REST API。
	1. 使用 IBM Integration Toolkit 建立 REST API。如需如何完成使用 IBM Integration Bus 建立 REST API 的作業相關資訊，請參閱 IBM Knowledge Center 中的[使用 REST API 開發整合解決方案 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: #new_window}。
		
	2. 選取**檔案** > **新建** > **REST API**，開啟「建立 REST API」精靈。
		
	3. 輸入 REST API 的名稱。您指定的名稱會用來作為 IBM Integration Toolkit 中的專案名稱。
		
	4. 選取下列其中一個建立 REST API 的方法，然後完成程序：
		
	**使用 IBM Integration Toolkit 提供的 REST API 編輯器從頭開始**：
		1. 選取**建立 REST API 並自行定義資源和作業**。
		2. 按一下**完成**。新 REST API 的 REST API 編輯器會自動開啟，您必須用它來定義資源、模型及作業。
		
	**從現有 Swagger 2.0 文件**：
		1. 選取**匯入 Swagger 文件中定義的資源及作業**，然後按**下一步**。
		2. 選取 Swagger 文件的路徑，該文件說明您要在 REST API 中的資源及作業。您可以從檔案系統匯入 Swagger 文件，或是從工作區裡的現有專案匯入。檔案已驗證可用於 REST API。如果選取的
Swagger 文件在驗證時發生任何錯誤，那些驗證錯誤會顯示在精靈的開始。如果在選取的 Swagger 文件中發現錯誤，您便無法繼續。
		3. 選取**完成**以建立 API。
	5. 實作 REST API 的子流程，這些是您要包含的 REST 作業。
2. 將 REST API 專案新增至 IBM Integration Bus 的新的或現有分配管理系統保存檔 (BAR)。
3. 將 BAR 檔案部署至 IBM Integration Bus on Cloud。
	1. 如果尚未登入，請使用您的 IBM ID 登入 IBM Integration Bus on Cloud。如果沒有帳戶，請註冊帳戶。
	2. 按一下**新增整合** > **上傳 BAR 檔案**。
	3. 選取您為 REST API 專案建立的 BAR 檔案。提示：您可以在 IBM Integration Toolkit 中，在 BAR 檔案上按一下滑鼠右鍵並檢視其內容，來找到它的位置。
	4. 選取**儲存**。
	5. 選取**重新整理清單**，以更新畫面。
	6. 在 IBM Integration Bus on Cloud 的*整合* 視窗中檢視 API 的「API 整合流程」，驗證已順利上傳 BAR 檔案。
4. 選取開始圖示 ![顯示開始圖示的畫面擷取。](images/a_play_button.jpg " ") 開始整合流程。API 會開始並顯示 `Running` 狀態。
5. 從整合清單選取整合，以檢視它的相關資訊。「內容」功能表中的樹狀結構顯示 REST API 和相關聯的子流程。您也可以在其他區段檢視資訊。在「公用端點」區段中，您可以檢視 IBM Integration Bus on Cloud 指派給整合流程的公用 URL。選取**顯示完整 URL** 以檢視該作業的完整 URL。
6. 將作業的完整 URL 複製到您的剪貼簿。當您配置 API 以搭配 {{site.data.keyword.apiconnect_short}} 使用時會需要它。如果您已啟用「基本鑑別」，則也請記下指派的使用者名稱及密碼。

### 整合 IBM Integration Bus 與 API Connect。
{: #integrateiibapic_importing_apis}

1. 將與 IBM Integration Toolkit 中 REST API 專案相關聯的 Swagger 檔案匯入至 {{site.data.keyword.apiconnect_short}} 服務。 
	1. 登入 {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 服務。
	2. 在 API Manager 使用者介面導覽窗格中，選取**草稿** > **API**。即會開啟 API 標籤。
	3. 選取 **+ 新增** > **從檔案或 URL 匯入 API**。即會開啟「*匯入 OpenAPI (Swagger)*」視窗。
	4. 若要從本端檔案系統中上傳您建立的檔案，請選取**選取檔案**，然後選取您使用 IBM Integration Bus 建立的檔案。如果 `.json`、`.yml` 及 `.yaml` 副檔名的檔案包含有效的 Swagger 定義，則予以支援。請確定已選取**新增產品**選項。您可以選擇性地藉由選取**將此產品發佈至型錄**來發佈產品。
	5. 按一下**匯入**。即會建立新的 REST API 定義（包括路徑及 HTTP 作業）。提示：如果匯入時間超過 1 分鐘，請取消匯入，重新整理瀏覽器，然後嘗試重新予以匯入。您的階段作業可能已過期。
2. 將 {{site.data.keyword.apiconnect_short}} 中的已匯入 API 與 IBM Integration Bus on Cloud 中的 API 相關聯。
	1. 移至 {{site.data.keyword.apiconnect_short}} 儀表板。
	2. 選取**草稿** > **API**。
	3. 按一下您匯入的 REST API。
	4. 選取「組合」標籤，然後選取**建立組件**以新增 Proxy 原則。
	5. 將 **Proxy** 原則拖曳到新的空原則加以啟用。
	6. 貼上您從 IBM Integration Bus on Cloud 的「公用端點」區段複製的 API URL。
	7. 如果您已啟用 REST API 的「基本鑑別」，請輸入在 IBM Integration Bus on Cloud 中產生的使用者名稱和密碼。
	8. 儲存 API 設定。
3. 測試 API。
	1. 在 API 的「組合」標籤中，選取「測試」按鈕 ![「測試」按鈕](images/a_play_button.jpg "顯示測試按鈕圖示的畫面擷取。")。
	2. 選取**重新發佈產品**。
	3. 選取「作業」。
	4. 輸入必要的參數。
	5. 選取 **Invoke**。
	6. 驗證您從 API 收到預期的回應。 
	
匯入及整合 API 定義之後，您可以管理和控管 API，就像任何其他 REST API 定義一樣。如需 API 的相關資訊，請參閱[管理 API](/docs/services/apiconnect?topic=apiconnect-managing_apis)。

## 發佈 IBM API Connect 中使用 IBM App Connect Professional 建立的 API
{: #publish_importing_apis}

使用此指導教學，您可以發佈及管理使用 IBM App Connect Professional 搭配 {{site.data.keyword.apiconnect_full}} 建立的 REST API。

### 必要條件
{: #prereq_pub_api_appconn_importing_apis}

您需要 IBM App Connect Professional on Cloud 和 {{site.data.keyword.apiconnect_short}} 的有效帳戶才能夠完成此指導教學。請確定您的 REST API 檔案符合 2.0 版的 Swagger 規格。此檔案的格式可以是 JSON 或 YAML。

您可以使用 IBM App Connect Professional 建立 REST API，也就是特殊化的應用程式，可以用來將整合公開為 RESTful Web 服務，且可以被 HTTP 用戶端呼叫。建立 API 之後，您可以使用 {{site.data.keyword.apiconnect_short}} 發佈及管理它們。下列清單包含在 {{site.data.keyword.apiconnect_short}} 管理 API 的一些優點：

- 您可以監視 API 的呼叫數目。
- 您可以控制 API 的呼叫數目。
- 您可以維護多個版本的 API。

如需瞭解更多優點，請參閱[管理 API](/docs/services/apiconnect?topic=apiconnect-managing_apis)。若要在 IBM App Connect Professional 建立 REST API 並將它發佈到 {{site.data.keyword.apiconnect_short}}，請完成下列步驟：

1. 使用 IBM App Connect Professional 建立 REST API。
  - 使用您的 IBM ID 登入 [App Connect Professional Web Management Console ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/app-connect){:new_window}。如需如何完成使用 IBM App Connect Professional Web Management Console 建立 REST API 的作業相關資訊，請參閱 IBM Knowledge Center 中的[關於管理主控台設定 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window}。

  - 如果尚未選取，請選取「正式作業」標籤。
  - 在導覽畫面中，選取**儲存庫** > **配置**。
  - 在「專案配置」畫面上，選取您要發佈到 {{site.data.keyword.apiconnect_short}} 的專案。畫面上會顯示正在發佈之專案的配置詳細資料。
  - 選取**推送至 API Management**。**提示**：**推送至 API Management** 按鈕只有在您所匯入的專案具有執行中或已部署狀態時才會作用。選取播放按鈕可以啟動專案，如果鏈結未顯示的話。

  - 在「推送至 API Management」畫面上，輸入下列資訊以建立與 API Management 系統的連線。

  <table><caption>表 １. API 發佈至 {{site.data.keyword.apiconnect_short}} 的連線資訊</caption>
  <thead>
  <tr>
  <th>欄位名稱</th>
  <th>說明</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>主機</td>
  <td>指定管理叢集、伺服器或雲端位址的主機名稱。對於 {{site.data.keyword.Bluemix_notm}}，此項目很可能是 us.apiconnect.ibmcloud.com。</td>
  </tr>
  <tr>
  <td>埠</td>
  <td>指定連接管理叢集、伺服器或雲端位址所需的埠號。</td>
  </tr>
  <tr><td>使用者 ID</td>
  <td>指定用來存取管理叢集、伺服器或雲端位址的鑑別使用者名稱。這很可能是您用來登入 {{site.data.keyword.Bluemix_notm}} 的 IBM ID。</td>
  </tr>
  <tr><td>密碼</td>
  <td>指定用來存取管理叢集、伺服器或雲端位址的鑑別密碼。這很可能是您用來登入 {{site.data.keyword.Bluemix_notm}} 的 IBM ID 密碼。</td>
  </tr>
  </tbody>
  </table>

2. 選取**載入組織**，以移入與您的 ID 和密碼相關聯的組織清單。

3. 選取**組織**，以將專案與其中一個可用的組織相關聯。

4. 選取**推送至 APIM**，然後選取**確定**。

5. 選取**關閉**以關閉視窗。在您的預設瀏覽器中會開啟新的瀏覽器分頁，並顯示您的 API。

將 IBM App Connect API 與 {{site.data.keyword.apiconnect_short}} 相關聯。

#### 匯入 Swagger API 定義
{: #import_sw_importing_apis}

若要將與 IBM App Connect 中 REST API 專案相關聯的 Swagger 檔案匯入至 {{site.data.keyword.apiconnect_short}} 服務，請遵循下列步驟：

1. 登入 {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 服務。

1.  在 API Manager 使用者介面標題列中，選取**導覽至** > **草稿**。

2. 在功能表列選取 **API**。即會開啟 API 標籤。

3. 選取已匯入的 API，以開啟 API Designer。

4. 在導覽視窗中選取**組合**。在導覽視窗中會顯示原則的清單。

5. 視需要選取**建立組件**。

6. 將 **Invoke** 原則拖曳到主視窗的組件以便新增它。

7. 在主視窗上選取 **Invoke** 原則，以修改它的配置設定。

8. 使用下列資訊配置 URL 欄位的 host/basePath：

- **hostname**：此設定視您的雲端實例而定。如需此設定的相關資訊，請參閱 [IBM App Connect Professional ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SS3LC4_7.5.2.0/mapfiles/ic_home.html){:new_window}。

- **basepath**：您在 App Connect Professional 編排的 httpReceive 要求附註上指定的路徑。

9. 將您的 IBM ID 使用者名稱和密碼新增並儲存至用於 App Connect Professional 的 HTTP 基本鑑別詳細資料。

#### 測試 API
{: #test_importing_apis}

若要測試 API，請遵循下列步驟：

1. 在 API 的「組合」標籤中，選取「測試」按鈕 <img alt="顯示測試按鈕圖示的畫面擷取" src="images/a_play_button.jpg" />。
2. 選取**重新發佈產品**。
3. 選取「作業」。
4.  輸入必要的參數。
5. 選取 **Invoke**。
6. 驗證您從 API 收到預期的回應。

匯入及整合 API 定義之後，您可以管理和控管 API，就像任何其他 REST API 定義一樣。如需 API 的相關資訊，請參閱[管理 API](/docs/services/apiconnect?topic=apiconnect-managing_apis)。



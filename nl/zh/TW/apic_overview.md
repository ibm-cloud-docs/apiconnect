---

copyright:
  years: 2017
lastupdated: "2017-07-18"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 關於 IBM API Connect

使用 {{site.data.keyword.apiconnect_full}} 服務，以根據 Node.js 及 Java 運行環境來快速建立 API 及微服務。建立之後，您就可以使用企業等級的控制措施來管理 API，方法是在與應用程式開發人員共用 API 的同時，設定不同的安全等級、可見性及速率限制。{{site.data.keyword.apiconnect_short}} 服務也會提供工具，透過結構化過濾搜尋的詳細分析來轉換及提高業務成長。

<object height="315" type="application/x-shockwave-flash" width="560"
data="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US">
<desc>此視訊概述 {{site.data.keyword.apiconnect_short}} 服務</desc>
<param name="movie" value="https://www.youtube.com/v/lmxyiNMER5Y?version=3&amp;hl=en_US"/>
<param name="allowFullScreen" value="true"/>
<param name="allowscriptaccess" value="always"/>
<param name="scale" value="noScale"/>
</object>

## API 建立

使用 {{site.data.keyword.apiconnect_short}}，您可以從 Swagger 定義匯入 API，或者，透過使用 Proxy URL 或組合 HTTP 資料來源中的資料來建立 API。此外，{{site.data.keyword.apiconnect_short}} 也支援離線建立及測試 API。微型閘道與 Developer Toolkit 內嵌在一起，它可讓您連接至後端資料來源（例如 SQL Database），以及執行以建立、讀取、更新及刪除為基礎的作業。

API 是在 Developer Toolkit 內建立的。Developer Toolkit 包括 CLI 及 API Designer 圖形使用者介面。若要存取 Developer Toolkit，您需要從 npm 進行下載並安裝。安裝 Toolkit 時，是從建立 LoopBack 專案開始。下圖說明 LoopBack 專案內所含的內容。

- **LoopBack 專案**：LoopBack 專案包含 LoopBack 應用程式及「API 產品」。

- **LoopBack 應用程式**：在 Loopback 應用程式內有一個 API 端點，可用來存取您的資料來源、商業資產或雲端服務。

- **產品**：「產品」是可讓您發佈 API 的單元。「產品」中包含「方案」，而「方案」則包含 API，在呼叫它時會呼叫 API 端點。

下圖示範 LoopBack 應用程式、API 及「產品」從 Developer Toolkit CLI 或使用者介面發佈之後的部署位置。

<img src="images/loopback_project.png" alt="顯示 LoopBack 專案內所含內容的圖表"/>

- **{{site.data.keyword.Bluemix_short}} 運行環境**：LoopBack 應用程式已部署至您選擇的 {{site.data.keyword.Bluemix_short}} 運行環境。

- **閘道**：API 已部署至閘道。

**API Manager**：產品已部署至 API Manager，您可以在這裡指定其使用方式。

<img src="images/Deployed.png" alt="顯示 LoopBack 應用程式、API 及產品部署位置的圖表。"/>

如需建立 API 所需作業的相關資訊，請參閱[建立 API](creating_apis.html)。

## API Management 概觀

編譯打包及發佈「產品」之後，您可以開啟 API Manager 來管理安全、速率限制及原則，然後將「產品」發佈至「開發人員入口網站」。

如下圖中所示，產品包含方案、方案包含 API。

<img src="images/Product.png" alt="顯示「產品」所含內容的圖表"/>

### 方案

若要讓 API 可供客戶使用，則必須將它包含在「方案」中。「方案」用來區分不同的供應項目。「方案」可以共用 API，但是否需要訂閱核准則取決於「方案」本身。此外，您還可以透過「方案」或透過「方案」API 內置換「方案」速率限制的作業，來強制速率限制。

### 產品

「方案」及 API 會群組到「產品」中。透過「產品」，您可以管理 API 及「方案」的可用性和可見性。使用 API Designer 可以建立、編輯及編譯打包「產品」。使用 API Manager 可以管理「產品」的生命週期。

下圖示範「產品」、「方案」與 API 彼此的關係。請注意，「方案」如何只屬於一個「產品」、可以擁有與相同「產品」內其他「方案」不同的 API，以及可以與任何「產品」中的「方案」共用 API。顯示「產品」、「方案」及 API 階層的圖例。<img src="images/plan_product_hierarchy.png" alt="顯示「產品」、「方案」及 API 階層的圖例。"/>

您只能在「產品」內建立「方案」，然後在「型錄」中發佈這些「產品」。生命週期管理者接著可以透過 API Manager 來控制 API 及「方案」的可用性和可見性。透過「開發人員入口網站」，客戶接著可以訂閱他們可用的其中一個「方案」（在 API Manager 中決定）。使用者只能訂閱特定「產品」中的一個「方案」。單一「產品」內的多個「方案」十分有用，原因在於它們可以滿足類似的用途，但效能層次不同。例如，您可能有「展示方案」（將單一 API 設為可用）及「完整方案」（將數個 API 設為可用）。

不但可控制客戶可以使用的 API，而且還可以使用不同的「方案」來實作速率限制。速率限制可以實作為整個「方案」的預設速率，或針對該「方案」內 API 的特定作業，從「方案」速率限制豁免它們。在作業之間以及針對整體限制，不同的「方案」可以有不同的速率限制。這適用於提供客戶不同的服務水準。例如，「展示方案」可能會強制執行每分鐘 10 個呼叫的速率限制，「完整方案」則可能允許每分鐘最多 1000 個呼叫。

**附註：**在「方案」層次套用速率限制，會建立適用於「方案」內每一個作業的預設速率限制。如果您需要為特定作業設定特定速率限制，則必須在作業本身內設定這些限制，此設定會置換「方案」層次的設定。

IBM API Connect 也支援多個「產品」版本的實作。您可以選擇版本號碼，並使用它們來協助開發「產品」及「方案」。

**附註：**「產品」的版本與關聯「方案」中所含的任何 API 版本不同。「方案」本身不能有自己的版本，而是使用其母「產品」的版本。

如需管理 API 所需作業的相關資訊，請參閱[管理 API](managing_apis.html)。

### 型錄

「產品」必須編譯打包到「型錄」，然後發佈至「開發人員」組織，以供應用程式開發人員使用。在 {{site.data.keyword.apiconnect_short}} 中，您可以建立多個「型錄」。
若要區隔「產品」與 API，以在使其可供「開發人員」組織使用之前進行測試，則型錄很有幫助。


「型錄」是一種編譯打包目標，其作用如同閘道及「開發人員入口網站」的邏輯分割區。API 呼叫及「開發人員入口網站」的 URL 是特定「型錄」的特有項目。在一般配置中，API 提供者組織會使用用於測試開發中 API 的開發「型錄」，以及用於管理準備好完整使用之 API 的正式作業「型錄」。一般方式是包含具有開發「型錄」的開發雲端、一些測試「型錄」，以及可能有其專屬測試「型錄」的正式作業雲端。

#### 型錄設定

您可以將下列設定套用至「型錄」：

- **開發**：依預設，會提供開發「型錄」。開發「型錄」只能用於進行測試。在開發「型錄」中，會強制執行編譯打包及發佈動作，這表示如果您重新發佈先前已發佈的「產品」，則會改寫該「產品」而不發出警告。如果發現衝突，系統會自動解決這些衝突。取消發佈動作會自動執行。

當您在開發「型錄」中使用測試工具時，會強制執行任何您測試的「產品」，並改寫已編譯打包及已發佈的「產品」，即使正在「開發人員入口網站」上使用這些作業。必須以相同的方式使用從開發「型錄」建立的「開發人員入口網站」，亦即，僅用於進行測試，而不是用於實際案例。

- **自動訂閱**：如果您啟用「型錄」的自動訂閱，則在 API Manager 使用者介面中測試 API 變得更簡單，因為會使用測試應用程式（內含預先提供的用戶端 ID 及用戶端密碼），它會自動訂閱「型錄」中的所有「方案」，因此您不需要在測試時指定方案或應用程式。測試應用程式不受限於速率限制。
自動訂閱僅適用於開發「型錄」。

- **預設**：您可以將其中一個「型錄」設為預設「型錄」。然後，對發佈到該「型錄」之 API 的呼叫可以使用不含「型錄」名稱的更簡短 URL。

如需使用「開發人員入口網站」的相關資訊，請參閱[探索及使用 API](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.dita)。

### 聯合

使用 {{site.data.keyword.apiconnect_full}} 聯合特性，您可以將「型錄」分割為「空間」。每一個「空間」都可供不同的 API 提供者開發團隊使用，並具有關聯團隊發佈到該「空間」的一組特別與 API 相關的專屬管理功能，讓每一個團隊單獨管理其 API。

當您將 API 編譯打包或發佈到已啟用「空間」的「型錄」時，請在您要編譯打包或發佈到其中的那個「型錄」內指定「空間」。不過，存取「型錄」的「開發人員入口網站」的應用程式開發人員不清楚「型錄」的「空間」分割，並將 API 視為協調供應項目。每一個「空間」都有它自己的「產品」生命週期管理、訂閱核准及分析資料。
您使用「空間」特定存取控制來限制使用者存取每一個「空間」；例如，「航班」團隊中的開發人員可以只將 API 編譯打包到「航班空間」。

**附註：**依預設，會停用「型錄」中的「空間」。修改「型錄」設定，即可啟用「空間」。

若要分割型錄，請參閱[分割型錄](create_catalog.html#apic_spaces)。

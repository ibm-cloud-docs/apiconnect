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

# 管理產品
{: #managing_products}

如需「產品」管理方式的詳細資料，請參閱 IBM&reg; Knowledge Center 文件：[管理產品 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/task_product_management.html){: #new_window}。

## 產品生命週期
{: #prod_lifecycle_managing_products}

當您管理「產品」版本時，這些版本會經過一系列的生命週期狀態，一開始是將草稿「產品」版本編譯打包至某個環境，接著發佈以讓應用程式開發人員可以使用該「產品」版本，最後予以棄用及保存。下表及下圖說明「產品」版本的各種「產品」生命週期狀態。

<table summary="" id="apic_004__table_lym_rxj_gv" class="defaultstyle"><caption class="style-scope doc-content">表 1. API Management 產品生命週期狀態</caption>
<thead class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 11.25%" id="d3569e1968" class="thleft thbot style-scope doc-content">狀態</th>
<th style="width: 88.75%" id="d3569e1970" class="thleft thbot style-scope doc-content">說明</th>
</tr>
</thead>
<tbody class="style-scope doc-content">
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">草稿</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">「產品」未部署且未與 API Connect「型錄」相關聯。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已編譯打包</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">將「產品」版本的不可變副本部署至目標環境。「已編譯打包」是從草稿「產品」編譯打包時的起始狀態。「產品」處於已編譯打包狀態時，任何開發人員都還看不到它也無法訂閱它。</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已發佈</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">目標開發人員或社群可以看到及訂閱「產品」版本。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已淘汰</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">只有目前訂閱其應用程式的開發人員才能看到「產品」版本。無法再對「產品」進行新的訂閱。</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已棄用</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">無法檢視或訂閱「產品」版本，並停止所有關聯的 API。依預設，已棄用的「產品」版本會顯示在 API Manager 使用者介面的「產品」頁面中。</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 11.25%" headers="d3569e1968 " class="style-scope doc-content">已保存</td>
<td style="width: 88.75%" headers="d3569e1970 " class="style-scope doc-content">無法檢視或訂閱「產品」版本，並停止所有關聯的 API。依預設，「產品」版本不會顯示在 API Manager 使用者介面的「產品」頁面中。</td>
</tr>
</tbody>
</table>

### 產品生命週期流程
{: #prod_lifecycle_flows_managing_products}

下圖顯示「產品」版本的可能生命週期狀態，以及將「產品」版本從某種生命週期狀態移至另一種狀態的「產品」管理作業；例如，「棄用」作業會將「產品」版本從「已發佈」移至「已棄用」狀態。

<img alt="「產品」版本的生命週期狀態圖" src="images/apic_plan_lifecycle.png">


## 建立產品
{: #create_product_managing_products}

建立「產品」，以將一組 API 及「方案」收集為一個可供開發人員使用的供應項目。「方案」包括可整個套用至「方案」或針對 API 中每一個作業而指定的速率限制設定。透過「產品」及「方案」，您可以更加強控制開發人員可存取哪些 API。建立產品之後，必須對其進行編譯打包。編譯打包產品會將其移至作用中狀態，以讓您呼叫及測試其內所含的 API。編譯打包產品後，任何開發人員都還看不到它。

**提示**：除了使用此作業中所述的方法之外，您也可以在建立 API 時建立「產品」。如果您使用 Developer Toolkit 指令行介面來建立 API，則會自動建立「產品」。您接著可以在 API Designer 的「**產品**」頁面中開啟新的「產品」，以變更任何「產品」設定。

若要使用 API Designer 來建立「產品」，請完成下列步驟：
1. 若要開啟 API Designer 使用者介面，請開啟指令行，然後輸入下列指令：
```
apic edit
```
即會在預設瀏覽器中開啟 API Designer。

2. 在 API Designer 的導覽窗格中，按一下**產品**。即會開啟「產品」標籤。

3. 按一下**新增**，然後按一下**新建產品**。即會開啟「新增產品」視窗。

4. 完成下列欄位：
    - 標題
    - 名稱
    - 版本

5. 按一下**新增**。即會開啟新「產品」的「設計」標籤。

6. **選用**：在**資訊**區段中，輸入「產品」的說明、聯絡人、授權及服務資訊條款。

7. 在**可見性**區段中，您可以指定可看見「產品」的使用者。您可以選擇**公用**、**已鑑別使用者**或**自訂**。如果您選取**自訂**，請使用**鍵入以新增**欄位，來搜尋可看見「產品」中「方案」的開發人員組織或社群。

    **附註：**若要搜尋開發人員組織或社群，「產品」必須處於已編譯打包、已發佈或已淘汰狀態。如果已於其中編譯打包、發佈或淘汰的「型錄」不是沙盤推演「型錄」，則無法對處於上述其中一種狀態的「產品」進行其他變更。如需相關資訊，請參閱[產品生命週期](#prod_lifecycle_managing_products)。

8. 指定可訂閱「產品」的使用者。您可以選擇**已鑑別使用者**或**自訂**。如果您選取**自訂**，請使用**鍵入以新增**欄位，來搜尋可訂閱「產品」中「方案」的開發人員組織或社群。

9. 在 API 區段中，指定您要包含在「產品」中的 API。
    1. 按一下**新增 API** 圖示。
    2. 選取您要包含的 API，然後按一下**套用**。即會列出選取的 API。

10. 若要讓 API 可供應用程式開發人員使用，您必須將它包含在「方案」中。若要將一個以上的「方案」新增至「產品」，請按一下**新增方案**圖示。
    1. 展開已建立的新「方案」。如果您已將 API 新增至「產品」，則會自動包含這些項目。
    2. 在**標題**及**名稱**欄位中重新命名您的「方案」，然後選擇性地新增說明。**附註：**系統會自動為您建立一個「預設方案」，如果您不想建立自己的「方案」，則可以將 API 併入此「方案」中。不過，如果您決定不使用「預設方案」，則必須予以刪除，因為如果「產品」包括任何未包括 API 的「方案」，則無法編譯打包「產品」。

11. 驗證您所需的 API 已包含在「方案」中。
    1. 展開您要新增 API 的「方案」。
    2. 在包含的 API 下，確定已選取所需 API 的勾選框。如果已選取 API，而且您不想要它們包含在您編輯的「方案」中，請清除其勾選框。

12. **選用**：新增「方案」的計費資訊。若要新增計費資訊，您必須建立一個具有信用卡處理服務的帳戶，如此您的客戶才可以使用信用卡付款。每月計費「方案」會在每一個月的同一個日期計費。

13. **選用**：如果您要修改「方案」中包括 API 的哪些作業，請將游標移至包含該作業的 API 上方。按一下**顯示作業**圖示，然後選取或清除您要包含或排除的作業的勾選框。

14. **選用**：若要新增「方案」的速率限制，請清除**無限制**勾選框，然後指定您要套用的速率限制。如果已選取**強制硬性限制**勾選框，則「方案」將在達到速率限制之後停止應用程式呼叫 API，否則將會顯示一則警告。

    **附註：**在「方案」層次套用速率限制，會建立適用於「方案」內每一個作業的預設速率限制。如果您需要為特定作業設定特定速率限制，則必須在作業本身內設定這些限制，此設定會置換「方案」層次的設定。

15. **選用**：指定「方案」是否需要訂閱核准。如果您要求透過 API Manager 使用者介面核准開發人員的訂閱，請選取**需要訂閱核准**；否則，請確定已清除此勾選框。

16. **選用**：新增作業的速率限制。
    1. 將游標移至包含作業的 API 上方，然後按一下**顯示作業**圖示。
    2. 將游標移至您要套用速率限制的作業上方。按一下**編輯速率限制**圖示。
    3. 確定已清除**無限制**勾選框，然後指定您要套用的速率限制。如果已選取**強制硬性限制**勾選框，則「方案」將在達到速率限制之後停止應用程式呼叫 API，否則將會顯示一則警告。

- 按一下**儲存**圖示，以儲存您的變更。

您已建立「產品」，並將一組 API 及「方案」指定為一個現在可供開發人員使用的供應項目。接下來，將您的產品編譯打包至型錄，如下節[編譯打包產品](#stage_product_managing_products})中所解釋。


## 編譯打包產品
{: #stage_product_managing_products}

請先編譯打包「產品」以在「型錄」中建立該「產品」的特定版本，然後再進行發佈。「產品」處於已編譯打包狀態時，任何開發人員都還看不到它也無法訂閱它。

**附註：**API Manager 使用者介面也包括編譯打包「產品」的能力，不過，這些作業的偏好方法是使用 API Designer 使用者介面（如下列程序中所述）。

1. 在 API Designer 的導覽窗格中，按一下**產品**。即會開啟「產品」標籤。

2. 按一下您要使用的**產品**。如果您有多個版本的「產品」，請確定按一下您要使用的版本。

3. 按一下**發佈**圖示。

4. 如果您要編譯打包「產品」到其中的「型錄」顯示於清單中，請執行下列動作：
    1. 選取您需要的「型錄」。 
    2. 依序選取**僅編譯打包（不會發佈產品）**及**發佈**。已編譯打包您的「產品」。

5. 如果您要編譯打包「產品」到其中的「型錄」未顯示於清單中，請執行下列動作：
    1. 按一下**新增及管理目標**。
    2. 按一下**新增 {{site.data.keyword.Bluemix_notm}} 目標**。
    3. 選取您要發佈至其中的 {{site.data.keyword.Bluemix_short}} **地區**。
    4. 選取您要發佈至其中的 {{site.data.keyword.Bluemix_notm}}
**組織**。
    5. 即會顯示「型錄」清單。選取您要發佈到其中的「型錄」。
    6. 按**下一步**。
    7. 如果您具有要發佈的 LoopBack 應用程式，請選取要發佈的應用程式。否則，請選取**無**。
    8. 按一下**儲存**。
    9. 再按一下**發佈**，然後選取您剛剛新增的目標。
    10. 選取所需的「型錄」。
    11. 選取**僅編譯打包**。
    12. 按一下**發佈**。

已將您的「產品」編譯打包到「型錄」。若要在「型錄」中檢視「產品」的狀態，請開啟 API Manager 使用者介面，在導覽窗格中選取「儀表板」區段，然後按一下所需的「型錄」。「產品」會顯示「已編譯打包」狀態。

- 開啟 {{site.data.keyword.Bluemix_notm}} **儀表板**。您將會在「應用程式」區段中看到應用程式磚。

開啟 API Manager 以將產品發佈至社群，且應用程式開發人員可以透過「開發人員入口網站」存取它，如下節[發佈產品](#publish_proj_managing_products})中所解釋。


## 發佈產品
{: #publish_proj_managing_products}

發佈方案之後，應用程式開發人員即可看見及存取 API。發佈「產品」，即可在 {{site.data.keyword.Bluemix_short}} **型錄**及內建「開發人員入口網站」中看見產品，以供應用程式開發人員使用。

### 必要條件
{: #prereq_publish_proj_managing_products}

您必須先編譯打包「產品」，才能進行發佈。如需編譯打包「產品」的相關資訊，請參閱[編譯打包產品](#stage_product_managing_products)。

若要發佈「產品」，請完成下列步驟：

1. 在 API Manager 的導覽窗格中，展開**型錄**區段，然後選取您要使用的「型錄」。即會開啟「型錄」的「產品」標籤，並顯示該「型錄」中可用的所有「產品」。您可以使用畫面右側的過濾器勾選框，來選取顯示的狀態。

2. 在您要使用的「產品」版本旁，按一下**管理**圖示，然後按一下**發佈**。即會顯示「編輯可見性及訂閱者」對話框。

3. 指定下列選項：
    - `顯示給`：您可以選擇**公用使用者**、**已鑑別使用者**或**自訂**。如果您選取`自訂`，則可以使用**鍵入以新增...** 欄位，來搜尋可看見「產品」的組織或社群。
    - `訂閱者`：您可以選擇**已鑑別使用者**或**自訂**。如果您選取`自訂`，則可以使用**鍵入以新增...** 欄位，來搜尋可看見「產品」的組織或社群。

4. 按一下**發佈**。如果需要核准才能在此「型錄」中發佈「產品」，則會傳送核准要求，而且「產品」會移至「擱置」狀態；核准要求之後即會發佈「產品」。如果不需要核准，則會立即發佈「產品」版本，並移至「已發佈」狀態。

您的「產品」即會處於「已發佈」狀態。您的「產品」已發佈至「型錄」，並可供指定的組織或社群使用。所選取群組內的應用程式開發人員可以在「產品」內看到及使用 API。
任何使用您「產品」的應用程式開發人員要求都會顯示在包含「型錄」的「核准」標籤上，您可以在其中拒絕或接受要求。


## 將產品發佈至 Bluemix
{: #pub_to_bm_managing_products}

若要在 {{site.data.keyword.apiconnect_short}}「儀表板」的「**探索 API**」區段中查看您的「產品」，請完成下列步驟。

### 必要條件
{: #prereq_pub_bm_managing_products}

開始之前，如果您要發佈使用 LoopBack 所實作的 REST API，請確定您已發佈應用程式運行環境，並已將您的產品編譯打包成讓 Invoke Proxy 指向新應用程式。如需如何執行此作業的相關資訊，請參閱[編譯打包及發佈 Loopback 應用程式](/docs/services/apiconnect?topic=apiconnect-managing_apis#stage_publish_lb_app_managing_apis)。

1. 在 API Manager 使用者介面中，按一下**新增** > **型錄**。即會顯示「**新增型錄**」視窗。

2. 完成下列欄位，然後按一下**新增**：
    - 顯示名稱
    - 名稱
	
3. 選取您所建立的「型錄」。

4. 按一下**設定**圖示。

5. 按一下**入口網站**，然後選取下列其中一個選項：
    - **IBM 開發人員入口網站**。如果您選取此選項，則會顯示「入口網站 URL」。
    - **其他**。如果您選取此選項，請輸入您要使用之「入口網站」的 URL。

6. 在「使用者登錄及邀請」區段中，按一下**使用者登錄**箭頭，然後選取 **SAML**。

7. 在導覽窗格中，按一下**開發人員**圖示。

8. 按一下**新增 IBM Cloud 組織**。

9. 新增 {{site.data.keyword.Bluemix_short}} 使用者電子郵件位址，然後按一下**新增**。

10. 即會將邀請傳送至您的電子郵件位址。

11. 按一下電子郵件中的鏈結，以接受邀請。即會開啟 {{site.data.keyword.Bluemix_notm}} 使用者介面。

12. 選取您的 {{site.data.keyword.Bluemix_notm}} 組織，然後按一下**確認**。

13. 在 API Manager 使用者介面中，按一下**產品**圖示。

14. 在您要使用的「產品」版本旁，按一下**管理**圖示，然後按一下**發佈**。即會顯示「編輯可見性及訂閱者」對話框。

15. 指定下列選項：
    - **顯示給**：選擇**自訂**，然後使用**鍵入以新增...** 欄位來選取開發人員組織，以及您要新增的任何其他組織。
    - **訂閱者**：選擇**自訂**，然後使用**鍵入以新增...** 欄位來選取開發人員組織，以及您要新增的任何其他組織。

16. 按一下**發佈**。

如果需要核准才能在此「型錄」中發佈「產品」，則會傳送核准要求，而且「產品」會移至「擱置」狀態；核准要求之後即會發佈「產品」。如果不需要核准，則會立即發佈「產品」版本，並移至「已發佈」狀態。

您的產品即會顯示在 {{site.data.keyword.apiconnect_short}} **儀表板**的**探索 API** 標籤中。如果您按一下「產品」鏈結，則會帶領您前往「開發人員入口網站」中的「產品」。

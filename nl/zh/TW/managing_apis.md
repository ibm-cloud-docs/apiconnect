---

copyright:
  years: 2018
lastupdated: "2019-01-17"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理 API
{: #managing_apis}

您可以在 {{site.data.keyword.Bluemix}} 中使用 API Connect 管理 API，不論它們是在 {{site.data.keyword.Bluemix_notm}} 中，還是在 {{site.data.keyword.Bluemix_notm}} 外部維護。管理 API 容許您控制用量、提高採用，以及追蹤統計資料。

如果您是客戶，則可以在開發人員建立 API 並將產品推送至 {{site.data.keyword.Bluemix_notm}} 之後，管理它在 API Manager 使用者介面內的使用方式。下列各主題說明如何在 {{site.data.keyword.apiconnect_short}} 內建立及管理產品。

## 透過 Secure Gateway 公開內部部署 API
{: #expose_apis_sec_gate_managing_apis}

您可以建立 Secure Gateway，以安全地將內部部署 API 公開到 {{site.data.keyword.apiconnect_full}}。

當您建立 Secure Gateway，然後提供其用戶端位址或 Cloud `<host>:<port>` 時，會整合 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.SecureGateway}} 服務與 {{site.data.keyword.apiconnect_short}} 的特性。這表示您有安全的方式可以透過安全通道從 {{site.data.keyword.apiconnect_short}} 存取內部部署 API。您可以有效率地在公用環境上建立與 {{site.data.keyword.apiconnect_short}} 的通道，而不需要公開內部部署資料。您只需要在 IBM Cloud 上建立並配置 Secure Gateway，然後在 API 裡為它提供位址。

如需 {{site.data.keyword.SecureGateway}} 服務的相關資訊，以及如何設定，請參閱[關於 {{site.data.keyword.SecureGateway}}![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}。

### 搭配使用 Secure Gateway 與 API
{: #using_sec_gate_apis_managing_apis notoc}

當您已配置閘道時，即可將它與 API 搭配使用。
{:shortdesc}

若要搭配使用 Secure Gateway 與 API，請完成下列步驟。
1. 如下列步驟所述，建立 API 及「產品」。
  - 按一下**導覽至** <img src="images/navigate_to_icon.png" alt="「導覽至」圖示" /> > **草稿** > **API** > **新增**。
  - 選取您要建立的 API 類型。
  - 選取或按一下**新增產品**。**重要事項**：請不要發佈「產品」。
  - 按一下**建立 API**。API 即會顯示在`設計`視圖中。
  
2. 按一下**組合**。

3. 按一下 **invoke** 原則，以開啟 **invoke** 選用區。**限制**：邏輯參數（例如 `Switch`、`Operation Switch` 及 `If`）不能與使用 Secure Gateway 的 API 搭配使用。

4. **請勿**選取**透過 Secure Gateway 存取 URL** 勾選框。
**重要事項**：此勾選框是針對已淘汰的特性，已不支援該特性用於正式作業，且可能隨時移除。您將改為直接提供 Secure Gateway URL 的位址，而不選取此勾選框。

5. 在 URL 欄位中，將 `target-url` 更新為雲端主機名稱及埠號，例如：
```
target-url: cap-sg-prd-5.securegateway.appdomain.cloud:18579
```

6. 按一下**儲存** <img src="images/icon_save.png" alt="「儲存」圖示" />。

7. 按一下**所有 API** > **產品**，然後選取您稍早建立的「產品」。

8. 按一下**發佈**，以將「產品」編譯打包到選取的「型錄」。

9. 選取您要使用的「型錄」。

10. 選取已編譯打包的「產品」。

11. 按一下**發佈**。

您已安全地將內部部署 API 公開到 {{site.data.keyword.apiconnect_short}}。接下來，測試 {{site.data.keyword.SecureGateway}} API。

### 測試 Secure Gateway API
{: test_sec_gate_managing_apis notoc}

在 API 中為 {{site.data.keyword.SecureGateway}} 提供位址之後，即可測試 API，以確保閘道運作中，並且產生正確回應。

若要使用 Secure Gateway 來測試 API，請完成下列步驟：

1. 按一下 <img alt="「導覽至」圖示" src="images/navigate_to_icon.png" /> > **草稿** > **API** **<您的 API>** > **組合**。

2. 按一下**測試**圖示 <img src="images/test_icon.png" alt="「測試」圖示"/>。

3. 從提供的清單中，選取要測試的「型錄」。

4. 確定 URL 提供正確 Secure Gateway `<cloud_host>:<port>` 的位址，且 Secure Gateway 服務目的地已正確地配置，如 [{{site.data.keyword.SecureGateway}}![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window} 文件中所述。

5. 從提供的清單中選擇現有「產品」，然後按一下**重新發佈產品**。**重要事項**：如果此「產品」已發佈至「型錄」，則會使用新的閘道來重新發佈「產品」。

6. **選用**：提供用來建立新「產品」的名稱，然後按一下**建立及發佈**。

7. 按**下一步**。

8. 從提供的清單中，選取要呼叫的作業。

9. 按一下 **Invoke**。

即會顯示測試結果。

## 編譯打包及發佈 LoopBack 應用程式
{: #stage_publish_lb_app_managing_apis}

1. 在 API Designer 的導覽窗格中，按一下**產品**。即會開啟「產品」標籤。

2. 選取「產品」的版本，並確保按一下您要使用的版本。

3. 若要將運行環境發佈至 {{site.data.keyword.Bluemix_notm}}，請按一下**發佈**。

4. 按一下**新增及管理目標** > **新增 IBM Cloud 目標**。

5. 選取您要發佈至其中的 {{site.data.keyword.Bluemix_notm}} **地區**，並登入。

6. 選取您要發佈至其中的 {{site.data.keyword.Bluemix_notm}} **組織**。

7.  即會顯示「型錄」清單。選取您要發佈到其中的「型錄」。

8.  按**下一步**。

9. 選取您要發佈的 LoopBack 應用程式。如果這是您第一次將運行環境部署至 {{site.data.keyword.Bluemix_notm}}，請新增名稱，然後按一下**新增**圖示。

10.  按一下**儲存**。

11.  再按一下**發佈**，然後選取**發佈應用程式**。

12.  按一下**發佈**。

13. 在指令行中，指定 API 的「API 目標 URL」及 API invoke tls-profile。記下此資訊。API invoke tls-profile 一律是 `client:Loopback-client`，但您可以擷取「API 目標 URL」（如下列步驟所述）。
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. 在 API Designer 使用者介面中，請完成下列步驟：
    1. 按一下 **API**。
    2. 選取您的 API。
    3. 按一下**組合**。
    4. 在「組合」編輯器中，按一下**過濾器原則**圖示。
    5. 選取 **DataPower Gateway 原則**。
    6. 按一下**儲存**，以儲存 API。

15.  接下來，您需要發佈至 API Manager。按一下**發佈**。
    1. 選取**發佈應用程式**，然後選擇下列其中一個選項：
	    - **取代現有應用程式**：如果擁有已發佈的應用程式，請選取這個選項來改寫現有應用程式。
        - **作為全新的應用程式（使用現有路徑）**：選取這個選項，可建立新的應用程式，並在**新建應用程式**欄位中為它提供名稱。此服務不會被岔斷。

    2. 選取下列選項：
	    - 編譯打包或發佈產品
        - 選取特定產品
        - _your product_
 
    3. 按一下**發佈**。

若要測試發佈已運作，請完成下列步驟：

1. 確定 {{site.data.keyword.Bluemix_notm}} 應用程式在執行中。

2. 開啟瀏覽器視窗，然後導覽至 API URL。應用程式是使用用戶端驗證進行保護。如果您未提供正確的用戶端憑證，則會發生錯誤（這是預期狀況）。

3. 導覽至公開的 {{site.data.keyword.apiconnect_short}} URL。例如：
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
即會顯示 200 回應。

## 配置型錄
{: #config_cat_managing_apis}

您可以建立及配置「API Manager 型錄」。若要區隔「產品」與 API，以在使其可供「開發人員」組織使用之前進行測試，則型錄很有幫助。配置「型錄」時，您也可以配置自訂品牌，如此就不需要使用 API Manager 所提供的預設 API URL。

完成下列步驟，以建立「型錄」：

1. 按一下**導覽至** <img alt="「導覽至」圖示" src="images/navigate_to_icon.png"> > **儀表板**。

2. 按一下 **+ 新增** > **型錄**。即會顯示「**新增型錄**」視窗。

3.  在**顯示名稱**欄位中，輸入新「型錄」的名稱。

4. 在**名稱**欄位中，輸入您要用來構成 URL 之「型錄」區段的文字。**附註：****名稱**欄位只能包含小寫英數字元（a-z 和 0-9）或連字號字元 (-)。連字號不能用來作為名稱的第一個或最後一個字元。

5. 按一下**新增**。即會在儀表板上建立及顯示「型錄」。

6. 若要配置「型錄」，請按一下「型錄」的名稱，按一下**設定** > **資訊**，然後繼續執行下列步驟：
  1. 如果新的「型錄」是開發「型錄」，請選取**開發模式**。如果您選取開發模式，則會強制執行編譯打包和發佈動作，這表示如果您重新發佈先前已發佈的「產品」，則會改寫該產品而不發出警告。如果發現衝突，系統會自動解決這些衝突。取消發佈動作會自動執行。**附註：**開發「型錄」不會顯示「核准」方框。您無法為生命週期啟用核准處理程序。
  2. 如果您要啟用「型錄」的自動訂閱，請選取**自動訂閱**。啟用自動訂閱可讓測試 API 變得更簡單，因為會使用測試應用程式（內含預先提供的用戶端 ID 及用戶端密碼），它會自動訂閱「型錄」中的所有「方案」，因此您不需要在測試時指定方案或應用程式。**附註：**自動訂閱僅適用於開發「型錄」。
  3. 如果「型錄」是預設編譯打包「型錄」，請選取**預設**。然後，對於發佈至「型錄」的 API 呼叫可以使用不含「型錄」名稱的更簡短 URL。**附註：**您只能對一個「型錄」選取**預設**。
  4. **選用**：按一下**端點**，然後在下列欄位中移入資料：
        - **自訂閘道 URL**：在「自訂閘道 URL」文字欄位中，輸入 URL。如果您想要對部署到 {{site.data.keyword.apiconnect_short}} 的 API 保存 URL 的自訂品牌，請使用「自訂閘道 URL」，而不是使用 API Manager 所產生的預設 URL。依預設，{{site.data.keyword.apiconnect_short}} 閘道 URL 具有下列格式：
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        不過，您可以指定更適合您企業的 URL 來置換預設值；例如，`https://api.mycompany.com`。然後，「開發人員入口網站」中顯示的所有 API 端點都會反映指定的 URL。
        **附註：**
		    - 您必須配置 DNS 項目，以將自訂主機名稱及網域對映到預設閘道 URL。
		    - 針對要反映自訂閘道 URL 的 API 端點，您必須將 API 配置成由 API Connect 閘道強制執行。如需相關資訊，請參閱[指定 API 的替代主機 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}。
		    - 確保未將相同的自訂閘道 URL 套用到多個「型錄」，因為在該實務範例中未定義此行為。**提示**：呼叫 API 時，您也可以將 API 要求上的 HTTP 主機標頭設為「自訂閘道 URL」欄位中所指定的值。

	    - **自訂 API URL**：在「自訂 API URL」文字欄位中，輸入 URL。您可以使用「自訂 API URL」，針對已部署至第三方閘道的 API 指定 URL。

	    「自訂 API URL」代表 API 透過其在外部已知的端點；亦即，發佈到開發人員入口網站且由應用程式開發人員用來呼叫或通告 API 的端點。

	    如果您要在這個「型錄」中使用協力廠商閘道或外部負載平衡器，請於此欄位中提供 URL。然後，開發人員入口網站中顯示的所有 API 端點都會反映指定的 URL。這些端點存在於第三方閘道或負載平衡器上，而且會投射一個公開給 API 消費者的虛擬位址，其對映到閘道上的 API Proxy 或 API 組合端點。從自訂 API URL 衍生而來的端點一般會在正式作業的開發人員入口網站中發佈，以通告 API 的位址。

	    **附註：**如果您為「型錄」指定自訂 API URL，其優先順序高於配置 API 時所指定的任何主機名稱。如需相關資訊，請參閱[指定 API 的替代主機 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}。

	    - **開發人員入口網站 API 呼叫的主機名稱**：在「入口網站 API 端點」視窗區域中，輸入「開發人員入口網站」API 呼叫的主機名稱。您輸入的主機名稱可以是「管理」服務的主機名稱。若要存取「開發人員入口網站」環境定義內的「開發人員入口網站 API」，您必須配置「開發人員入口網站 API」呼叫的基本主機名稱。這個動作可讓 API Manager 將主機名稱對映至「開發人員入口網站 API」呼叫的提供者組織及「型錄」，而不需要您對其進行查閱並將它們併入呼叫中。

7. 按一下**儲存**圖示。

## 分割型錄
{: #part_cat_managing_apis}

若要在 {{site.data.keyword.apiconnect_short}} 中使用聯合特性，您必須在任何需要聯合功能的「型錄」中啟用「空間」。

若要在「型錄」中啟用「空間」，請完成下列步驟：
1. 在 API Manager 使用者介面的「儀表板」上，選取您要使用的「型錄」。

2. 按一下**設定** > **概觀**，然後按一下**空間**調節器控制項。

3. 在**啟用空間**視窗中，按一下**啟用**，然後按一下**儲存**圖示 <img src="images/icon_save.png" alt="「儲存」圖示"/>。即會在**空間**調節器控制項下方顯示**管理空間**鏈結，並將**空間**鏈結新增至導覽窗格。按一下下列任一個鏈結，即可管理「空間」。

即會啟用「型錄」的「空間」，並建立預設「空間」（稱為「新空間」）。

如需使用聯合的相關資訊，請參閱 Knowledge Center 主題：[在 IBM API Connect 中使用聯合 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}。

## 配置開發人員入口網站
{: #config_dev_portal_managing_apis}

開發人員入口網站是發佈方案以供應用程式開發人員存取及使用的位置。

您可以建置自訂的「開發人員入口網站」，以供應用程式開發人員使用。您具有外觀、內容、使用者設定及配置設定的完整管理控制權。

除了容許應用程式開發人員尋找及使用 API 之外，「開發人員入口網站」還提供其他特性（例如，討論區、部落格、評論、評分，以及 API 的 Swagger 使用者介面）。

1. 在 API Manager 使用者介面中，選取您要使用的「型錄」。

2. 選取**設定**標籤。

3. 按一下**入口網站**。

4. 在「**入口網站配置**」區段中，選取 **IBM 開發人員入口網站**。即會顯示「入口網站 URL」。

5. 按一下**儲存**。您即會收到一封電子郵件，其中包含「開發人員入口網站」Web 管理使用者的一次性登入鏈結。

6. 按一下電子郵件中傳送的鏈結，並遵循指示來重設密碼。

您的「開發人員入口網站」已配置好。您可以在所收到電子郵件的主旨行中找到「開發人員入口網站」的 URL。按一下**入口網站** > **設定**，也可以在 API Manager 使用者介面中找到 URL。

如需可在「開發人員入口網站」中完成的作業的相關資訊，請參閱 IBM Knowledge Center 中有關[開發人員入口網站 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){: #new_window} 的主題。

## 配置角色的許可權
{: #config_permissions_roles_managing_apis}

若要在 API Manager 中配置角色的「許可權」，請完成下列步驟。

1. 在 API Manager「**儀表板**」中，按一下您要使用的「型錄」。

2. 按一下**設定** > **許可權**。即會顯示您可指派角色的「產品管理許可權」：
  - **編譯打包**：容許將「產品」編譯打包到「型錄」。
  - **檢視**：容許在「型錄」中檢視及列出「產品」。
  - **管理**：容許管理「產品」生命週期（發佈、淘汰、棄用及保存）。
  - **核准**：啟用「產品」生命週期狀態變更的核准功能。
**附註：**所有開發「型錄」都已停用「產品」生命週期狀態變更的核准功能。

3. 若要將「角色」新增至**編譯打包**、**檢視**或**管理**許可權，請按一下相對應的 **+** 圖示。下列清單顯示預設的可用角色：
  - 管理者
  - 產品管理員
  - API 開發人員
  - 發佈者
「擁有者」角色具有所有許可權。

4. 啟用「產品」生命週期狀態變更的核准功能，方法為選取必要的勾選框，然後按一下相對應的 **+** 圖示，以指派有權核准生命週期狀態變更的角色。所選取的生命週期狀態變更是您要對其強制執行核准的項目。例如，如果您選取「發佈」，但清除了其他項目，則在任何人嘗試發佈「產品」時需要核准，但任何其他生命週期狀態變更都不需要核准。
5. 若要指派有權管理使用者定義原則的角色，請按一下「**原則管理**」區段中的 **+** 圖示。即會顯示原則管理許可權，讓您視需要指派角色。
6. 按一下**儲存**圖示。

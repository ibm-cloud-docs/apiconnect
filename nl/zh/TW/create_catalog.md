---

copyright:
  years: 2017
lastupdated: "2017-10-24"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 配置型錄
{: #create_catalog}

您可以建立及配置「API Manager 型錄」。若要區隔「產品」與 API，以在使其可供「開發人員」組織使用之前進行測試，則型錄很有幫助。配置「型錄」時，您也可以配置自訂品牌，如此就不需要使用 API Manager 所提供的預設 API URL。

完成下列步驟，以建立「型錄」：

1. 按一下**導覽至** <img alt="「導覽至」圖示" src="images/navigate_to_icon.png"> > **儀表板**。

2. 按一下 **+ 新增** > **型錄**。即會顯示「**新增型錄**」視窗。

3.  在**顯示名稱**欄位中，輸入新「型錄」的名稱。

4. 在**名稱**欄位中，輸入您要用來構成 URL 之「型錄」區段的文字。**附註：****名稱**欄位只能包含小寫英數字元（a-z 和 0-9）或連字號字元 (-)。連字號不能用來作為名稱的第一個或最後一個字元。

5. 按一下**新增**。即會在儀表板上建立及顯示「型錄」。

6. 若要配置「型錄」，請按一下「型錄」的名稱，按一下**設定** > **資訊**，然後繼續執行下列步驟：
  1. 如果新的「型錄」是開發「型錄」，請選取**開發模式**。如果您選取開發模式，則會強制執行編譯打包和發佈動作，這表示如果您重新發佈先前已發佈的「產品」，則會改寫該產品而不發出警告。如果發現衝突，系統會自動解決這些衝突。取消發佈動作會自動執行。

**附註：**開發「型錄」不會顯示「核准」方框。您無法為生命週期啟用核准處理程序。
  2. 如果您要啟用「型錄」的自動訂閱，請選取**自動訂閱**。啟用自動訂閱可讓測試 API 變得更簡單，因為會使用測試應用程式並搭配預先提供的用戶端 ID 及用戶端密碼。測試應用程式會自動訂閱「型錄」中的所有「方案」，因此在測試時不需要指定方案或應用程式。**附註：**自動訂閱僅適用於開發「型錄」。
  3. 如果「型錄」是預設編譯打包「型錄」，請選取**預設**。然後，呼叫發佈至「型錄」的 API 可以使用不包含「型錄」名稱的較短 URL。您只能夠對一個「型錄」選取**預設**。**附註：**
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
{: #apic_spaces_create_catalog}

若要在 {{site.data.keyword.apiconnect_short}} 中使用聯合特性，您必須在任何需要聯合功能的「型錄」中啟用「空間」。

若要在「型錄」中啟用「空間」，請完成下列步驟：
1. 在 API Manager 使用者介面的「儀表板」上，選取您要使用的「型錄」。

2. 按一下**設定** > **概觀**，然後按一下**空間**調節器控制項。

3. 在**啟用空間**視窗中，按一下**啟用**，然後按一下**儲存**圖示 <img src="images/icon_save.png" alt="「儲存」圖示"/>。即會在**空間**調節器控制項下方顯示**管理空間**鏈結，並將**空間**鏈結新增至導覽窗格。按一下下列任一個鏈結，即可管理「空間」。

即會啟用「型錄」的「空間」，並建立預設「空間」（稱為「新空間」）。

如需使用聯合的相關資訊，請參閱 Knowledge Center 主題：[在 IBM API Connect 中使用聯合 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}。

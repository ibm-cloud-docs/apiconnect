---

copyright:
  years: 2019
lastupdated: "2019-3-14"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 2-legged OAuth による API の保護
{: #tut_secure_oauth_2}

所要時間: 10 分  
スキル・レベル: ビギナー

## 目標
{: #object_tut_secure_oauth_2}

このチュートリアルでは、2-legged OAuth 2.0 のフローを使用して API を保護する手順を取り上げます。 このアプリケーション・フローの場合、OAuth クライアントは、許可サーバーへの要求を開始して、アクセス・トークンを受け取ります。 OAuth クライアントは、そのトークンを使用して、API 経由で保護リソースにアクセスできます。

## 前提条件
{: #prereq_tut_secure_oauth_2}

開始する前に、以下のチュートリアルを完了しておく必要があります。  
- [クライアント ID とクライアント秘密鍵による API の保護 ({{site.data.keyword.Bluemix}}](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_bm) を使用する場合)
または
- [クライアント ID とクライアント秘密鍵による API の保護 (ツールキットを使用する場合)](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_id_secret_tk)

注: このチュートリアルでは、{{site.data.keyword.Bluemix}} UI 内でタスクを実行する手順とスクリーン・ショットを紹介します。 コマンド・ラインでも同じ手順を行うことができます。 その手順については、[IBM Knowledge Center ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tutorial_apionprem_security_OAuth_v506.html){: #new_window} を参照してください。 

## 手順
{: #steps_tut_secure_oauth_2}

1. OAuth プロバイダー API を作成し、OAuth スキームを選択します。  
	a. **「ドラフト」**を開き、**「API」**を選択し、**「追加」**>**「OAuth 2.0 プロバイダー API」**をクリックします。  
    ![](images/oauth_provider_1.png)
	b. 「OAuth Endpoint API」というタイトルを付けます。 名前と基本パスのデータは自動的に取り込まれます。  
	c. **「API の作成」**を選択します。  
	d. 新しく作成した OAuth Endpoint API で**「OAuth 2」**パネルに移動して (スクロールダウンして)、クライアント・タイプとして「機密」を選択します。  
	e. 「スコープ」で _scope1_ という名前を _view_current_ に変更します。 _scope2_ と _scope3_ は削除します。  
	![](images/oauth_provider_type_scope.png) 
	
	f. **「付与」**で、**「暗黙」**、**「パスワード」**、**「アクセス・コード」**を選択解除します。 **「アプリケーション」**は選択したままにします。  
	![](images/oauth_provider_grants.png)  
	
	g. API を保存します。  

2. Weather Provider API のセキュリティー定義を更新して OAuth を組み込みます。  
	a. _Weather Provider API_ に切り替えます。 (「API」に戻ってから _Weather Provider API_ を選択します。)  
	![](images/oauth_weatherapi_info.png)
	
	b. 「セキュリティー定義」で、**+** アイコンをクリックして、OAuth の新しい定義を追加します。
	![](images/oauth_add_security.png)
	c. 「OAuth definition」という名前に設定します。  
	d. 「フロー」フィールドで**「アプリケーション」**を選択します。  
	e. トークンの URL (_**基本 URL**/oauth-endpoint-api/oauth2/token_) を入力します。  
	![](images/oauth_secdef_top.png)
	
	f. 新しいスコープ view_current を追加します。  
	![](images/oauth_secdef_scopes.png)
	g. **「セキュリティー」**で **OAuth Definition** と **view_current** を選択し、クライアント ID とクライアント秘密鍵を選択した状態のままにします。  
	![](images/oauth_security_oauth.png)
	
	h. 「保存」をクリックします。  
	
	i. **「ドラフト」**に戻って、**「製品」**を選択します。  **「Weather Provider API product」**を開きます。
	![](images/weatherapi_prod_info.png)
	
	j. ナビゲーション・バーで**「API」**をクリックします。**+** アイコンをクリックして、新しい API を追加します。OAuth Endpoint API を Weather Provider 製品に追加します。  
	![](images/weatherapi_prod_apis.png)
	k. 製品を保存し、それをサンドボックスにステージングします。  
	![](images/oauth_security_definition_3a.png)

3. OAuth セキュリティー構成をテストします。  
	a. 更新版の製品をサンドボックスに公開します。 **「ダッシュボード」>「サンドボックス」**をクリックして、製品を公開します。  
	  ![](images/test_oauth_1.png)
	b. 「可視性」ダイアログでデフォルトを受け入れます。**「公開」**をクリックします。
	  ![](images/pub_visibility.png)
	  
	c. **「探索」>「サンドボックス」**をクリックします。  
      ![](images/test_oauth_2.png)
	d. **Weather Provider API** の操作のリストで **GET /current** をクリックします。 
	
	e. **「試行 (Try It)」**をクリックします。 
	
	f. 右側のパネルで、クライアント ID とクライアント秘密鍵のデータが既に取り込まれていることを確認します。  
	
	g. **「パラメーター」**セクションの**「郵便番号 (zipcode)」**フィールドに _10504_ と入力します。  
	  ![](images/weather_oauth_explorer_param.png)
	
	h. **「許可」**セクションで、**「許可」**をクリックしてアクセス・トークンを取得します。
	  ![](images/weather_oauth_explorer_auth.png)
	
	i. アクセス・トークンを受け取ったら、**「操作の呼び出し」**をクリックしてテストを実行します。  
      ![](images/test_oauth_4.png)

4. この要求には、アクセス・トークン、クライアント ID、クライアント秘密鍵が含まれています。 要求でアクセス・トークンだけを渡すには、Weather Provider API のセキュリティー要件からクライアント ID とクライアント秘密鍵を除外する必要があります。  
    ![](images/test_oauth_5.png)

5. Weather Provider API を保存します。 それをサンドボックスにステージングしてから公開します。 前と同じ要領で「探索」ツールから同じテストを実行します。  
    ![](images/test_oauth_6.png)
    
## まとめ
{: #conclusion_tut_secure_oauth_2}

このチュートリアルでは、OAuth Provider API を作成する方法、API のセキュリティー定義を更新して OAuth を組み込む方法、セキュリティー構成をテストする方法を学習しました。

---

## 次のステップ
{: #next_tut_secure_oauth_2}

[開発者ポータルのセットアップと構成](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_config_dev_portal)に進んで、API のソーシャル化を開始します。

作成 > 管理 > **保護** > ソーシャル化 > 分析

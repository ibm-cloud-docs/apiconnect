---

copyright:
  years: 2019
lastupdated: "2019-3-11"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# SOAP サービスの管理
{: #tut_manage_soap_api}

**所要時間**: 15 分
**スキル・レベル**: ビギナー

---
## 目標
{: #object_tut_manage_soap_api}

このチュートリアルでは、API Manager を使用して、SOAP ベースの天候サービスのプロキシーとしての役割を果たす SOAP API を作成します。

## 前提条件
{: #prereq_tut_manage_soap_api}

- 始める前に、[{{site.data.keyword.apiconnect_short}} インスタンスのセットアップ](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)を行う必要があります。
- 始める前に、[weatherprovider.wsdl テスト ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){: #new_window} ファイルをローカル・ファイル・システムにコピーしてください。
注: **「未加工 (Raw)」**をクリックし、結果のページを `.wsdl` ファイルとしてローカル・システムに保存することもできます。 この SOAP サービスは、名前のとおり、郵便番号の入力に対して天候データを返します。

---
## SOAP API 定義のセットアップ
{: #setup_tut_manage_soap_api}

1. {{site.data.keyword.Bluemix_short}} (https://cloud.ibm.com) にログインします。
2. {{site.data.keyword.Bluemix_notm}} の**ダッシュボード**で、**「Cloud Foundary サービス (Cloud Foundary Services)」**をクリックします。 
3. {{site.data.keyword.apiconnect_short}} サービスを起動します。 
4. {{site.data.keyword.apiconnect_short}} で、左側にナビゲーション・パネルが開いていることを確認します。 表示されていない場合は、**「>>」**をクリックして開きます。  
5. ナビゲーション・パネルで**「ドラフト」** を選択します。   

6. ドロップダウン・メニューで**「SOAP サービスからの API」**を選択します。
![新規 API](images/newapi-menu2.png)

7. 「WSDL による新規 API」ダイアログ・ボックスが開きます。 **「ファイルのアップロード」**をクリックします。
![ .wsdl file のアップロード](images/4-uploadwsdl.png)

8. 前に保存した `weatherprovider.wsdl` ファイルを選択します。

9. 「WSDL による新規 API」ダイアログ・ボックスが再表示されます。 **weatherService** のチェック・ボックスにチェック・マークを付けます。 **「完了」**をクリックします。
![天候サービスの選択](images/newapi2.png)

10. インポートが成功すると、API の「設計」ビューが表示されます。 また、「ソース」タブには OpenAPI 定義が表示されています。
   _「ソース」タブで、WSDL が OpenAPI 定義の中にラップされていることを確認できます。
_![API エディター・ページ](images/designpage2.png)

11. ![「保存」](images/save.png)アイコンをクリックして、変更内容を保存します。 「API が保存されました」という確認通知が一瞬表示されます。

12. **「設計」**タブでは、保存アイコンのあるメニュー・バーで現在の場所を確認できます。 その横にある**「ソース」**タブでは、API を示す Swagger (2.0) ファイルを直接確認できます。その横にある**「アセンブル」**タブでは、ドラッグ・アンド・ドロップ・インターフェースで API を処理できます。 **「アセンブル」**をクリックします。
![「アセンブル」タブ](images/assemble-clean.png)  

## SOAP API 定義のテスト
{: #test_tut_manage_soap_api}

1. **「アセンブル」**タブで、**「その他のアクション」**(3 つのドット) アイコンをクリックし、メニューから**「デフォルト製品の生成」**を選択します。  
   ![「その他のアクション」メニューを開く](images/gen-default-prod.png)

2. **「新規製品」**ダイアログ・ポップアップでデフォルト・オプションを受け入れ、**「製品の作成」**を選択します。 **weatherService product 1.0.0** が作成され、サンドボックス・カタログに公開されます。  
  ![新しい製品の作成](images/12a-chooseproduct.png)
 
  _{{site.data.keyword.apiconnect_short}} では、**製品**という形で、API を用途ごとにグループ分けできます。 製品は**カタログ**に公開されます。 参照: [{{site.data.keyword.apiconnect_short}} 用語集](docs/services/apiconnect/tutorials/tut_expose_soap_service/apic_glossary.html)_

3. 変更を保存します。  

4. 検索ボックスの横にあるテスト・アイコンをクリックして、API サービスをテストします。 「セットアップ」メニューが表示されます。

5. 製品リストから `weatherService product 1.0.0` を選択します。  
  ![choose weather service](images/12-chooseproduct.png)

6. 一番下までスクロールして、**「次へ」**をクリックします。

7. 操作のリストから `post /weatherRequest` を選択します。  
  ![要求の送信](images/13-selectoperation.png)

8. スクロールダウンします。 本文フィールドに以下の XML を入力します。 以下のサンプル XML を選択してコピーし、**本文**フィールドをクリックしてアクティブにしてから、そのサンプル XML を貼り付けます。  
  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
   <soap:Body>
  <wdata:WeatherRequest xmlns:wdata="http://www.ibm.com/wdata">
       <zipcode>10504</zipcode>
  </wdata:WeatherRequest>
   </soap:Body>
  </soap:Envelope>
  ```
 
  ![要求](images/14-enterrequest.png)

9. 必要ならスクロールダウンして、**「呼び出し」**をクリックします。
現在の天候を示す応答の**本文**が API から返されます。  
  ![](images/15-success.png)

## まとめ
{: #conclusion_tut_manage_soap_api}

このチュートリアルでは、以下を実行しました。
1. SOAP API 定義をセットアップしました
2. API 定義をテストしました
3. 天候 API エンドポイントから要求の結果を示す応答の**本文**を受け取りました。

---

## 次のステップ
{: #next_tut_manage_soap_api}

[サービスを REST API として公開する](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_expose_soap_service)か、[OAuth 2.0 を使用した保護](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)を用いて API を保護します。

作成 > **管理** > 保護 > ソーシャル化 > 分析

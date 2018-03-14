---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# SOAP サービスの管理
**所要時間**: 15 分
**スキル・レベル**: ビギナー

---
## 目標
このチュートリアルでは、API Manager を使用して、SOAP ベースの天候サービスのプロキシーとしての役割を果たす SOAP API を作成します。

## 前提条件
- 始める前に、[{{site.data.keyword.apiconnect_short}} インスタンスのセットアップ](tut_prereq_set_up_apic_instance.html)が必要です。
- 始める前に、[weatherprovider.wsdl テスト ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weatherprovider.wsdl){:new_window} ファイルをローカル・ファイル・システムにコピーしてください。
注: **「未加工 (Raw)」**をクリックし、結果のページを `.wsdl` ファイルとしてローカル・システムに保存することもできます。 この SOAP サービスは、名前のとおり、郵便番号の入力に対して天候データを返します。

---
## SOAP API 定義のセットアップ
1. {{site.data.keyword.Bluemix_short}} にログインします ([https://new-console.ng.bluemix.net/login](https://new-console.ng.bluemix.net/login){:new_window})。

2. {{site.data.keyword.Bluemix_notm}} **ダッシュボード**で**「すべてのサービス」**までスクロールダウンします。

3. **「API Connect」**を選択して、{{site.data.keyword.apiconnect_short}} サービスを起動します。 
  
4. 「ドラフト」ページがまだ表示されていなければ、そのページに移動します。  
    a. {{site.data.keyword.apiconnect_short}} インターフェースで「>>」をクリックしてナビゲーション・パネルを開きます。
    b. ナビゲーション・パネルで**「ドラフト」** をクリックします。
    c. **「API」**タブに進みます。

5. 「API」タブで`「追加 +」`をクリックします。

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

11. **「セキュリティー」**タブまでスクロールダウンし、削除アイコンをクリックして、サービスの作成時に自動的に生成された `clientIDHeader (API キー)` を削除します。
   _API キーによるセキュリティーについては、次のチュートリアルで学びます。_

12. ![「保存」](images/save.png)アイコンをクリックして、変更内容を保存します。 「API が保存されました」という確認通知が一瞬表示されます。

13. **「設計」**タブでは、保存アイコンのあるメニュー・バーで現在の場所を確認できます。 その横にある**「ソース」**タブでは、API を示す Swagger (2.0) ファイルを直接確認できます。その横にある**「アセンブル」**タブでは、ドラッグ・アンド・ドロップ・インターフェースで API を処理できます。 **「アセンブル」**をクリックします。
![「アセンブル」タブ](images/assemble-clean.png)  

## SOAP API 定義のテスト

1. **「アセンブル」**タブで、**「その他のアクション」**(3 つのドット) アイコンをクリックし、メニューから**「デフォルト製品の生成」**を選択します。  
   ![「その他のアクション」メニューを開く](images/gen-default-prod.png)

2. **「新規製品」**ダイアログ・ポップアップでデフォルト・オプションを受け入れ、**「製品の作成」**を選択します。 **weatherService product 1.0.0** が作成され、サンドボックス・カタログに公開されます。  
  ![新しい製品の作成](images/12a-chooseproduct.png)
 
  _{{site.data.keyword.apiconnect_short}} では、**製品**という形で、API を用途ごとにグループ分けできます。 製品は**カタログ**に公開されます。 [{{site.data.keyword.apiconnect_short}} 用語集](../apic_glossary.html)を参照してください_

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
  {: codeblock}  
  ![要求](images/14-enterrequest.png)

9. 必要ならスクロールダウンして、**「呼び出し」**をクリックします。
現在の天候を示す応答の**本文**が API から返されます。  
  ![](images/15-success.png)

## このチュートリアルで学習した内容
このチュートリアルでは、以下を実行しました。
1. SOAP API 定義をセットアップしました
2. API 定義をテストしました
3. 天候 API エンドポイントから要求の結果を示す応答の**本文**を受け取りました。

---

## 次のステップ

[サービスを REST API として公開する](tut_expose_soap_service.html)か、[レート制限](tut_rate_limit.html)、[クライアント ID と秘密鍵](tut_secure_landing.html)、[OAuth 2.0 を使用した保護](tut_secure_oauth_2.html)のいずれかを使用して API を保護します。

作成 > **管理** > 保護 > ソーシャル化 > 分析

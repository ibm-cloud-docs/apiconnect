---

copyright:
  years: 2019
lastupdated: "2017-3-15"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 製品の置換
{: #tut_manage_replace}

**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 目標
{: #object_tut_manage_replace}
このチュートリアルでは、既存の API 製品を新しい製品に置換して更新します。 API 製品を置換すると、変更内容がすぐに有効になり、すべてのアプリケーションのサブスクリプションが自動的に更新されます。  

---
## 前提条件
{: #prereq_tut_manage_replace}

1. [{{site.data.keyword.apiconnect_full}} インスタンスをセットアップ](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)します。

2. 以下のいずれかのチュートリアルを完了します。
 
    - [OpenAPI2.0 仕様のインポートと既存の REST サービスへのプロキシー作成](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)
       **または**  
    - [新しい API 仕様の追加と既存の REST サービスの呼び出し](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing)

---

## API 製品の置換
{: #repl_api_prod_tut_manage_replace}}

1. {{site.data.keyword.Bluemix_short}} (https://cloud.ibm.com) にログインします。
2. {{site.data.keyword.Bluemix_notm}} の**ダッシュボード**で、**「Cloud Foundary サービス (Cloud Foundary Services)」**をクリックします。{{site.data.keyword.apiconnect_short}} サービスを起動します。 
3. {{site.data.keyword.apiconnect_short}} でナビゲーション・パネルが開いていることを確認します。 表示されていない場合は、**「>>」**をクリックして開きます。  

  ![](images/cloud-apic-dashboard.png)

4. **「ドラフト」** > **「API」**をクリックします。

5. 「API」パネルで **Weather Provider API** をクリックして、REST プロキシー API を開きます。  
![](images/rep-api-list.png)

6. **バージョン**を 2.0.0 に変更します。  

7. ディスク・アイコンをクリックして、API の変更内容を保存します。  
![](images/rep-change-version.png)

8. **「すべての API」**をクリックします。  
![](images/rep-all-apis.png)

9. **「製品」**をクリックします。  
![](images/rep-api-list-2.png)

10.	**Weather Provider API Product** を選択します。  
![](images/rep-draft-prod-list.png)

11.	**バージョン**を 2.0.0 に変更します。 **「説明」**フィールドに `Updated API` と入力します。 ディスク・アイコンをクリックして、変更内容を保存します。  
![](images/rep-update-prod.png)

12.	**「ステージ」**アイコンをクリックして、新しいバージョンをアップロードします。 **「サンドボックス」** カタログが選択されていない場合は選択します。
![](images/rep-stage-prod-2.png)
    **注**: 新しいバージョンを別のカタログにステージングすることも可能です。そうすれば、そのバージョンの対象者をどの開発者にするかを制御できます。 開発、テスト、実動という順序で API 製品を移す時にこの機能を使用できます。

13.	**「>>」**をクリックしてナビゲーション・メニューを開き、**「ダッシュボード」**を選択します。  
![](images/rep-dashboard.png)

14.	**「サンドボックス」**をクリックします。  

15.	**Weather Provider API Product 2.0.0 Staged** の行にある縦の省略符号をクリックします。  
![](images/rep-dash-prod-list-2.png)

16.	**「既存の製品の置換」**を選択します。  
![](images/rep-replace-prod.png)

17.	表示される製品リストで **Weather Provider API Product 1.0.0** を選択します。 **「次へ」**をクリックします。  
![](images/rep-replace-dialog.png)

18.	**「デフォルトのプラン」**を選択します。 **「置換」**をクリックします。  
![](images/rep-replace-dialog-2.png)

    このようにして置換すると、Weather Provider API Product 1.0.0 が破棄され、Weather Provider API Product 2.0.0 が公開されます。 **注**: 置換プロセスでこの製品に関連付けるプランを変更することも可能です。 そのようにして、API 製品のプランを簡単に変更できます。
 ![](images/rep-prod-retired.png) 
 

## まとめ
{: #conclusion_tut_manage_replace}

このチュートリアルでは、以下のアクティビティーを実行しました。
1. API 製品を更新しました。
2. 既存の API 製品を更新版の API 製品に置換しました。

---













---

copyright:
  years: 2019
lastupdated: "2017-3-18"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 製品の取り替え
{: #tut_manage_supercede}

**所要時間**: 15 分  
**スキル・レベル**: ビギナー  

## 目標
{: #object_tut_manage_supercede}

このチュートリアルでは、既存の API を新しい API に取り替えます。

---
## 前提条件
{: #prereq_tut_manage_supercede}

1. [{{site.data.keyword.apiconnect_full}} インスタンスをセットアップ](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)します。

2. [API 製品の置換のチュートリアル](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace)を完了します。

---

## API 製品の取り替え
{: #super_tut_manage_supercede}

1. {{site.data.keyword.Bluemix_short}} (https://cloud.ibm.com) にログインします。
2. {{site.data.keyword.Bluemix_notm}} の**ダッシュボード**で、**「Cloud Foundary サービス (Cloud Foundary Services)」**をクリックします。{{site.data.keyword.apiconnect_short}} サービスを起動します。 
3. {{site.data.keyword.apiconnect_short}} でナビゲーション・パネルが開いていることを確認します。 表示されていない場合は、**「>>」**をクリックして開きます。  

  ![](images/cloud-apic-dashboard.png)

4. **「ドラフト」** > **「API」**をクリックします。

5. 「API」パネルで **Weather Provider API** をクリックして、REST プロキシー API を開きます。  
![](images/rep-api-list.png)

6. **バージョン**を 3.0.0 に変更します。

7. ディスク・アイコンをクリックして、API の変更内容を保存します。  
![](images/sup-change-version.png)

8. **「すべての API」**をクリックします。  
![](images/rep-all-apis.png)

9. **「製品」**をクリックします。  
![](images/sup-prods.png)

10.	**Weather Provider API Product 2.0.0** を選択します。  
![](images/sup-draft-prod-list.png)

11.	**バージョン**を 3.0.0 に変更します。 ディスク・アイコンをクリックして、変更内容を保存します。 **「ステージ」**アイコンをクリックします。  
![](images/sup-change-prod-vers-3.png)

12.	**「>>」**をクリックしてナビゲーション・ペインを開き、**「ダッシュボード」**を選択します。  
![](images/rep-dashboard.png)

13.	**「サンドボックス」**をクリックします。

14.	**「コミュニティー」**をクリックします。  
![](images/sup-sand-dash.png)

15.	**「サブスクリプション」**をクリックします。  
![](images/sup-comm-orgs.png)

16.	アプリケーションのサブスクリプションの対象が Weather Provider API Product 2.0.0 であることを確認します。 **「製品」**をクリックします。
![](images/sup-scriptions-200.png)  

17.	**Weather Provider API Product 3.0.0 Staged** の行にある縦の省略符号をクリックします。  
![](images/sup-stage-prod-3.png)

18.	**「既存の製品の取り替え」**を選択します。  
![](images/sup-super-prod.png)

19.	表示される製品リストで **Weather Provider API Product 2.0.0** を選択します。 **「次へ」**をクリックします。  
![](images/sup-super-dialog-1.png)

20.	**「デフォルトのプラン」**を選択します。 **「取り替え」**をクリックします。  
![](images/sup-super-dialog-2.png)
    このようにして取り替えると、Weather Provider API Product 2.0.0 が非推奨になり、Weather Provider API Product 3.0.0 が公開されます。  
![](images/sup-dash-prods-3.png) 
 
21.	**「コミュニティー」>>「サブスクリプション」**をクリックします。  
![](images/sup-scriptions-200.png)
 
22.	**Weather Provider API Product 2.0.0** の行にある縦の省略符号をクリックします。 **「管理」**を選択します。  
![](images/sup-dots-manage.png) 

23.	Weather Provider API Product 3.0.0 の下で**「デフォルトのプラン」**を選択します。 **「マイグレーション」**をクリックします。  
![](images/sup-migrate-dialog.png)
    このようにマイグレーションすると、Weather Provider API Product 2.0.0 が Weather Provider API Product 3.0.0 にマイグレーションされます。  
![](images/sup-migrated.png) 
 

 
## まとめ
{: #conclusion_tut_manage_supercede}

このチュートリアルでは、以下のアクティビティーを実行しました。

1. API 製品を更新しました。
2. 既存の API 製品を更新版の API 製品に取り替えました。
3. 既存の API 製品のサブスクリプションを更新版の API 製品にマイグレーションしました。

---













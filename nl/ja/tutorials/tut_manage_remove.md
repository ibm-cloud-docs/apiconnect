---

copyright:
  years: 2017
lastupdated: "2017-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 製品のアーカイブ保存と削除
**所要時間**: 15 分  
**スキル・レベル**: ビギナー 

## 前提条件

1. [{{site.data.keyword.apiconnect_full}} インスタンスをセットアップします](tut_prereq_set_up_apic_instance.html)。

2. [API 製品の取り替えのチュートリアル](tut_manage_supercede.html)を完了します。

---
## 目標
このチュートリアルでは、API の削除、アーカイブ保存、廃棄の方法を取り上げます。

---
## API 製品の削除
1. {{site.data.keyword.Bluemix_short}} にログインします ([https://console.ng.bluemix.net/login) ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://console.ng.bluemix.net/login){:new_window}。

2. {{site.data.keyword.Bluemix_short}} ダッシュボードで {{site.data.keyword.apiconnect_short}} サービスを起動します。
![](images/Bluemix.png)

3. 以前に UI ナビゲーション・ペインをピン留めしていなかった場合は、API Manager で**「ナビゲート」**アイコン ![](images/navigate-to.png) をクリックします。 API Manager UI ナビゲーション・ペインが開きます。 UI ナビゲーション・ペインをピン留めするには、**「メニューのピン留め」**アイコン ![](images/pinned.png) をクリックします。

4. **「サンドボックス」**をクリックして、サンドボックス・カタログを開きます。 **注**: 使用可能なカタログを確認するために、ダッシュボードに戻らなければならない場合もあります。 ダッシュボード・ページで、カタログがリスト形式ではなくタイル形式で表示されることもあります。
![](images/del-sandbox-list.png)

5. **Weather Provider API 1.0.0** の行にある縦の省略符号をクリックします。  
![](images/del-prod-list1.png)

6. **「カタログから削除」**を選択します。  
![](images/del-del-from-cat.png)

7. **「OK」**をクリックします。  
![](images/del-del-dialog.png)
    カタログの製品リストからその製品が消えます。 これ以降は復元できません。


## API 製品のアーカイブ保存
1. **Weather Provider API 2.0.0** の行にある縦の省略符号をクリックします。  
![](images/del-prod-list2.png)

2. **「廃棄」**を選択します。  
![](images/del-select-retire.png)

3. **「OK」**をクリックします。  
![](images/del-retire-dialog.png)

4. **Weather Provider API 2.0.0** の行にある縦の省略符号をクリックします。  
![](images/del-prod-list3.png)

5. **「アーカイブ」**を選択します。  
![](images/del-select-archive.png)

6. **「OK」**をクリックします。  
![](images/del-archive-dialog.png)
    カタログの製品リストからその製品が消えます。 復元は可能です。

7. リスト・ビュー・アイコンをクリックします。  
![](images/del-prod-list4.png)

8. **「アーカイブ済み」**にチェック・マークを付けます。  
![](images/del-view-archived.png)

9. **Weather Provider API 2.0.0** の行にある縦の省略符号をクリックします。  
![](images/del-prod-list5.png)

10. **「解凍」**を選択します。  
![](images/del-unarchive.png)
    製品の状態が廃棄済みに変わります。
    ![](images/del-prod-list6.png)

 
 
## このチュートリアルで学習したこと
このチュートリアルでは、以下のアクティビティーを実行しました。

1. API 製品を削除しました
2. API 製品を廃棄しました
3. API 製品をアーカイブ保存しました
4. API 製品を解凍しました

---













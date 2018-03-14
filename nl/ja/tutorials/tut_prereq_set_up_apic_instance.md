---
copyright:
  years: 2017
lastupdated: "2017-10-31"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API Connect インスタンスのセットアップ
**所要時間**: 15 分  
**スキル・レベル**: ビギナー  


## 必要なもの:
1. IBMid
2. {{site.data.keyword.Bluemix_short}} アカウント
3. {{site.data.keyword.apiconnect_full}} インスタンス (少なくとも _Lite_ プラン)


<table>
  <tr><td><b>IBMid</b>: IBM のすべてのアプリケーション、コミュニティー、サポートなどにアクセスする時に使用されます
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>: {{site.data.keyword.apiconnect_short}} と他のアプリケーションやサービスをホストする IBM のクラウド・プラットフォーム<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>: {{site.data.keyword.Bluemix_notm}} でホストする無料版の {{site.data.keyword.apiconnect_short}}</td></tr>
  </table>  


---


1. IBMid を取得するための登録を行います (URL は [https://console.ng.bluemix.net/registration/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://console.ng.bluemix.net/registration/){:new_window})。

	IBMid を既に持っている場合は、登録をスキップして、無料の {{site.data.keyword.Bluemix_short}} アカウントを作成します (URL は [https://console.ng.bluemix.net/ ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://console.ng.bluemix.net/){:new_window})。  

2. IBMid と {{site.data.keyword.Bluemix_notm}} アカウントがそろったら、{{site.data.keyword.apiconnect_short}} インスタンスを作成します。  
  a. {{site.data.keyword.Bluemix_notm}} にログインします ([https://new-console.ng.bluemix.net/login) ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://new-console.ng.bluemix.net/login){:new_window}。  
  ![](images/prereqs-1.png)  
  b. {{site.data.keyword.Bluemix_notm}} で_組織_ を作成します。 初めてログインした時に、その作業を求める画面が表示されます。  
  ![](images/prereqs-2.png)
  c. _スペース_ を作成します。  
  ![](images/prereqs-3.png)
  d. [https://console.ng.bluemix.net/catalog/services/api-connect ![外部リンクのアイコン](../../../icons/launch-glyph.svg "外部リンクのアイコン")](https://console.ng.bluemix.net/catalog/services/api-connect){:new_window} にアクセスします。  
  ![](images/prereqs-4.png)  
  e. _Lite_ の価格設定プラン (無料) を選択し、**「作成」**をクリックして、作業を開始します。  
  ![](images/lite-plan.png)  

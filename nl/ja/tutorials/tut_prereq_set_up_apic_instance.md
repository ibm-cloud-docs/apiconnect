---

copyright:
  years: 2019
lastupdated: "2019-3-14"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorials

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API Connect インスタンスのセットアップ
{: #tut_prereq_set_up_apic_instance}

**所要時間**: 15 分  
**スキル・レベル**: ビギナー  


## 前提条件
{: #prereq_tut_prereq_set_up_apic_instance}

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


1. IBM Cloud ID を取得するための登録を行います (URL: [https://cloud.ibm.com/registration/ ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン")](https://cloud.ibm.com/registration/){: #new_window})。

	IBMid を既にお持ちの場合には、登録をスキップして、無料の {{site.data.keyword.Bluemix_short}} アカウントを作成します (URL: [https://cloud.ibm.com/ ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン")](https://cloud.ibm.com/){: #new_window})。  

2. IBMid と {{site.data.keyword.Bluemix_notm}} アカウントがそろったら、{{site.data.keyword.apiconnect_short}} インスタンスを作成します。  
  a. {{site.data.keyword.Bluemix_notm}} ([https://cloud.ibm.com/login ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン")](https://cloud.ibm.com/login){: #new_window}) にログインします。  
  ![](images/cloud_login_page.png)  
  b. {{site.data.keyword.Bluemix_notm}} で_組織_ を作成します。 初めてログインした時に、その作業を求める画面が表示されます。  
  ![](images/prereqs-2.png)
  c. _スペース_ を作成します。  
  ![](images/prereqs-3.png)
  d. [https://console.ng.bluemix.net/catalog/services/api-connect ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window} にアクセスします。  
  ![](images/prereqs-4.png)  
  e. _Lite_ の価格設定プラン (無料) を選択し、**「作成」**をクリックして、作業を開始します。  
  ![](images/lite-plan.png)  

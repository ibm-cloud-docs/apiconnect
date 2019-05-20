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

# API Connect 인스턴스 설정
{: #tut_prereq_set_up_apic_instance}

**소요 시간**: 15분  
**스킬 레벨**: 초보자  


## 전제조건
{: #prereq_tut_prereq_set_up_apic_instance}

1. IBM ID
2. {{site.data.keyword.Bluemix_short}} 계정
3. _Lite_ 플랜 이상의 {{site.data.keyword.apiconnect_full}} 인스턴스


<table>
  <tr><td><b>IBM ID</b>: IBM의 앱, 커뮤니티, 지원 등에 모두 액세스하는 데 사용
    <br>
    <b>{{site.data.keyword.Bluemix_notm}}</b>: 다른 앱 및 서비스와 함께 {{site.data.keyword.apiconnect_short}}를 호스트하는 IBM의 클라우드 플랫폼<br>
    <b>{{site.data.keyword.apiconnect_short}} Lite</b>: {{site.data.keyword.Bluemix_notm}}에서 호스팅되는 {{site.data.keyword.apiconnect_short}}의 무료 버전</td></tr>
  </table>  


---


1. 다음 URL에서 IBM Cloud ID에 등록하십시오. [https://cloud.ibm.com/registration/ ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/registration/){: #new_window}.

	이미 IBM ID가 있습니까? 그러면 등록을 건너뛰고 다음 URL에서 무료 {{site.data.keyword.Bluemix_short}} 계정을 작성하십시오. [https://cloud.ibm.com/ ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/){: #new_window}.  

2. IBM ID와 {{site.data.keyword.Bluemix_notm}} 계정이 있으면 {{site.data.keyword.apiconnect_short}} 인스턴스를 작성하십시오.  
  a. {{site.data.keyword.Bluemix_notm}}에 로그인하십시오. [https://cloud.ibm.com/login ![외부 랑크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/login){: #new_window}.  
  ![](images/cloud_login_page.png)  
  b. {{site.data.keyword.Bluemix_notm}}에 _조직_을 작성하십시오. 처음 로그인할 때 이 작업을 수행하도록 프롬프트가 표시됩니다.  
  ![](images/prereqs-2.png)
  c. _영역_을 작성하십시오.  
  ![](images/prereqs-3.png)
  d. [https://console.ng.bluemix.net/catalog/services/api-connect ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/catalog/services/api-connect){: #new_window}로 이동하십시오.  
  ![](images/prereqs-4.png)  
  e. _Lite_ 가격 플랜(무료)을 선택하고 **작성**을 클릭하여 시작하십시오.  
  ![](images/lite-plan.png)  

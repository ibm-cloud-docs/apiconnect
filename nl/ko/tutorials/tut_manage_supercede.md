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

# API 제품 대체
{: #tut_manage_supercede}

**소요 시간**: 15분  
**스킬 레벨**: 초보자  

## 목표
{: #object_tut_manage_supercede}

이 튜토리얼에서는 기존 API를 새 API로 대체합니다.

---
## 전제조건
{: #prereq_tut_manage_supercede}

1. [{{site.data.keyword.apiconnect_full}} 인스턴스를 설정](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)하십시오.

2. [API 제품 바꾸기 튜토리얼](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace)을 완료하십시오.

---

## API 제품 대체
{: #super_tut_manage_supercede}

1. {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com에 로그인하십시오.
2. {{site.data.keyword.Bluemix_notm}} **대시보드**에서 **Cloud Foundary 서비스**를 클릭하십시오.{{site.data.keyword.apiconnect_short}} 서비스를 시작하십시오. 
3. {{site.data.keyword.apiconnect_short}}에서 탐색 패널이 열려 있는지 확인하십시오. 열려 있지 않으면 **>>**를 클릭하여 여십시오.  

  ![](images/cloud-apic-dashboard.png)
4. **드래프트** > **API**를 클릭하십시오.

5. API 패널에서 **Weather Provider API**를 클릭하여 REST 프록시 API를 여십시오.  
![](images/rep-api-list.png)

6. **버전**을 3.0.0으로 변경하십시오.

7. 디스크 아이콘을 클릭하여 API 변경사항을 저장하십시오.  
![](images/sup-change-version.png)

8. **모든 API**를 클릭하십시오.  
![](images/rep-all-apis.png)

9. **제품**을 클릭하십시오.  
![](images/sup-prods.png)

10.	**Weather Provider API 제품 2.0.0**을 선택하십시오.  
![](images/sup-draft-prod-list.png)

11.	**버전**을 3.0.0으로 변경하십시오. 디스크 아이콘을 클릭하여 변경사항을 저장하십시오. **스테이지** 아이콘을 클릭하십시오.  
![](images/sup-change-prod-vers-3.png)

12.	**>>**를 클릭하여 탐색 분할창을 열고 **대시보드**를 선택하십시오.  
![](images/rep-dashboard.png)

13.	**샌드박스**를 클릭하십시오.

14.	**커뮤니티**를 클릭하십시오.  
![](images/sup-sand-dash.png)

15.	**등록**을 클릭하십시오.  
![](images/sup-comm-orgs.png)

16.	Weather Provider API 제품 2.0.0에 대한 애플리케이션 등록을 기록해 두십시오. **제품**을 클릭하십시오.
![](images/sup-scriptions-200.png)  

17.	**Weather Provider API 제품 3.0.0 스테이징됨** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/sup-stage-prod-3.png)

18.	**기존 제품 대체**를 선택하십시오.  
![](images/sup-super-prod.png)

19.	표시된 제품 목록에서 **Weather Provider API 제품 2.0.0**을 선택하십시오. **다음**을 클릭하십시오.  
![](images/sup-super-dialog-1.png)

20.	**기본 플랜**을 선택하십시오. **대체**를 클릭하십시오.  
![](images/sup-super-dialog-2.png)
    이와 같이 바꾸기를 수행하면 Weather Provider API 제품 2.0.0이 더 이상 사용되지 않고 Weather Provider API 제품 3.0.0이 공개됩니다.  
![](images/sup-dash-prods-3.png) 
 
21.	**커뮤니티 >> 등록**을 클릭하십시오.  
![](images/sup-scriptions-200.png)
 
22.	**Weather Provider API 제품 2.0.0** 행에서 세로 생략 기호를 클릭하십시오. **관리**를 선택하십시오.  
![](images/sup-dots-manage.png) 

23.	Weather Provider API 제품 3.0.0에서 **기본 플랜**을 선택하십시오. **마이그레이션**을 클릭하십시오.  
![](images/sup-migrate-dialog.png)
    이와 같이 마이그레이션하면 Weather Provider API 제품 2.0.0이 Weather Provider API 제품 3.0.0으로 마이그레이션됩니다.  
![](images/sup-migrated.png) 
 

 
## 결론
{: #conclusion_tut_manage_supercede}

이 튜토리얼에서 다음 활동을 완료했습니다.

1. API 제품 업데이트.
2. 기존 API를 업데이트된 API 제품으로 대체
3. 기존 API 제품의 등록을 업데이트된 API 제품으로 마이그레이션

---













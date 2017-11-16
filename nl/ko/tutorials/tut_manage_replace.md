---

copyright:
  years: 2017
lastupdated: "2017-10-19"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 제품 바꾸기
**기간**: 15분  
**스킬 레벨**: 초보자  


## 전제조건

1. [{{site.data.keyword.apiconnect_full}} 인스턴스를 설정하십시오](tut_prereq_set_up_apic_instance.html).

2. 다음 튜토리얼 중 하나를 완료하십시오.
 
    - [OpenAPI2.0 스펙 가져오기 및 기존 REST 서비스 프록시](tut_rest_landing.html)
**또는**  
    - [새 API 스펙 추가 및 기존 REST 서비스 호출](tut_rest_landing.html).

---
## 목표
이 튜토리얼에서는 기존 API 제품을 새 제품으로 바꾸어 업데이트합니다. API 제품을 바꾸면 변경사항이 즉시 적용되고 모든 애플리케이션 등록이 자동으로 업데이트됩니다.  


---
## API 제품 바꾸기
{: #repl_api_prod}

1. {{site.data.keyword.Bluemix_short}}에 로그인: [https://console.ng.bluemix.net/login ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/login){:new_window}.

2. {{site.data.keyword.Bluemix_short}} 대시보드에서 {{site.data.keyword.apiconnect_short}} 서비스를 실행하십시오.
![](images/Bluemix.png)

3. API Manager에서 UI 탐색 분할창을 아직 고정하지 않은 경우 **이동 위치** 아이콘 ![](images/navigate-to.png)을 클릭하십시오. API Manager UI 탐색 분할창이 열립니다. UI 탐색 분할창을 고정하려면 **핀 메뉴** 아이콘 ![](images/pinned.png)을 클릭하십시오.

4. **초안** > **API**를 클릭하십시오.

5. API 패널에서 **Weather Provider API**를 클릭하여 REST 프록시 API를 여십시오.  
![](images/rep-api-list.png)

6. **버전**을 2.0.0으로 변경하십시오.  

7. 디스크 아이콘을 클릭하여 API 변경사항을 저장하십시오.  
![](images/rep-change-version.png)

8. **모든 API**를 클릭하십시오.  
![](images/rep-all-apis.png)

9. **제품**을 클릭하십시오.  
![](images/rep-api-list-2.png)

10.	**Weather Provider API 제품**을 선택하십시오.  
![](images/rep-draft-prod-list.png)

11.	**버전**을 2.0.0으로 변경하십시오. **설명** 필드에 `Updated API`를 입력하십시오. 디스크 아이콘을 클릭하여 변경사항을 저장하십시오.   
![](images/rep-update-prod.png)

12.	**스테이지** 아이콘을 클릭하여 새 버전을 업로드하십시오. 아직 선택되지 않은 경우 **샌드박스** 카탈로그를 선택하십시오.
![](images/rep-stage-prod-2.png)
    **참고**: 새 버전을 다른 카탈로그로 스테이징할 수 있으므로, 개발자 중 이 버전을 볼 수 있는 대상을 제어할 수 있습니다. 이 기능은 API 제품을 개발에서 테스트를 거쳐 프로덕션으로 이동할 때 유용하게 사용할 수 있습니다.

13.	**>>**를 클릭하여 탐색 메뉴를 열고 **대시보드**를 선택하십시오.  
![](images/rep-dashboard.png)

14.	**샌드박스**를 클릭하십시오.  

15.	**Weather Provider API 제품 2.0.0 스테이징됨** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/rep-dash-prod-list-2.png)

16.	**기존 제품 바꾸기**를 선택하십시오.  
![](images/rep-replace-prod.png)

17.	표시된 제품 목록에서 **Weather Provider API 제품 1.0.0**을 선택하십시오. **다음**을 클릭하십시오.   
![](images/rep-replace-dialog.png)

18.	**기본 플랜**을 선택하십시오. **바꾸기**를 클릭하십시오.  
![](images/rep-replace-dialog-2.png)

    이와 같이 바꾸기를 수행하면 Weather Provider API 제품 1.0.0이 폐기되고 Weather Provider API 제품 2.0.0이 공개됩니다. **참고**: 바꾸기 프로세스 중에 이 제품과 연관된 플랜을 변경할 수 있습니다. 따라서 API 제품의 플랜을 쉽게 변경할 수 있습니다.
 ![](images/rep-prod-retired.png)


## 이 튜토리얼에서 수행한 작업

이 튜토리얼에서 다음 활동을 완료했습니다.
1. API 제품 업데이트.
2. 기존 API를 업데이트된 API 제품으로 바꾸기.

---













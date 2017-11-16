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

# API 제품 아카이브 및 삭제
**기간**: 15분  
**스킬 레벨**: 초보자 

## 전제조건

1. [{{site.data.keyword.apiconnect_full}} 인스턴스를 설정하십시오](tut_prereq_set_up_apic_instance.html).

2. [API 제품 튜토리얼 대체](tut_manage_supercede.html)를 완료하십시오.

---
## 목표
이 튜토리얼에서는 API를 삭제, 아카이브 및 폐기합니다.

---
## API 제품 삭제
1. {{site.data.keyword.Bluemix_short}}에 로그인: [https://console.ng.bluemix.net/login ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/login){:new_window}.

2. {{site.data.keyword.Bluemix_short}} 대시보드에서 {{site.data.keyword.apiconnect_short}} 서비스를 실행하십시오.
![](images/Bluemix.png)

3. API Manager에서 UI 탐색 분할창을 아직 고정하지 않은 경우 **이동 위치** 아이콘 ![](images/navigate-to.png)을 클릭하십시오. API Manager UI 탐색 분할창이 열립니다. UI 탐색 분할창을 고정하려면 **핀 메뉴** 아이콘 ![](images/pinned.png)을 클릭하십시오.

4. **샌드박스**를 클릭하여 샌드박스 카탈로그를 여십시오. **참고**: 사용 가능한 카탈로그를 보려면 대시보드로 리턴해야 할 수도 있습니다. 또한 대시보드 페이지에는 목록이 아니라 타일로 카탈로그가 표시될 수 있습니다.
![](images/del-sandbox-list.png)

5. **Weather Provider API 1.0.0** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/del-prod-list1.png)

6. **카탈로그에서 삭제**를 선택하십시오.  
![](images/del-del-from-cat.png)

7. **확인**을 클릭하십시오.  
![](images/del-del-dialog.png)
    제품이 카탈로그의 제품 목록에서 사라집니다. 현재로서는 복구할 수 없습니다.


## API 제품 아카이브
1. **Weather Provider API 2.0.0** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/del-prod-list2.png)

2. **폐기**를 선택하십시오.  
![](images/del-select-retire.png)

3. **확인**을 클릭하십시오.  
![](images/del-retire-dialog.png)

4. **Weather Provider API 2.0.0** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/del-prod-list3.png)

5. **아카이브**를 선택하십시오.  
![](images/del-select-archive.png)

6. **확인**을 클릭하십시오.  
![](images/del-archive-dialog.png)
    제품이 카탈로그의 제품 목록에서 사라집니다. 이 제품은 복구할 수 있습니다.

7. 목록 보기 아이콘을 클릭하십시오.  
![](images/del-prod-list4.png)

8. **아카이브됨**을 확인하십시오.  
![](images/del-view-archived.png)

9. **Weather Provider API 2.0.0** 행에서 세로 생략 기호를 클릭하십시오.  
![](images/del-prod-list5.png)

10. **아카이브 해제**를 선택하십시오.  
![](images/del-unarchive.png)
    제품 상태가 폐기됨으로 변경됩니다.
    ![](images/del-prod-list6.png)

 
 
## 이 튜토리얼에서 수행한 작업
이 튜토리얼에서 다음 활동을 완료했습니다.

1. API 제품 삭제
2. API 제품 폐기
3. API 제품 아카이브
4. API 제품 아카이브 해제

---













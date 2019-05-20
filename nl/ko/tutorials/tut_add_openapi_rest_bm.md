---
copyright:
  years: 2019
lastupdated: "2019-3-9"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.Bluemix_notm}}를 사용하여 API 사양을 추가하고 REST 서비스 호출
{: #tut_add_openapi_rest_bm}

**소요 시간**: 15분  
**스킬 레벨**: 초보자  

## 목표
{: #object_tut_add_openapi_rest_bm}

이 튜토리얼을 사용하면 {{site.data.keyword.apiconnect_full}}를 쉽게 시작할 수 있습니다. 몇 분 만에 기존 REST 서비스의 통과(passthrough) API 프록시 역할을 하는 새 API를 빌드합니다. 빌드한 API는 보안과 모니터링을 제공합니다. 

## 전제조건
{: #prereq_tut_add_openapi_rest_bm}

시작하기 전에 [API Connect 인스턴스를 설정](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_set_up_apic_instance)해야 합니다.

---

### 샘플 앱 탐색 및 대상 엔드포인트 테스트
{: #expl_tut_add_openapi_rest_bm}

이 튜토리얼용으로 샘플 _날씨 제공업체_ 앱이 작성되었습니다.
1. 앱을 탐색하려면 [http://gettingstartedweatherapp.mybluemix.net/ ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://gettingstartedweatherapp.mybluemix.net/){: #new_window}으로 이동하십시오.  
2. 올바른 5자리 미국 우편번호를 입력하여 _**현재 날씨**_ 및 _**오늘의 예보**_를 보십시오.  
![](images/explore-weatherapp-1.png)

3. 위의 샘플 날씨 앱은 날씨 데이터를 제공하는 API를 사용하여 빌드되었습니다. **현재** 날씨 데이터를 가져오는 엔드포인트는 _**https://myweatherprovider.mybluemix.net/current?zipcode={zipcode}**_입니다. [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){: #new_window}을 방문하여 테스트하십시오.  

  ![](images/explore-weatherapp-2.png)

4. 마찬가지로 **오늘의** 예보 데이터를 가져오는 엔드포인트는 _**https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}**_입니다. [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){: #new_window}으로 이동하여 테스트하십시오.  

  ![](images/explore-weatherapp-3.png)


---

### 새 OpenAPI 스펙을 추가하여 REST API 프록시 작성  
{: #add_spec_tut_add_openapi_rest_bm}

1. {{site.data.keyword.Bluemix_short}}: https://cloud.ibm.com에 로그인하십시오.
2. {{site.data.keyword.Bluemix_notm}} **대시보드**에서 **Cloud Foundary 서비스**를 클릭하십시오.{{site.data.keyword.apiconnect_short}} 서비스를 시작하십시오. 
3. {{site.data.keyword.apiconnect_short}}에서 탐색 패널이 열려 있는지 확인하십시오. 열려 있지 않으면 **>>**를 클릭하여 여십시오.  

  ![](images/cloud-apic-dashboard.png)
4. 탐색 패널에서 **드래프트**를 선택하십시오.
5. **API** 탭에서 **추가**를 클릭하십시오. 드롭 다운 메뉴에서 **새 API**를 선택하십시오.    
  ![](images/cloud-add-api-new.png)  
6. *새 API* 창에서 제목으로 `New Weather Provider API`를 입력하십시오.
_이름과 기본 경로가 자동으로 채워집니다_.  
  ![](images/bluemix-add-new-api2.png)
7. **API 작성**을 클릭하여 마법사를 완료하십시오.  
8. API를 작성하고 나면 **디자인** 탭이 선택됩니다. 
9. **호스트** 패널로 스크롤하십시오. 필드가 자동으로 채워지지 않으면 `$(catalog.host)`를 값으로 입력하십시오.
10. **기본 경로** 패널에서 자동으로 채워진 값 `/new-weather-provider-api`를 기록하십시오. 이 값에서 API의 대상 URL이 작성됩니다.  


11. 이제 weather API를 호출할 때 리턴되는 응답 오브젝트를 정의해야 합니다. 이를 수행하려면 탐색줄에서 **정의**를 클릭하십시오.    
    a. 새 정의를 추가하십시오.  
    b. 새 정의의 이름을 _Current_로 지정하십시오.  
    c. 유형을 _object_로 설정하십시오.  
    d. **Current** 정의의 새 특성을 추가하십시오.    
       - 이름: zip         /  유형: string   
       - 이름: temperature /  유형: integer   
       - 이름: humidity    /  유형: integer   
       - 이름: city        /  유형: string   
       - 이름: state       /  유형: string   
	   
    ![](images/definition-current-1.png)   
	
    e. API를 저장하십시오.  

12. 새 정의를 작성하십시오. **Today**.

13. **Today** 정의의 새 특성을 추가하십시오.
    - 이름: zip / 유형: string
    - 이름: hi / 유형: integer
    - 이름: lo / 유형: integer
    - 이름: nightHumidity / 유형: integer
    - 이름: dayHumidity / 유형: integer
    - 이름: city / 유형: string
    - 이름: state / 유형: string

14. 정의한 데이터 형식을 사용하여 호출 경로를 작성할 수 있습니다. 탐색줄에서 **경로**를 클릭하십시오. **+**를 클릭하여 새 경로를 작성하십시오.      
    a. 새 경로의 이름을 "**/current**"로 지정하십시오.  
    b. 동일한 *경로* 패널에서 **GET /current** 섹션을 선택하십시오.    
    c. **GET /current** 섹션에서 새 **매개변수**를 추가하십시오. 샘플 앱을 탐색하는 중에 확인한 바와 같이 날씨 서비스에는 매개변수로 우편번호가 필요합니다.   
      - 이름: zipcode  
      - 위치: Query  
      - 필수: Yes  
      - 유형: string   
	  
    ![](images/path-current-1.png)   
	
    d. 아래로 스크롤하십시오.  **응답** 섹션에서 **스키마**를 _Current_로 변경하십시오.   
	
	![](images/path-current-responses.png)
	
	e. API를 저장하십시오.  

15. "**/today**"라는 다른 경로를 작성하려면 11단계에서 수행한 조치를 반복하십시오. 이 경우에서는 **응답** 스키마를 _Today_로 설정하십시오. API를 저장하십시오.

16. API를 저장하십시오.

17. **어셈블** 탭으로 전환하십시오. 지금까지 두 개의 오퍼레이션, **GET /current** 및 **GET /today**를 작성했습니다. 올바른 대상 엔드포인트가 호출되었는지 확인하려면 호출되는 오퍼레이션에서 조건부를 실행할 로직을 작성해야 합니다. **오퍼레이션 스위치** 로직 구성을 사용하여 이 작업을 수행해 보겠습니다.  **오퍼레이션 스위치**에서 의사결정 지점을 제공합니다. verb/path 쌍을 기반으로 적절한 오퍼레이션을 호출해야 합니다.

    a. 이미 _캔버스_에 추가될 수 있는 **호출** 정책을 삭제하십시오.  
    b. 팔레트에서 **오퍼레이션 스위치**를 끌어와 캔버스에 놓으십시오.  
      - **case 0**에 **get /current** 오퍼레이션을 지정합니다.
      - 새 케이스, **case 1**을 추가합니다.
      - **get /today** 오퍼레이션을 **case 1**에 지정합니다.
	  
	  
      ![](images/new-assemble-1.png)
	  
    c. 팔레트에서 **호출** 정책을 끌어와 **get /current** 아래의 처리 행에 놓으십시오. _호출 조치는 오퍼레이션에서 기존 서비스를 호출하는 데 사용합니다_.   
    d. 조치 제목을 "**invoke-current**"로 변경하십시오.   
    e. URL 필드를 `https://myweatherprovider.mybluemix.net/current?zipcode=$(request.parameters.zipcode)`로 업데이트하십시오.  
	
	![](images/new-assemble-invoke1.png)
	
	
	f. 팔레트에서 **호출** 정책을 끌어와 **get /today** 아래의 처리 행에 놓으십시오.  
    g. 조치 제목을 "**invoke-today**"로 변경하십시오.   
    h. URL 필드를 `https://myweatherprovider.mybluemix.net/today?zipcode=$(request.parameters.zipcode)`로 업데이트하십시오.  
	
       ![](images/new-assemble-invoke2.png)
	   

18. 조치 구성 패널을 닫으십시오. API를 저장하십시오.

---

### API 프록시 테스트
{: #test_proxy_tut_add_openapi_rest_bm}

1. **어셈블** 탭에서 추가 조치를 위한 아이콘을 클릭한 다음 **기본 제품 생성**을 선택하십시오.  
   ![](images/generate-default-product-small.png)

2. **새 제품** 대화 상자에서 기본 옵션을 승인하고 **제품 작성**을 클릭하십시오. Weather Provider API 제품이 작성되어 샌드박스 카탈로그에 공개됩니다. 제품 생성 성공을 나타내는 메시지가 표시됩니다.  

  ![](images/generate-default-product-new-weather.png) 

  - _{{site.data.keyword.apiconnect_short}}에서 **제품**을 사용하여 특정 용도로 사용할 API를 그룹화할 수 있습니다. 제품은 **카탈로그**에 공개됩니다. [{{site.data.keyword.apiconnect_short}} 용어집](../apic_glossary.html)_

3. 어셈블 탭에서 재생 아이콘을 클릭하여 API 프록시의 대상 호출을 테스트하십시오.

4. 테스트 패널에서 **get /current** 오퍼레이션을 선택하십시오.

	a. 우편번호는 이 오퍼레이션의 필수 매개변수이므로, 올바른 미국 우편번호(예: 10504)를 입력하십시오. 
	
	![](images/test-invoke-params.png)  
		
	b. **호출**을 클릭하십시오.   

	_CORS 오류가 발생하면 오류 메시지의 지시사항을 따르십시오. 오류의 링크를 클릭하여 브라우저에 예외를 추가하고 "호출" 단추를 다시 누르십시오._
  
    ![](images/test-invoke-new.png)  


---

### 결론
{: #conclusion_tut_add_openapi_rest_bm}

이 튜토리얼에서는 API 통과 프록시를 통해 기존 REST 서비스를 호출하는 방법을 학습했습니다. 웹 브라우저를 통해 샘플 서비스의 가용성을 확인하는 작업부터 시작했습니다. 그런 다음 {{site.data.keyword.apiconnect_short}}에서 새 OpenAPI 스펙을 작성하여 호출할 샘플 서비스에 연결했습니다. API를 제품에 패키징하고 제품을 카탈로그에 공개한 다음 프록시를 테스트했습니다.

---

## 다음 단계
{: #next_tut_add_openapi_rest_bm}

[OAuth 2.0을 사용한 보안](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_secure_oauth_2)을 통해 API를 보호하십시오.

작성 > **관리** > 보안 > 소셜화 > 분석

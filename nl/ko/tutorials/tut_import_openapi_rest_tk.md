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

# 개발자 툴킷을 사용하여 API 스펙 가져오기 및 기존 REST 서비스 프록시
소요 시간: 5분  
스킬 레벨: 초보자  


## 목표
이 튜토리얼에서는 {{site.data.keyword.apiconnect_full}}를 사용하여 기존 API를 관리 제어하는 방법을 설명합니다. 이 튜토리얼에서는 OpenAPI 스펙을 가져오고 기존 REST 서비스의 통과 API 프록시를 작성합니다.

## 전제조건
시작하기 전에 [API Connect 인스턴스를 설정](tut_prereq_set_up_apic_instance.html)하고 [API Connect 툴킷을 설치](tut_prereq_install_toolkit.html)해야 합니다.

---


## 샘플 앱 탐색 및 대상 엔드포인트 테스트

이 튜토리얼용으로 샘플 _날씨 제공업체_ 앱이 작성되었습니다. 해당 API 스펙(Swagger 2.0)은 [weather-provider-api_1.yaml ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml){:new_window} 파일에 있습니다.

1. 앱을 탐색하려면 [http://gettingstartedweatherapp.mybluemix.net/ ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](http://gettingstartedweatherapp.mybluemix.net/){:new_window}으로 이동하십시오.  
2. 올바른 5자리 미국 우편번호를 입력하여 _**현재 날씨**_ 및 _**오늘의 예보**_를 보십시오.  
![](images/explore-weatherapp-1.png)

3. 위의 샘플 날씨 앱은 날씨 데이터를 제공하는 API를 사용하여 빌드되었습니다. **현재** 날씨 데이터를 가져오는 엔드포인트는 `https:// myweatherprovider<span></span>.mybluemix.net/current?zipcode={zipcode}`입니다. [https://myweatherprovider.mybluemix.net/current?zipcode=90210 ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://myweatherprovider.mybluemix.net/current?zipcode=90210){:new_window}을 방문하여 테스트하십시오.  

  ![](images/explore-weatherapp-2.png)

4. 마찬가지로 **오늘의** 예보 데이터를 가져오는 엔드포인트는 `https:// myweatherprovider<span></span>.mybluemix.net/today?zipcode={zipcode}`입니다. [https://myweatherprovider.mybluemix.net/today?zipcode=90210 ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://myweatherprovider.mybluemix.net/today?zipcode=90210){:new_window}으로 이동하여 테스트하십시오.  

  ![](images/explore-weatherapp-3.png)



---

## 샘플 앱의 OpenAPI 스펙을 가져와 REST API 프록시 작성
1. **API Designer**를 실행하십시오. 터미널 창에서 `apic edit` 명령을 입력하십시오.
2. IBM ID를 사용하여 로그인하십시오.
    ![](images/screenshot_apic-edit_login.png)
3. **API Designer**에서 탐색 패널이 열려 있는지 확인하십시오. 열려 있지 않으면 >>를 클릭하여 여십시오.
4. 탐색 패널에서 **드래프트**를 클릭하십시오.
5. **API** 탭으로 이동하십시오.
6. API 탭에서 **추가**를 클릭하십시오.
7. 드롭다운 메뉴에서 **파일 또는 URL에서 API 가져오기**를 클릭하십시오.
   ![](images/toolkit-import-1.png)
8. 이 튜토리얼에서 사용할 날씨 API의 OpenAPI 2.0 정의가 있습니다. "OpenAPI(Swagger) 가져오기" 대화 상자에서 이 URL을 입력하십시오.
`https://raw.githubusercontent.com/IBM-Bluemix-Docs/apiconnect/master/tutorials/weather-provider-api_1.yaml`.
9. _제품 추가_ 옵션을 선택하지 않은 상태로 두고 **가져오기**를 클릭하십시오.  
    ![](images/screenshot_import-url.png)  

OpenAPI 스펙을 가져오고 나면 API의 디자인 보기로 이동합니다. 여기서 OpenAPI 정의의 다양한 섹션을 볼 수 있습니다. 스크롤하여 탐색하고 호스트 값을 기록하십시오. 소스 탭에서 OpenAPI도 볼 수 있습니다. 
_호스트 값이 _ `$(catalog.host)`로 설정됩니다_. 이 값은 API 프록시의 기본 URL입니다._
 


## API 프록시 테스트

1. **서버 시작** 아이콘을 선택하여 로컬 테스트 서버를 시작하십시오. 게이트웨이가 시작되면 상태가 자동으로 _**실행 중**_으로 업데이트됩니다.
    ![](images/screenshot_start-server-1.png)

2. **어셈블** 탭을 선택하십시오.

3. 재생 아이콘(>)을 클릭하여 API 프록시의 대상 호출을 테스트하십시오.
   _이 튜토리얼에서는 임베디드 Micro Gateway를 사용하므로 **Micro Gateway 정책**이 선택되었는지 확인하십시오.
    ![](images/screenshot_test-0.png)

4. 테스트 패널에서 다음을 수행하십시오.
  - **get /current** 오퍼레이션을 선택하십시오.  
  - 우편번호는 이 오퍼레이션의 필수 매개변수이므로, 올바른 미국 우편번호(예: 90210)를 입력하십시오.  
  - **호출**을 선택하고 응답을 확인하십시오.

    _CORS 오류가 발생하면 오류 메시지의 지시사항을 따르십시오. 오류의 링크를 클릭하여 브라우저에 예외를 추가하고 **호출**을 다시 클릭하십시오.
  
  - 예상 응답은 **200 OK** 응답과 우편번호 90210의 현재 날씨 데이터입니다.
    ![](images/screenshot_test-1.png)    


## 결론

이 튜토리얼에서는 API 통과 프록시를 통해 기존 REST 서비스를 호출하는 방법을 확인했습니다. 웹 브라우저를 통해 샘플 서비스의 가용성을 확인하는 작업부터 시작했습니다. 그런 다음 {{site.data.keyword.apiconnect_short}}에서 API 프록시를 작성하고 호출할 샘플 서비스에 프록시를 연결했습니다. 마지막으로 {{site.data.keyword.apiconnect_short}} 내부 테스트 도구를 사용하여 이 서비스를 테스트했습니다.

---

## 다음 단계

[비율 한계](tut_rate_limit.html), [클라이언트 ID 및 시크릿](tut_secure_landing.html) 또는 [OAuth 2.0를 사용하여 보호](tut_secure_oauth_2.html)를 사용하여 API를 보호합니다.

작성 > **관리** > 보안 > 소셜화 > 분석

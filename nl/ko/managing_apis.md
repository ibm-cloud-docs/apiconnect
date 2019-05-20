---

copyright:
  years: 2018
lastupdated: "2019-01-17"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 관리
{: #managing_apis}

{{site.data.keyword.Bluemix_notm}}에 있는지 아니면 {{site.data.keyword.Bluemix_notm}} 외부에서 유지보수되는지에 상관없이 API Connect를 사용하여 {{site.data.keyword.Bluemix}}에서 API를 관리할 수 있습니다. API를 관리하면 사용을 제어하고 채택을 증가시키며 통계를 추적할 수 있습니다.

고객인 경우 개발자가 API를 작성하고 {{site.data.keyword.Bluemix_notm}}에 제품을 푸시하고 나면 API Manager UI에서 API의 사용 방식을 관리할 수 있습니다. 다음 주제에서는 {{site.data.keyword.apiconnect_short}}에서 제품을 작성하고 관리하는 방법을 설명합니다.

## Secure Gateway를 통해 온프레미스 API 노출
{: #expose_apis_sec_gate_managing_apis}

온프레미스 API를 {{site.data.keyword.apiconnect_full}}에 안전하게 노출하기 위해 Secure Gateway를 작성할 수 있습니다.

Secure Gateway를 작성한 다음 해당 클라이언트 또는 Cloud에 대한 주소를 제공하십시오. `<host>:<port>`{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.SecureGateway}} 서비스의 기능을 {{site.data.keyword.apiconnect_short}}와 통합합니다. 즉, 보안 패시지를 통해 {{site.data.keyword.apiconnect_short}}에서 안전하게 온프레미스 API에 액세스할 수 있습니다. 온프레미스 데이터를 노출하지 않고 공용 환경에서
{{site.data.keyword.apiconnect_short}}에 대한 터널을 효과적으로 작성합니다. IBM Cloud에 Secure Gateway 서비스를 작성하고 구성한 다음 API에서 이에 대한 주소를 제공하기만 하면 됩니다.

{{site.data.keyword.SecureGateway}} 서비스 및 해당 서비스 설정 방법에 관한 자세한 정보는 [{{site.data.keyword.SecureGateway}} 정보![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}를 참조하십시오.

### 사용자 API로 Secure Gateway 사용
{: #using_sec_gate_apis_managing_apis notoc}

게이트웨이를 구성한 후에는 사용자 API와 함께 사용할 수 있습니다.
{:shortdesc}

Secure Gateway에서 API를 사용하려면 다음 단계를 완료하십시오.
1. 다음 단계에서 설명한 대로 API 및 제품을 작성하십시오.
  - **이동 위치** <img src="images/navigate_to_icon.png" alt="이동 위치 아이콘" /> > **드래프트** > **API** > **추가**를 클릭하십시오.
  - 작성할 API의 유형을 선택하십시오.
  - **제품 추가**를 선택하거나 클릭하십시오. **중요**: 제품을 아직 공개하지 마십시오.
  - **API 작성**을 클릭하십시오.
  API가 `디자인` 보기에 표시됩니다.
  
2. **어셈블**을 클릭하십시오.

3. **호출** 정책을 클릭하여 **호출** 팔레트를 여십시오.
**제한사항**: 논리 전환(예: `Switch`, `Operation Switch`, `If`)은
Secure Gateway를 사용하는 API와 함께 사용할 수 없습니다.

4. **Secure Gateway를 통해 URL에 액세스** 선택란을 선택하지 **마십시오**.
**중요**: 이 선택란은 프로덕션에 지원되지 않는 더 이상 사용되지 않는 기능용이므로 언제든 제거될 수 있습니다. 대신 이 선택란을 선택하지 않고 Secure Gateway URL에 대한 주소를 직접 제공하십시오. 

5. URL 필드에서 클라우드 호스트 이름 및 포트 번호로 `target-url`을 업데이트하십시오. 예를 들어 다음과 같습니다.
```
target-url: cap-sg-prd-5.securegateway.appdomain.cloud:18579
```

6. **저장** <img src="images/icon_save.png" alt="저장 아이콘" />을 클릭하십시오.

7. **모든 API** > **제품**을 클릭하고 이전에 작성한 제품을 선택하십시오.

8. 제품을 선택한 카탈로그에 스테이징하려면 **공개**를 클릭하십시오.

9. 사용할 카탈로그를 선택하십시오.

10. 스테이징된 제품을 선택하십시오.

11. **공개**를 클릭하십시오.

온프레미스 API를 {{site.data.keyword.apiconnect_short}}에 안전하게 노출했습니다. 그런 다음, {{site.data.keyword.SecureGateway}} API를 테스트하십시오.

### Secure Gateway API 테스트
{: test_sec_gate_managing_apis notoc}

API에서 {{site.data.keyword.SecureGateway}}에 대한 주소를 제공한 다음 API를 테스트하여 게이트웨이가 작동하는지, 정상적으로 응답하는지 확인할 수 있습니다.

Secure Gateway를 사용하여 API를 테스트하려면 다음 단계를 완료하십시오:

1. <img alt="이동 위치 아이콘" src="images/navigate_to_icon.png" /> > **드래프트** > **API**
**<API>** > **어셈블**을 클릭하십시오.

2. **테스트** 아이콘<img src="images/test_icon.png" alt="테스트 아이콘"/>을 클릭하십시오.

3. 제공된 목록에서 테스트할 카탈로그를 선택하십시오.

4. URL이 올바른 Secure Gateway에 대한 주소를 제공하는지 확인하십시오. `<cloud_host>:<port>` Secure Gateway 서비스 대상이 [{{site.data.keyword.SecureGateway}}![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/docs/services/SecureGateway?topic=index#getting-started-with-sg){: #new_window}문서에 설명된 대로 올바르게 구성되었는지 확인하십시오.

5. 제공된 목록에서 기존 제품을 선택한 다음 **제품
재공개**를 클릭하십시오.
   **중요** 이 제품이 이미 카탈로그에 공개된 경우,
   새 게이트웨이에 제품을 다시 공개합니다.

6. **선택사항**:
새 제품을 작성할 이름을 제공하고 **작성 및 공개**를
클릭하십시오.

7. **다음**을 클릭하십시오.

8. 제공된 목록에서 호출할 오퍼레이션을 선택하십시오.

9. **호출**을 클릭하십시오.

테스트 결과가 표시됩니다.

## LoopBack 애플리케이션 스테이징 및 공개
{: #stage_publish_lb_app_managing_apis}

1. API Designer의 탐색 분할창에서 **제품**을 클릭하십시오.
제품 탭이 열립니다.

2. 제품의 버전을 선택하고 작업할 버전을 클릭하십시오.

3. 런타임을 {{site.data.keyword.Bluemix_notm}}에 공개하려면 **공개**를 클릭하십시오.

4. **대상 추가 및 관리** > **IBM Cloud 대상 추가**를 클릭하십시오.

5. 공개할 {{site.data.keyword.Bluemix_notm}} **지역**을 선택하고 로그인하십시오.

6. 공개할 {{site.data.keyword.Bluemix_notm}} **조직**을 선택하십시오.

7.  카탈로그의 목록이 표시됩니다. 공개할 카탈로그를 선택하십시오.

8.  **다음**을 클릭하십시오.

9. 공개할 LoopBack 애플리케이션을 선택하십시오.
{{site.data.keyword.Bluemix_notm}}에 런타임을
처음 배치하는 경우에는 이름을 추가하고 **추가** 아이콘을 클릭하십시오.

10.  **저장**을 클릭하십시오.

11.  **공개**를 다시 클릭하고 **애플리케이션 공개**를 선택하십시오.

12.  **공개**를 클릭하십시오.

13. 명령행에서 API 대상 URL 및 API 호출 tls-profile이 API에 대해 지정됩니다.
이 정보를 기록하십시오. API 호출 tls-profile은 항상
`client:Loopback-client`이지만, 다음 단계에서 설명하는 대로 API 대상 URL을
검색할 수 있습니다.
    ```
    Deploying to Bluemix
    ...preparing project
    ...building package for deploy
    ...uploading package
    Runtime published successfully.
    Management URL: https://<domain name>/apps/33e7b062-092b-4227-af97-047499dab2e7
    API target urls: apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>
    API invoke tls-profile: client:Loopback-client
    Updated newapi_1.0.0.yaml with tls-profile and target-url.
    Updated notes.yaml with tls-profile and target-url.
    ```

14. API Designer UI에서 다음 단계를 완료하십시오.
    1. **API**를 클릭하십시오.
    2. API를 선택하십시오.
    3. **어셈블**을 클릭하십시오.
    4. 어셈블리 편집기에서 **필터 정책** 아이콘을 클릭하십시오.
    5. **DataPower Gateway 정책**을 선택하십시오.
    6. **저장**을 클릭하여 API를 저장하십시오.

15.  다음으로 API Manager에 공개해야 합니다. **공개**를 클릭하십시오.
    1. **애플리케이션 공개**를 선택한 후 다음 옵션 중 하나를 선택하십시오.
	    - **기존 앱 바꾸기**: 공개된 애플리케이션이 있으면 이 옵션을 선택하여 기존 앱을 겹쳐쓰십시오.
        - **완전히 새로운 앱으로 공개(기존 라우트 사용)**: 이 옵션을 선택하여 새 앱을 작성하고 **새 앱** 필드에서 해당 이름을 제공하십시오. 서비스가 인터럽트되지 않습니다.

    2. 다음 옵션을 선택하십시오.
	    - 제품 스테이징 또는 공개
        - 특정 제품 선택
        - _your product_
 
    3. **공개**를 클릭하십시오.

공개가 작동하는지 테스트하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.Bluemix_notm}} 앱이 실행 중인지
확인하십시오.

2. 브라우저 창을 열고 API URL로 이동하십시오.
애플리케이션은 클라이언트 유효성 검증으로 보호됩니다. 올바른 클라이언트 인증서를 제공하지 않으면
오류가 발생합니다(이는 예상된 결과임).

3. 노출된 {{site.data.keyword.apiconnect_short}} URL로
이동하십시오.
예:
```
https://<domain>/<Bluemix org>-<Bluemix space>/<Catalog identifier>/api/notes
```
200 응답이 표시됩니다.

## 카탈로그 구성
{: #config_cat_managing_apis}

API Manager 카탈로그를 작성하고 구성할 수 있습니다. 카탈로그는
개발자 조직에 사용 가능하도록 하기 전에 테스트할 제품 및 API를 분리하는 데 유용합니다.
또한 카탈로그를 구성할 때 API Manager에서 제공하는 기본 API URL을 사용할 필요가 없도록
사용자 정의 브랜딩을 구성할 수도 있습니다.

다음 단계를 완료하여 카탈로그를 작성하십시오.

1. **이동 위치** <img alt="이동 위치 아이콘" src="images/navigate_to_icon.png"> > **대시보드**를 클릭하십시오.

2. **+ 추가** > **카탈로그**를 클릭하십시오.
**카탈로그 추가** 창이 표시됩니다.

3.  **표시 이름** 필드에서 새 카탈로그의 이름을 입력하십시오.

4. **이름** 필드에서
URL의 카탈로그 세그먼트를 구성하는 텍스트를 입력하십시오.
**참고:** **이름** 필드에는 소문자 영숫자 문자(a-z
및 0-9) 또는 하이픈 문자(-)만 사용할 수 있습니다. 하이픈은 이름에서 첫 번째 또는 마지막 문자로
사용할 수 없습니다.

5. **추가**를 클릭하십시오. 카탈로그가 작성되고 대시보드에 표시됩니다.

6. 카탈로그를 구성하려면 카탈로그의 이름을 클릭한 후 **설정** > **정보**를 클릭하고 다음 단계를 진행하십시오.
  1. 새 카탈로그가 개발 카탈로그인 경우 **개발 모드**를 선택하십시오.
개발 모드를 선택하는 경우 스테이징 및 공개 조치가 강제 실행되어
이전에 공개된 제품을 다시 공개하는 경우 경고 없이 겹쳐쓰는 것을 의미합니다. 충돌이
발견되는 경우 시스템이 자동으로 충돌을 해결합니다. 공개 취소 조치가 자동으로 발생합니다.
**참고:** 승인 상자는 개발 카탈로그에 표시되지 않습니다. 라이프사이클에 대한 승인 프로세스를
사용으로 설정할 수 없습니다.
  2. 카탈로그에 대해 자동 등록을 사용하려면 **자동
등록**을 선택하십시오.
자동 등록을 사용하면 사전 제공된 클라이언트 ID 및 클라이언트 시크릿과 함께
테스트 애플리케이션이 사용되므로 API를 더 쉽게 테스트할 수 있으며, 이는 카탈로그에서 모든 플랜에
자동으로 등록되어 사용자가 테스트 시 플랜 또는 애플리케이션을 지정할 필요가 없습니다.
**참고:** 자동 등록은 개발 카탈로그에만 사용할 수 있습니다.
  3. 카탈로그가 기본 스테이징 카탈로그인 경우 **기본값**을 선택하십시오. 그런 다음
카탈로그에 공개된 API에 대한 호출에서는 카탈로그 이름을 포함하지 않는
단축형 URL을 사용할 수 있습니다.
     **참고:** 한 카탈로그에만 **기본값**을 선택할 수 있습니다.
  4. **선택사항**: **엔드포인트**를 클릭하고 다음 필드를 채우십시오.
        - **사용자 정의 게이트웨이 URL**: 사용자 정의 게이트웨이 URL 텍스트 필드에 URL을 입력하십시오. API Manager가 생성하는 기본 URL을 사용하지 않고
        {{site.data.keyword.apiconnect_short}}에 배치되는 API에 대해 URL의 사용자 정의 브랜딩을 완료하려는 경우
        사용자 정의 게이트웨이 URL을 사용합니다.
        기본적으로 {{site.data.keyword.apiconnect_short}} 게이트웨이
        URL의 형식은 다음과 같습니다.
        ```
        https://gateway_cluster_hostname/organization_name/Catalog_name
        ```
        그러나 엔터프라이즈에 더 적합한 URL을 지정하여 기본값을 대체할 수
        있습니다(예: `https://api.mycompany.com`). 그런 다음 개발자 포털에 표시되는 API 엔드포인트가
        지정된 URL을 반영합니다.
        **참고:**
		    - 기본 게이트웨이 URL에 사용자 정의 호스트 이름 및 도메인을 맵핑하는 DNS 항목을 구성해야
		    합니다.
		    - API의 엔드포인트가 사용자 정의 게이트웨이 URL을 반영하려면 API Connect 게이트웨이에서
		    강제 실행되도록 API를 구성해야 합니다. 자세한 정보는 [API의 대체 호스트 지정 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}을 참조하십시오.
		    - 동일한 사용자 정의 게이트웨이 URL이 여러 카탈로그에 적용되지 않도록 하십시오. 해당 시나리오의
		    동작이 정의되지 않습니다.
	        **팁**: 또한, API를 호출할 때 API 요청에서 HTTP 호스트 헤더를
		    사용자 정의 게이트웨이 URL 필드에 지정한 값으로 설정할 수 있습니다.

	    - **사용자 정의 API URL**
	    사용자 정의 API URL 텍스트 필드에 URL을 입력하십시오. 사용자 정의 API URL을 사용하여
	    서드파티 게이트웨이에 배치되는 API에 대해 URL을 지정합니다.

	    사용자 정의 API URL은 외부적으로 API가 알려져 있는 엔드포인트를 나타냅니다. 즉,
	    개발자 포털에 공개되고 애플리케이션 개발자가 API를 호출하거나 알리기 위해 사용하는
	    엔드포인트입니다.

	    이 카탈로그에서 서드파티 게이트웨이 또는 외부 로드 밸런서를 사용 중인 경우 이 필드에 URL을
	    제공하십시오. 그런 다음 개발자 포털에 표시되는 API 엔드포인트가 지정된 URL을
	    반영합니다. 이러한 엔드포인트는 서드파티 게이트웨이 또는 로드 밸런서에 존재하고
	    게이트웨이의 API 프록시 또는 API 어셈블리 엔드포인트에 맵핑되며 API 이용자에게 노출되는 가상 주소를
	    예상합니다. 사용자 정의 API URL에서 파생된 엔드포인트는 일반적으로
	    API의 주소를 알리기 위해 프로덕션 개발자 포털에 공개됩니다.

	    **참고:** 카탈로그에 대해 사용자 정의 API URL을 지정하는 경우,
	    이는 API 구성 시 지정하는 호스트 이름보다 우선합니다. 자세한 정보는 [API의 대체 호스트 지정 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html#task_tq2_11r_xt__enforce_step){: #new_window}을 참조하십시오.

	    - **개발자 포털 API 호출의 호스트 이름**:
	    포트 API 엔드포인트 창 영역에서 개발자 포털 API 호출의 호스트 이름을 입력하십시오. 입력하는 호스트 이름은
	    관리 서비스의 호스트 이름일 수 있습니다. 개발자 포털의 컨텍스트 내에서 개발자 포털 API에
	    액세스하려면 개발자 포털 API 호출에 대해 기본 호스트 이름을
	    구성해야 합니다. 이 조치를 통해 API Manager는
	    검색하거나 호출에 포함할 필요 없이 개발자 포털 API 호출의 제공자 조직 및 카탈로그에 호스트 이름을
	    맵핑할 수 있습니다.

7. **저장** 아이콘을 클릭하십시오.

## 카탈로그 파티셔닝
{: #part_cat_managing_apis}

{{site.data.keyword.apiconnect_short}}의 신디케이션 기능을 사용하려면
신디케이션 기능이 필요한 모든 카탈로그에서 영역을 설정해야 합니다.

카탈로그에서 영역을 사용하려면 다음 단계를 완료하십시오.
1. API Manager UI의 대시보드에서 작업할 카탈로그를 선택하십시오.

2. **설정** > **개요**를 클릭하고 **영역** 슬라이더 제어를 클릭하십시오.

3. **영역 사용** 창에서 **사용**을 클릭하고 **저장** 아이콘 <img src="images/icon_save.png" alt="저장 아이콘"/>을 클릭하십시오.
**영역 관리** 링크가
**영역** 슬라이더 제어 아래에 표시되며 **영역** 링크가 탐색 분할창에
추가됩니다. 이러한 링크 중 하나를 클릭하여 영역을 관리할 수 있습니다.

카탈로그의 영역이 설정되며 '새 영역'이라는 기본 영역이
작성됩니다.

신디케이션에 대한 자세한 정보는 Knowledge Center 주제, [IBM API Connect에서 신디케이션 사용 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.apionprem.doc/capic_syndication_using.html){: #new_window}을 참조하십시오.

## 개발자 포털 구성
{: #config_dev_portal_managing_apis}

개발자 포털은 애플리케이션 개발자가 액세스하고 사용할 수 있도록 플랜이
공개되는 위치입니다.

애플리케이션 개발자가 사용할 수 있도록 사용자 정의된 개발자 포털을 빌드할 수 있습니다. 
사용자에게는 모양, 컨텐츠, 사용자 설정 및 구성 설정을 전체적으로 관리할 수 있는 제어 권한이 있습니다.

애플리케이션 개발자가 API를 찾아서 사용할 수 있도록 허용함은 물론, 개발자 포털은
API의 Swagger UI 및 포럼, 블로그, 주석, 등급과 같은 추가 기능을 제공합니다.

1. API Manager UI에서 작업할 카탈로그를 선택하십시오.

2. **설정** 탭을 선택하십시오.

3. **포털**을 클릭하십시오.

4. **포털 구성** 섹션에서 **IBM 개발자 포털**을
선택하십시오. 포털 URL이 표시됩니다.

5. **저장**을 클릭하십시오. 개발자 포털 웹 관리자에 대한 일회성 로그인 링크가 포함된 이메일이
사용자에게 발송됩니다.

6. 이메일로 발송된 링크를 클릭하고 지시사항에 따라 비밀번호를
재설정하십시오.

개발자 포털이 구성되었습니다. 수신한 이메일의 제목 행에서 개발자 포털의 URL을 찾을 수
있습니다. 또한 **포털** > **설정**을 사용하여
API Manager UI에서 URL을 찾을 수 있습니다.

개발자 포털에서 완료할 수 있는 태스크에 대한 자세한 정보는 [개발자 포털
![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/support/knowledgecenter/SSFS6T/com.ibm.apic.devportal.doc/capim_devportal_overview.html){: #new_window}에 대한 IBM Knowledge Center 주제를 참조하십시오.

## 역할의 권한 구성
{: #config_permissions_roles_managing_apis}

API Manager에서 역할의 권한을 구성하려면 다음 단계를
완료하십시오.

1. API Manager **대시보드**에서 작업할 카탈로그를
클릭하십시오.

2. **설정** > **권한**을 클릭하십시오.
역할을 지정할 수 있는 제품 관리 권한이 표시됩니다.
  - **단계**: 제품을 카탈로그로 스테이징할 수 있습니다.
  - **보기**: 카탈로그에서 제품의 보기 및 나열을 허용합니다.
  - **관리**: 제품 라이프사이클(공개, 사용하지 않음, 폐기 및 아카이빙)의 관리를 허용합니다.
  - **승인**: 제품 라이프사이클 상태 변경에 대한 승인을 사용합니다.
**참고:** 제품 라이프사이클 상태 변경에 대한 승인은 모든 개발 카탈로그에 대해 사용 안함으로 설정됩니다.

3. **스테이지**, **보기** 또는 **관리** 권한에 역할을 추가하려면 해당하는 **+** 아이콘을 클릭하십시오.
다음 목록에는 사용 가능한 기본 역할이 표시됩니다.
  - 관리자
  - 제품 관리자
  - API 개발자
  - 공개자
소유자 역할에는 모든 권한이 있습니다.

4. 라이프사이클 상태 변경을 승인할 권한이 있는 역할을 지정하기 위해 필수 선택란을 선택한 후
해당하는 **+** 아이콘을 클릭하여 제품 라이프사이클 상태 변경에 대한 승인을
사용으로 설정하십시오.
선택하는 라이프사이클 상태 변경은 승인을 강제하려는 항목입니다.
예를 들어, 공개를 선택하지만 다른 항목은 해제된 상태로 두는 경우
누군가 제품 공개를 시도할 때 승인이 필요합니다. 그러나 다른 라이프사이클 상태 변경에는
승인이 필요하지 않습니다.
5. 사용자 정의된 정책을 관리할 권한이 있는 역할을 지정하려면
**정책 관리** 섹션에서 **+** 아이콘을 클릭하십시오.
정책 관리 권한이 표시되어 사용자가 필요한 대로 역할을
지정할 수 있습니다.
6. **저장** 아이콘을 클릭하십시오.

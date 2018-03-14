---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 가져오기

Swagger 정의 파일을 사용하여 REST API를 추가할 수 있습니다.
{:shortdesc}

## 전제조건
{: #prereq_import_swagger}

시작하기 전에, 파일이 버전 2.0의 Swagger 스펙을 준수하는지
확인하십시오. 파일 형식은 JSON 또는 YAML일 수 있습니다.

Swagger 파일을 로드하여 REST API를 추가하려면 다음 단계를
완료하십시오.

1. API Manager UI 탐색 분할창에서 **드래프트**를 클릭한 후에 **API**를
클릭하십시오.
API 탭이 열립니다.

2. **+ 추가**를 클릭한 후에 **가져오기** 섹션에서
**Swagger 2.0**을 선택하십시오.
**Swagger API 가져오기** 창이 열립니다.

3. **선택사항**:
로컬 파일 시스템에서 파일을 업로드하려면 **파일 선택**을 클릭하고
파일 시스템에서 사용하고자 하는 파일을 선택하십시오. 유효한
Swagger 정의가 포함되어 있는 `.json`, `.yml` 및 `.yaml`
파일이 지원됩니다.

4. **선택사항**:
URL에서 파일을 업로드하려면 **또는 URL에서 가져오기**를
클릭한 후에 제시되는 **URL** 필드에서 올바른 URL을 입력하십시오. 
URL에 액세스하는 데 인증이 필요하면 사용자 이름 및 비밀번호를 입력하십시오. 유효한
Swagger 정의가 포함되어 있는 `.json`, `.yml` 및 `.yaml`
파일이 지원됩니다.

5. **가져오기**를 클릭하십시오.
경로 및 HTTP 오퍼레이션을 포함하여 새 REST API 정의가 작성됩니다.

API 정의를 가져온 경우, 이는 **드래프트** 페이지의
**API** 탭에서 API 정의의 목록에 표시됩니다.
그다음, 기타 REST API 정의에서와 같이 API 정의를 편집할 수 있습니다.

## IBM Integration Bus에서 API 가져오기
{: #tut_import_iib_apic}

이 튜토리얼에서 사용자는 관리와 공개가 보다 용이할 수 있도록 IBM Integration Bus에서 작성한 REST API를 {{site.data.keyword.apiconnect_full}}에 가져올 수 있습니다. 
{: shortdesc}

시작하기 전에, REST API 파일이 버전 2.0의 Swagger 스펙을 준수하는지 확인하십시오. 파일 형식은 JSON 또는 YAML일 수 있습니다.

IBM Integration Bus를 사용하면 RESTful 웹 서비스로서 통합을
노출하는 데 사용될 수 있으며 HTTP 클라이언트에 의해 호출될 수 있는
특수 애플리케이션인 REST API를 작성할 수 있습니다. 일단 API가 작성되면 {{site.data.keyword.apiconnect_short}}에 가져와서 이를 관리하고 공개할 수 있습니다.

다음 목록에는 {{site.data.keyword.apiconnect_short}}에서 API를 관리하는 경우의 일부 장점이 포함되어 있습니다.
* API에 대한 호출의 수를 모니터할 수 있습니다.
* API에 대한 호출의 수를 제어할 수 있습니다.
* 다중 버전의 API를 유지보수할 수 있습니다.

자세한 이점은 [API 관리](managing_apis.html)를 참조하십시오.

IBM Integration Bus에서 REST API를 작성하여
{{site.data.keyword.apiconnect_short}}에 가져오려면
다음 단계를 완료하십시오.
1. IBM Integration Bus를 사용하여 REST API를 작성하십시오. 제한사항: IBM Integration Bus의 설치된 버전에서 제공되는 IBM Integration Toolkit에서만 REST API를 작성할 수 있습니다.
	1. IBM Integration Toolkit을 사용하여 REST API를
    작성하십시오. IBM Integration Bus에서 REST API 작성 태스크를 완료하는 방법에 대한 자세한 정보는 IBM Knowledge Center에서 [REST API를 사용하여 통합 솔루션 개발 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSMKHH_10.0.0/com.ibm.etools.mft.doc/bi12016_.htm){: new_window}을 참조하십시오.
		
	2. **파일** > **새로 작성** > **REST API**를 선택하여 REST API 마법사 작성을 여십시오.
		
	3. REST API의 이름을 입력하십시오. 지정하는 이름은 IBM Integration Toolkit에서
    프로젝트의 이름으로 사용됩니다.
		
	4. 다음의 REST API 작성 방법 중 하나를 선택하고 해당 프로시저를 완료하십시오.
		
	**IBM Integration Toolkit에서 제공하는 REST API 편집기를 사용하여 처음부터 새로 작성**:
		1. **REST API를 작성하고 리소스 및 오퍼레이션을 직접 정의**를 선택하십시오.
		2. **완료**를 클릭하십시오. 새 REST API에 대한 REST API 편집기가 자동으로 열리며, 사용자는 이를 사용하여 리소스, 모델 및 오퍼레이션을 정의해야 합니다.
		
	**기존 Swagger 2.0 문서에서 작성**:
		1. **Swagger 문서에 정의된 리소스 및 오퍼레이션 가져오기**를 선택하고 **다음**을 클릭하십시오.
		2. REST API에서 원하는 리소스 및 오퍼레이션을 기술하는 Swagger 문서의 경로를 선택하십시오. 파일 시스템에서 또는 작업공간의 기존 프로젝트에서 Swagger 문서를 가져올 수 있습니다. 파일은 REST API에서 사용할 수 있도록 유효성 검증됩니다. 선택된 Swagger 문서의 유효성을 검증하는 동안 오류가 발생하면 마법사를 시작할 때 해당 유효성 검증 오류가 표시됩니다. 선택된 Swagger 문서에서 유효성 검증 오류가 발생하면 계속 진행할 수 없습니다.
		3. **완료**를 클릭하여 API를 작성하십시오.
	5. 포함하고자 하는 REST 오퍼레이션인 REST API의 서브플로우를 구현하십시오.
2. IBM Integration Bus의 신규 또는 기존 브로커 아카이브(BAR) 파일에 REST API 프로젝트를 추가하십시오.
3. IBM Integration Bus on Cloud에 BAR 파일을 배치하십시오.
	1. 아직 로그인하지 않았으면 IBM ID를 사용하여 IBM Integration Bus on Cloud에 로그인하십시오. 아직 계정이 없으면 계정을 등록하십시오.
	2. **통합 추가** > **BAR 파일 업로드**를 클릭하십시오.
	3. REST API 프로젝트에 대해 작성한 BAR 파일을 선택하십시오. 팁: IBM Integration Toolkit에서 BAR 파일에 마우스 오른쪽 단추를 클릭하고 해당 특성을 보면 이 파일의 위치를 찾을 수 있습니다.
	4. **저장**을 선택하십시오.
	5. **목록 새로 고치기**를 선택하여 화면을 업데이트하십시오.
	6. IBM Integration Bus on Cloud의 *통합* 창에서 API에 대한 API 통합 플로우를 보고 BAR 파일이 정상적으로 업로드되었는지 확인하십시오.
4. 시작 아이콘 ![시작 아이콘을 표시하는 화면 캡처.](images/a_play_button.jpg " ")을 선택하여 통합 플로우를 시작하십시오. API가 시작되며 `Running` 상태를 표시합니다.
5. 통합의 목록에서 통합을 선택하여 이에 대한 정보를 보십시오. 컨텐츠 메뉴의 트리에서 REST API 및 이와 연관된 서브플로우를 표시합니다. 기타 섹션에서 정보를 볼 수도 있습니다. 공용 엔드포인트 섹션에서
IBM Integration Bus on Cloud가 통합 플로우에 지정한
공용 URL을 볼 수 있습니다. **전체 URL 표시**를 선택하여 해당 오퍼레이션의 전체 URL을 보십시오.
6. 오퍼레이션의 전체 URL을 클립보드에 복사하십시오. 이는 {{site.data.keyword.apiconnect_short}}에서 작업할 API를 구성할 때 필요합니다. 기본 인증을 사용한 경우에는 지정된 사용자 이름과 비밀번호도 기록하십시오.

### IBM Integration Bus를 API Connect와 통합하십시오.
{: #integrateiibapic}

1. IBM Integration Toolkit의 REST API 프로젝트와 연관된 Swagger 파일을 {{site.data.keyword.apiconnect_short}} 서비스로 가져오십시오. 
	1. {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 서비스에 로그인하십시오.
	2. API Manager UI 탐색 분할창에서 **드래프트** > **API**를 선택하십시오. API 탭이 열립니다.
	3. **+ 추가** > **파일 또는 URL에서 API 가져오기**를 선택하십시오. *OpenAPI(Swagger) 가져오기* 창이 열립니다.
	4. 로컬 파일 시스템에서 작성한 파일을 업로드하려면 **파일 선택**을 선택하고 IBM Integration Bus에서 작성된 파일을 선택하십시오. 올바른 Swagger 정의가 포함되어 있으면 `.json`, `.yml` 및 `.yaml` 확장자가 있는 파일이 지원됩니다. **제품 추가**에 대한 옵션이 선택되었는지 확인하십시오. **카탈로그에 이 제품 공개**를 선택하여 제품을 선택적으로 공개할 수 있습니다.
	5. **가져오기**를 클릭하십시오. 경로 및 HTTP 오퍼레이션을 포함하여 새 REST API 정의가 작성됩니다. 팁: 가져오는 데 1분이 초과되면, 가져오기를 취소하고 브라우저를 새로 고친 후에 가져오기를 다시 시도하십시오. 세션이 만료될 수 있습니다.
2. {{site.data.keyword.apiconnect_short}}의 가져온 API를 IBM Integration Bus on Cloud의 API와 연관시키십시오.
	1. {{site.data.keyword.apiconnect_short}}의 대시보드로 이동하십시오.
	2. **드래프트** > **API**를 선택하십시오.
	3. 가져온 REST API를 클릭하십시오.
	4. 어셈블 탭을 선택하고 **어셈블리 작성**을 선택하여 프록시 정책을 추가하십시오.
	5. **프록시** 정책을 비어있는 새 정책으로 끌어와서 이를 사용할 수 있도록 하십시오.
	6. IBM Integration Bus on Cloud의 공용 엔드포인트 섹션에서 복사한 API에 대한 URL을 붙여넣으십시오.
	7. REST API에 대해 기본 인증을 사용한 경우에는 IBM Integration Bus on Cloud에서 생성된 사용자 이름과 비밀번호를 입력하십시오.
	8. API 설정을 저장하십시오.
3. API를 테스트하십시오.
	1. API의 어셈블 탭에서 테스트 단추 ![테스트 단추](images/a_play_button.jpg "테스트 단추를 표시하는 화면 캡처 아이콘.")를 선택하십시오.
	2. **제품 재공개**를 선택하십시오.
	3. 오퍼레이션을 선택하십시오.
	4. 필수 매개변수를 입력하십시오.
	5. **호출**을 선택하십시오.
	6. API에서 예상 응답을 수신하는지 확인하십시오. 
	
API 정의를 가져오고 통합하는 경우, 사용자는 기타 REST API 정의에서와 같이 API를 관리하고 규정할 수 있습니다. API에 대한 자세한 정보는 [API 관리](managing_apis.html)를 참조하십시오.

## IBM API Connect에서 IBM App Connect Professional로 작성된 API 공개

이 튜토리얼에서는 IBM App Connect Professional 및 {{site.data.keyword.apiconnect_full}}를 사용하여 작성한 REST API를 공개하고 관리할 수 있습니다.

### 전제조건
{: #prereq_pub_api_appconn}

이 튜토리얼을 완료하려면 IBM App Connect
Professional on Cloud와 {{site.data.keyword.apiconnect_short}}의 올바른 계정이 있어야 합니다. REST
API 파일이 Swagger 버전 2.0 스펙을 준수하는지 확인하십시오. 파일 형식은 JSON 또는 YAML일 수
있습니다.

IBM App Connect Professional을
사용하면 RESTful 웹 서비스로서 통합을 노출하는 데 사용될 수 있으며 HTTP 클라이언트에 의해
호출될 수 있는 특수 애플리케이션인 REST API를 작성할 수 있습니다. API를 작성한 후
{{site.data.keyword.apiconnect_short}}를 사용하여 API를 공개하고 관리할 수 있습니다.
다음 목록에는 {{site.data.keyword.apiconnect_short}}에서 API를 관리하는 경우의 일부 장점이 포함되어 있습니다.

- API에 대한 호출의 수를 모니터할 수 있습니다.
- API에 대한 호출의 수를 제어할 수 있습니다.
- 다중 버전의 API를 유지보수할 수 있습니다.

자세한 이점은 [API 관리](managing_apis.html)를 참조하십시오.
IBM App Connect Professional에서 REST API를 작성하고
{{site.data.keyword.apiconnect_short}}에 공개하려면
다음 단계를 완료하십시오.

1. IBM App Connect Professional을
사용하여 REST API를 작성하십시오.
  - IBM ID를 사용하여 [App Connect Professional Web Management Console ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://appconnect.ibmcloud.com/professional/){:new_window}에 로그인하십시오. IBM App Connect Professional Web Management Console에서 REST API를 작성하는 태스크를 완료하는 방법에 대한 자세한 정보는 IBM Knowledge Center의 [관리 콘솔 설정 정보 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS3LC4_7.5.2.0/com.ibm.wci.appliance.doc/About_the_WMC/consoleSettings.html){:new_window}를 참조하십시오.
  - 아직 선택되지 않은 경우 프로덕션 탭을 선택하십시오.
  - 탐색 패널에서 **저장소** > **구성**을 선택하십시오.
  - 프로젝트 구성 화면에서 {{site.data.keyword.apiconnect_short}}에 공개할 프로젝트를 선택하십시오.  공개할 프로젝트의 구성 세부사항이 표시됩니다.
  - **API 관리에 푸시**를 선택하십시오. 
      **팁**: 가져올 프로젝트의 상태가 실행 중이거나 배치됨인 경우에만 **API 관리에 푸시** 단추가 활성입니다. 링크가 표시되지 않으면 재생 단추를 선택하여 프로젝트를 시작하십시오.
  - API 관리에 푸시 화면에서 다음 정보를 입력하여 API 관리 시스템에 대한 연결을 작성하십시오.

  <table><caption>표 1. {{site.data.keyword.apiconnect_short}}에 API 공개를 위한 연결 정보</caption>
  <thead>
  <tr>
  <th>필드 이름</th>
  <th>설명</th>
  </tr>
  </thead>
  <tbody>
  <tr><td>호스트</td>
  <td>관리 클러스터, 서버 또는 클라우드 주소의 호스트 이름을 지정합니다. {{site.data.keyword.Bluemix_notm}}의 경우 이 항목은 us.apiconnect.ibmcloud.com일 가능성이 큽니다.</td>
  </tr>
  <tr>
  <td>포트</td>
  <td>관리 클러스터, 서버 또는 클라우드 주소에 연결해야 하는 포트 번호를 지정합니다.</td>
  </tr>
  <tr><td>사용자 ID</td>
  <td>관리 클러스터, 서버 또는 클라우드 주소에 액세스하는 데 사용한 인증 사용자 이름을 지정합니다. {{site.data.keyword.Bluemix_notm}}에 로그인하는 데 사용하는 IBM ID일 가능성이 큽니다.</td>
  </tr>
  <tr><td>비밀번호</td>
  <td>관리 클러스터, 서버 또는 클라우드 주소에 액세스하는 데 사용한 인증 비밀번호를
  지정합니다. {{site.data.keyword.Bluemix_notm}}에 로그인하는 데
  사용하는 IBM ID 비밀번호일 가능성이 큽니다.</td>
  </tr>
  </tbody>
  </table>

2. ID 및 비밀번호와 연결된 조직 목록을 채우려면 **조직 로드**를
선택하십시오.

3. 사용 가능한 조직 중 하나에 프로젝트를 연결하려면 **조직**을
선택하십시오.

4. **APIM에 푸시**를 선택한 다음 **확인**을 선택하십시오.

5. **닫기**를 선택하여 창을 닫으십시오.
기본 브라우저에 새 브라우저 탭이 열리고 API를 표시합니다.

IBM App Connect API를 {{site.data.keyword.apiconnect_short}}와 연관시키십시오.

#### Swagger API 정의 가져오기

IBM App Connect의 REST API 프로젝트와 연관된 Swagger 파일을 {{site.data.keyword.apiconnect_short}} 서비스에 가져오려면 다음 단계를 따르십시오.

1. {{site.data.keyword.apiconnect_short}} {{site.data.keyword.Bluemix_notm}} 서비스에 로그인하십시오.

1.  API Manager UI 제목 표시줄에서 **이동 위치** > **드래프트**를 선택하십시오.

2. 메뉴 표시줄에서 **API**를 선택하십시오.
API 탭이 열립니다.

3. 가져온 API를 선택하여 API Designer를 여십시오.

4. 탐색 창에서 **어셈블**을 선택하십시오.
정책 목록이 탐색 창에 표시됩니다.

5. 필요한 경우 **어셈블리 작성**을 선택하십시오.

6. 기본 창의 어셈블리에 끌어와 **호출** 정책을
추가하십시오.

7. 기본 창에서 **호출** 정책을 선택하여 해당 구성 설정을
수정하십시오.

8. 다음 정보로 URL 필드의 host/basePath를 구성하십시오.

- **hostname**: 클라우드 인스턴스에 따라 다른 설정입니다. 이 설정에 대한 자세한 정보는
[IBM App Connect Professional ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://provide.castiron.ibmcloud.com){:new_window}을 참조하십시오.

- **basepath**: App Connect Professional 오케스트레이션의 httpReceive Request 참고에 지정하는 경로입니다.

9. App Connect Professional에 사용하는 Http Basic 인증 세부사항에 IBM ID 사용자 이름과
비밀번호를 추가하고 저장하십시오.

#### API 테스트

API를 테스트하려면 다음 단계를 수행하십시오.

1. API의 어셈블 탭에서 테스트 단추 <img alt="테스트 단추를 표시하는 화면 캡처 아이콘" src="images/a_play_button.jpg" />를 선택하십시오.
2. **제품 재공개**를 선택하십시오.
3. 오퍼레이션을 선택하십시오.
4.  필수 매개변수를 입력하십시오.
5. **호출**을 선택하십시오.
6. API에서 예상 응답을 수신하는지 확인하십시오.

API 정의를 가져오고 통합하는 경우, 사용자는 기타 REST API 정의에서와 같이 API를
관리하고 규정할 수 있습니다. API에 대한 자세한 정보는 [API 관리](managing_apis.html)를 참조하십시오.



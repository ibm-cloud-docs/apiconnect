---

copyright:
  years: 2018
lastupdated: "2018-02-22"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Node.js에 API 작성
{: #tut_create_api_node}

**소요 시간**: 20분  
**스킬 레벨**: 초보자  

---
## 목표
{: #object_tut_create_api_node}

이 튜토리얼에서는 LoopBack 프레임워크를 사용하여 Node.js에서 API를 작성하는 단계를 안내합니다. 이 튜토리얼에서는 다음을 수행하는 방법을 설명합니다.
1. 새 LoopBack 프로젝트를 작성합니다.
2. {{site.data.keyword.apiconnect_full}} 툴킷의 API Designer를 사용하여 LoopBack 프로젝트에 새 데이터 소스와 모델을 추가합니다.
3. API Designer Explore 도구를 사용하여 API 엔드포인트를 테스트합니다.

---
## 전제조건
{: #prereq_tut_create_api_node}

시작하기 전에 [{{site.data.keyword.apiconnect_short}} 툴킷을 설치](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_prereq_install_toolkit)하십시오. 툴킷이 이미 설치된 경우, 버전 5.0.8.1 이상을 실행 중인지 확인하십시오. 명령행에 다음 명령을 입력하여 이를 확인할 수 있습니다.
	```
	apic -v
	```

---
## Loopback 프로젝트 작성
{: #create_tut_create_api_node}

{{site.data.keyword.apiconnect_short}} 개발자 툴킷 명령행 인터페이스 또는 API Designer 인터페이스를 사용하여 Loopback 프로젝트를 작성할 수 있습니다. 
 
### 툴킷 명령행을 사용하여 LoopBack 프로젝트 작성
{: #create_cli_tut_create_api_node}

{{site.data.keyword.apiconnect_short}} 툴킷 명령행을 사용하여 LoopBack 프로젝트를 작성하려면 다음 단계를 완료하십시오.
1.  명령행 인터페이스에서 다음 명령을 입력하십시오. LoopBack 애플리케이션을 작성하고 관리하는 데 사용합니다.
	```bash 
	apic loopback
	```
	>![정보]
	>이 튜토리얼에서는 weather-data라는 프로젝트를 작성합니다.
2.  프롬프트에서 `weather-data`를 프로젝트 이름으로 입력하고 **Enter**를 누르십시오.
	```bash
	? What's the name of your application? weather-data
	```
  	>![중요]
  	>일반적으로 프로젝트 이름에는 공백(" "), 슬래시("/"), 앰퍼샌드("&"), 앳("@"), 더하기("+"), 퍼센트("%") 및 콜론(":")을 제외한 모든 문자가 포함될 수 있습니다.
3.  프로젝트를 작성할 디렉토리의 이름을 입력하십시오. **Enter**를 눌러 프로젝트와 이름이 같은 디렉토리를 사용하거나 새 이름을 입력하고 **Enter**를 누르십시오.
	```bash
	? Enter name of the directory to contain the project: weather-data
	```
4.  사용할 LoopBack 버전을 선택하십시오. 현재 제품 버전 선택: 3.x.
	```bash
	? Which version of LoopBack would you like to use? 
  	2.x (long term support) 
	? 3.x (current) 
	```
5.  화살표 키를 사용하여 **empty-server**를 선택함으로써 작성할 애플리케이션 유형을 지정하십시오.
	```bash
	? What kind of application do you have in mind? (Use arrow keys)
	? empty-server (An empty LoopBack API, without any configured models or datasources)
  	hello-world (A project containing a basic working example, including a memory database)
  	notes (A project containing a basic working example, including a memory database)
	```
6.  **Enter**를 눌러 비어 있는 LoopBack API를 작성하십시오. 

프로젝트 디렉토리를 작성하면서 도구에서 다수의 메시지를 표시하며 다수의 디렉토리 및 파일을 이에 추가합니다. 또한 npm install을 실행하여 package.json에서 지정한 대로 모든 프로젝트 종속 항목을 설치합니다. 이 프로세스는 node_modules 디렉토리를 작성하며 시간이 걸릴 수 있습니다.

비어 있는 LoopBack 프로젝트에는 다음 디렉토리가 포함되어 있습니다.
- 서버: 서버 모델과 데이터 소스 정의 및 기타 서버 코드 포함
- 정의: YAML 정의 파일 포함
- node_modules: Node.js에서 작성됨


### API Designer 인터페이스를 사용하여 LoopBack 프로젝트 작성
{: #create_apid_tut_create_api_node}

API Designer를 사용하여 LoopBack 프로젝트를 작성하려면 다음 단계를 완료하십시오.
1.  명령행 인터페이스에서 다음 명령을 입력하여 API Designer를 시작하십시오.
	```bash
	apic edit
	```
	![](images/api-designer-1.png)
	>![정보]
	>위의 명령은 {{site.data.keyword.apiconnect_short}} 툴킷을 초기화하고 완료되면 기본 브라우저에서 API Designer를 시작합니다.
	>![정보]
	>이 튜토리얼에서는 weather-data라는 프로젝트를 작성합니다.
2.  UI 탐색 분할창을 아직 고정하지 않은 경우 이동 위치 아이콘 ![](images/navigate-to.png)을 클릭하십시오. API Manager UI 탐색 분할창이 열립니다. UI 탐색 분할창을 고정하려면 핀 메뉴 아이콘 ![](images/pinned.png)을 클릭하십시오.
3.  사이드바에서 프로젝트 더하기 아이콘 ![](images/add-icon.png)을 클릭하십시오.
4.  **LoopBack 프로젝트 작성**을 클릭하십시오. **새 LoopBack 프로젝트 추가** 대화 상자가 표시됩니다.
5.  프로젝트 템플리트로 **empty-server**를 선택하십시오.
6.  **LoopBack 버전**으로 버전 3.x(현재 버전)을 선택하십시오.
7.  표시 이름 및 이름 필드에 `weather-data`를 입력하십시오.
8.  **프로젝트 디렉토리**의 경우 **찾아보기** 단추를 클릭하여 1단계에서 작성한 `weather-data` 폴더를 선택하십시오.
 ![](images/api-designer-2.png)
9. **추가**를 클릭하여 프로젝트를 추가하십시오.
	>![정보]
	>프로젝트 디렉토리를 작성하여 여러 디렉토리와 파일을 추가함에 따라 **새 LoopBack 프로젝트 추가** 창에 여러 메시지가 표시됩니다. 또한 npm install을 실행하여 package.json에서 지정한 대로 모든 프로젝트 종속 항목을 설치합니다. 이 프로세스는 node_modules 디렉토리를 작성하며 시간이 걸릴 수 있습니다.
	
	>비어 있는 LoopBack 프로젝트에는 다음 디렉토리가 포함되어 있습니다.
	- 서버: 서버 모델과 데이터 소스 정의 및 기타 서버 코드 포함
	- 정의: YAML 정의 파일 포함
	- node_modules: Node.js에서 작성됨
10. **완료**를 클릭하여 **새 LoopBack 프로젝트 추가** 대화 상자를 닫으십시오.
11. 1단계의 명령행으로 돌아가서 `Ctrl + C`를 입력하여 **API Designer**를 종료하십시오. `Y`를 입력하여 종료를 확인하십시오.
12. 브라우저 세션을 닫으십시오.

---
## 새 데이터 소스 및 모델 추가
{: #add_tut_create_api_node}

API Designer를 사용하여 새 모델과 데이터 소스를 LoopBack 프로젝트에 추가하려면 다음 단계를 완료하십시오.

### 데이터 소스 추가
{: #add_ds_tut_create_api_node}

API Designer를 사용하여 LoopBack 프로젝트에 새 데이터 소스를 추가하려면 다음 단계를 완료하십시오.
1. `명령행에서 LoopBack 프로젝트 작성`에 설명된 대로 LoopBack 프로젝트("weather-data" 프로젝트)를 작성하고 현재 작업 디렉토리가 프로젝트 루트 디렉토리인지 확인해야 합니다.
	```bash
	cd weather-data
	```
2. 명령행에서 다음 명령을 입력하십시오.
	```bash
	apic edit
	```
	일시정지한 후 콘솔에 다음 메시지가 표시됩니다.
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer가 기본 웹 브라우저에서 열리고 최근에 로그인하지 않은 경우 처음에 로그인 페이지를 표시합니다.  
	>![정보]
	>{{site.data.keyword.Bluemix}} 계정을 사용하여 로그인하거나 계정을 작성할 수 있습니다.
3. **데이터 소스** 아이콘 ![](images/datasource-icon.png)을 클릭하십시오.
4. **추가**를 클릭하십시오. 새 LoopBack 데이터 소스 창이 열립니다.
5. **이름** 텍스트 필드에 `weatherDS`를 입력하십시오.
	>![정보]
	>데이터 소스 이름에 영숫자 문자, 대시 및 밑줄을 사용할 수 있습니다.
6. **새로 작성**을 클릭하십시오.
7. 기본적으로 **커넥터** 설정은 **인메모리 db**를 표시하며 다른 설정은 공백입니다. 지금은 기본 설정을 유지하십시오. 그러면 API Designer가 새 데이터 소스를 자동으로 저장합니다.
	>![정보]
	>인메모리 데이터 소스는 LoopBack에 기본 제공되며 개발과 초기 테스트용으로만 적합합니다. 모델을 데이터베이스 서버와 같은 실제 데이터 소스에 연결할 준비가 되면 **커넥터** 설정을 적절하게 변경하고 IBM Knowledge Center 주제, <https://www.ibm.com/support/knowledgecenter/SSMNED_5.0.0/com.ibm.apic.toolkit.doc/tapim-connector-install.html#task_i2p_dnw_vv>LoopBack 커넥터 설치 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")의 지시사항에 따라 데이터 소스 커넥터를 커넥터 유형에 맞게 적절하게 설치하고 **저장** 아이콘 ![](images/save-icon.png)을 클릭하십시오. API Designer에서 데이터 소스에 대한 연결을 자동으로 테스트합니다. 테스트에 성공하면 **성공 - 데이터 소스 연결 테스트 성공** 메시지가 표시됩니다.
8. 테스트 연결 아이콘 ![](images/db-test-icon.png)을 클릭하여 데이터 소스 연결을 테스트하십시오. "데이터 소스 연결 테스트 성공" 메시지가 표시됩니다.
9. 모든 데이터 소스를 클릭하십시오. 데이터 소스가 데이터 소스의 목록에 표시되고 편집기가 새 데이터 소스에 대한 설정으로 server/datasources.json 파일을 업데이트합니다.

### 모델 추가
{: #add_model_tut_create_api_node}

API Designer를 사용하여 새 모델을 LoopBack 프로젝트에 추가하려면 다음 단계를 완료하십시오.
1. 모델 아이콘 ![](images/models-icon.png)을 클릭하십시오.
2. 추가를 클릭하십시오. 새 LoopBack 모델 창이 열립니다.
3. 이름 텍스트에서 weather를 입력한 다음 새로 작성을 클릭하십시오.
4. 데이터 소스 필드에서 weatherDS를 선택하십시오.
	![](images/new-model-1.png)
5. 특성에서 특성 추가  아이콘 ![](images/add-icon.png)을 클릭하십시오.
6. 특성 이름 텍스트 필드에 zip_code를 입력하십시오.
7. 유형에서는 숫자를 선택하십시오.
8. 필수를 선택하여 특성이 필수가 되게 하십시오. 즉 모델 인스턴스를 추가하거나 업데이트할 때 값이 필요합니다. 
9. ID를 선택하여 특성에 고유한 ID가 있는지 확인하십시오. 지금은 기타 설정에 대해 기본값을 유지하십시오.
	- 배열: 특성이 지정된 유형의 요소가 있는 JavaScript 배열인지 여부입니다.
	- 인덱스: 특성이 데이터베이스 인덱스인 열(필드)을 나타내는지 여부입니다.
	- 설명: 특성의 텍스트 설명입니다.
9. 특성 추가 아이콘 ![](images/add-icon.png)을 다시 클릭하여 다른 특성을 추가하십시오.  아래 테이블을 참조하여 나머지 특성을 완료하십시오.
![](images/new-model-property-1.png)
10. 저장 아이콘 ![](images/save-icon.png)을 클릭하여 변경사항을 저장하십시오.
11. 모든 모델을 클릭하여 모델 편집을 완료하십시오.

그러면 weather-data LoopBack 프로젝트에 새 데이터 소스와 모델의 추가를 완료합니다.

---

## LoopBack 프로젝트 테스트
{: #test_tut_create_api_node}

>![정보]
	>"새 모델 및 데이터 소스 추가" 섹션을 완료한 후 {{site.data.keyword.apiconnect_short}} 디자이너를 종료하지 않은 경우 아래 2단계로 바로 이동할 수 있습니다.
	
API Designer Explore 도구를 사용하여 API 엔드포인트를 테스트하려면 다음 단계를 완료하십시오.
1. 명령행에서 다음 명령을 입력하십시오.
	```bash
	apic edit
	```
	일시정지한 후 콘솔에 다음 메시지가 표시됩니다.
	```bash
	Express server listening on http://127.0.0.1:9000
	```
	API Designer가 기본 웹 브라우저에서 열리고 최근에 로그인하지 않은 경우 처음에 로그인 페이지를 표시합니다.
	
2. 로컬 테스트 서버를 시작하십시오.
	a. 화면 맨 아래에 잇는 테스트 콘솔에서 **서버 시작** 아이콘 ![](images/test-icon.png)을 클릭하십시오.
	![](images/start-server-1.png)
	b. 실행 중 메시지가 표시될 때까지 기다리십시오.
	![](images/running-server-1.png)

	>![정보]
	>프로젝트 구성과 다른 프로세스가 실행 중인지 여부에 따라 다른 포트 번호가 표시될 수 있습니다.
3. **http://127.0.0.1:port_number**를 클릭하여 API 루트 엔드포인트를 표시하십시오. 기본 LoopBack(비어 있음 또는 hello-world) 프로젝트의 경우에는 아래와 유사한 내용이 표시됩니다.
	```bash
	{"started":"2017-05-24T19:21:47.807Z","uptime":80.876}
	```
	>![정보]
	>프로젝트를 중지하려면 **서버 중지** 아이콘 ![](images/stop-icon.png)을 클릭하십시오.
	>![](images/stop-server-1.png)
	
	>다시 시작하려면 **서버 다시 시작** 아이콘 ![](images/restart-icon.png)을 클릭하십시오.
	>![](images/restart-server-1.png)
	
4. API Designer Explore 도구를 보려면 **탐색** 아이콘 ![](images/explore-icon.png)을 클릭하십시오. 사이드바에 API에 있는 LoopBack 모델의 REST 오퍼레이션이 모두 표시됩니다. PersistedModel을 기반으로 하는 모델에는 루프백 문서에 설명된 대로 기본적으로 [표준 작성, 읽기, 업데이트 및 삭제 오퍼레이션 세트![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://loopback.io/doc/en/lb2/PersistedModel-REST-API){: new_window}가 있습니다.

5. 왼쪽 분할창의 **weather.create** 오퍼레이션을 클릭하여 엔드포인트를 표시하십시오.
![](images/explore-test-1.png)
센터 분할창에는 매개변수, 보안, 모델 인스턴스 데이터 및 응답 코드 등의 엔드포인트에 대한 요약 정보가 표시됩니다. 오른쪽 분할창에서는 curl 명령을 사용하여 엔드포인트를 호출하는 템플리트 코드 및 언어(예: Ruby, Python, Java 및 Node)가 제공됩니다.

6. API Designer Explore 도구에서 REST 엔드포인트를 테스트하려면 다음 단계를 완료하십시오.
    1. 오른쪽 분할창에서 **시도**를 선택하십시오. `id` 데이터 요소가 있는 경우 테스트를 실행하기 전에 이 데이터 요소를 생성된 데이터에서 제거하십시오. 
	
	2. 아래로 스크롤하여 **매개변수**로 이동하고 **생성**을 클릭하여 더미 데이터를 생성하십시오. 기본적으로 생성된 데이터에는 `zip_code`, `current_temperature`, `current_humidity`, `tonight_temperature_low`, `tonight_temperature_high`, `tonight_humidity_low` 및 `tonight_humidity_high` 특성이 포함됩니다.
	
	3. **오퍼레이션 호출**을 클릭하십시오.
	![](images/explore-test-2.png)
	
>![문제점 해결]
>localhost의 신뢰할 수 없는 인증서로 인해 오류 메시지가 표시되는 경우 API Designer Explorer 도구에서 오류 메시지에 제공되는 링크를 클릭하여 인증서를 승인한 다음 계속하여 웹 브라우저에서 오퍼레이션을 호출하십시오. 정확한 프로시저는 사용 중인 웹 브라우저에 따라 달라집니다. 브라우저에서 직접 REST 엔드포인트를 로드하는 경우 {"name":"PreFlowError","message":"unable to process the request"} 메시지가 표시됩니다. 필수 헤더와 기타 요청 매개변수를 포함하므로 API Designer Explorer 도구를 사용하여 브라우저에서 REST 엔드포인트를 테스트해야 합니다.
>
>![문제점 해결]
>다음과 같은 페이로드와 함께 **422 - 처리할 수 없는 엔티티** 응답 코드가 표시되면,
>![](images/explore-test-3.png)
>
>생성된 데이터에서 제거되지 않은 `id` 데이터 요소가 없는지 확인하십시오. ID 요소가 있는 경우, 해당 요소를 제거한 다음 테스트를 다시 실행하십시오.
>![문제점 해결]
>**요청 본문을 구문 분석하는 데 실패** 오류가 표시되면 마지막 `humidity_high` 번호 다음에 있는 쉼표를 제거해야 합니다.
7. **데이터** 섹션에 표시된 JSON의 값을 편집하십시오. 생성된 더미 데이터를 변경한 다음 **오퍼레이션 호출**을 다시 클릭하십시오. 입력한 JSON 인스턴스 데이터와 함께 요청과 응답 매개변수가 표시되어야 합니다.
![](images/explore-test-4.png)

8. 오퍼레이션에서 모델 인스턴스를 추가했는지 확인하려면 **weather.find**를 클릭하십시오. **오퍼레이션 호출**을 클릭하여 모든 날씨 인스턴스를 표시하십시오. 두 개의 모델 인스턴스가 있는 예는 다음과 같습니다.

	![](images/explore-test-5.png)
---

### 이 튜토리얼에서 수행한 작업
{: #conclusion_tut_create_api_node}

이 튜토리얼에서 다음과 같은 작업을 완료했습니다.
1. {{site.data.keyword.apiconnect_short}} 툴킷 명령행을 사용하여 새 LoopBack 프로젝트 작성.
2. {{site.data.keyword.apiconnect_short}} 툴킷에서 API Designer를 사용하여 LoopBack 프로젝트에 새 모델과 데이터 소스 추가.
3. API Designer Explore 도구를 사용하여 API 엔드포인트 테스트.


---

## 다음 단계
{: #next_tut_create_api_node}

[REST 서비스 관리](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_rest_landing) 또는 [SOAP 서비스 관리](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_soap_api).

작성 > **관리** > 보안 > 소셜화 > 분석

 
[important]: ./images/important.png "중요!"
[info]: ./images/info.png "정보"
[troubleshooting]: ./images/troubleshooting.png "문제점 해결" 


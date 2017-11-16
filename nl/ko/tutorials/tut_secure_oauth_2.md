---
copyright:
  years: 2017
lastupdated: "2017-09-30"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 2LO(Two-Legged OAuth)로 API 보호

기간: 10분  
스킬 레벨: 초보자

## 목표

이 튜토리얼에서는 2LO(Two-Legged OAuth) 2.0 플로우를 사용한 보안을 안내합니다. 이 애플리케이션 플로우에서 OAuth 클라이언트가 권한 서버로 요청을 시작하고 액세스 토큰을 수신합니다. 그런 다음 OAuth 클라이언트에서 토큰을 사용하여 API를 통해 보호되는 자원에 액세스할 수 있습니다.

## 전제조건

시작하기 전에 다음 튜토리얼을 완료해야 합니다.  
- [IBM Bluemix를 사용하여 클라이언트 ID와 클라이언트 시크릿 키로 API 보호](tut_secure_id_secret_bm.html)
또는
- [툴킷을 사용하여 클라이언트 ID와 클라이언트 시크릿 키로 API 보호](tut_secure_id_secret_tk.html)

## 프로시저

1. OAuth Provider API를 작성하고 OAuth 스키마를 선택하십시오.  
	a. **초안**을 열고 **API**를 선택한 다음 **추가** > **OAuth 2.0 Provider API**를 클릭하십시오.  
    ![](images/oauth_provider_1.png)
	b. "OAuth Endpoint API"로 제목을 지정하십시오. (이름과 기본 경로는 자동으로 채워져야 합니다.)  
	c. **API 작성**을 선택하십시오.  
	d. 새로 작성된 OAuth Endpoint API에서 **OAuth 2** 패널로 이동(또는 아래로 스크롤하여 이동)한 다음 클라이언트 유형으로 "기밀"을 선택하십시오.  
	e. 범위에서 _scope1_의 이름을 _view_current_로 바꾸십시오. _scope2_ 및 _scope3_을 삭제하십시오.  
	f. **권한 부여**에서 **내재적**, **비밀번호** 및 **액세스 코드**의 선택을 취소하십시오. **애플리케이션**은 선택된 상태로 두십시오.  
	![](images/oauth_provider_2.png)  
	g. API를 저장하십시오.  

2. OAuth를 포함하도록 Weather Provider API의 보안 정의를 업데이트하십시오.  
	a. _Weather Provider API_로 전환하십시오. (API로 돌아가서 _Weather Provider API_를 선택하십시오.)  
	b. 보안 정의에서 OAuth의 새 정의를 추가하십시오. 그런 다음 이름을 "OAuth definition"로 지정하십시오.  
	c. 플로우 필드에서 **애플리케이션**을 선택하십시오.  
	d. 토큰 URL _<your base URL>/oauth-endpoint-api/oauth2/token_을 입력하십시오.  
	e. 새 범위, view_current를 추가하십시오.  
	![](images/oauth_security_definition_1.png)
	f. **보안**에서 **OAuth 정의** 및 **view_current**를 선택하고 클라이언트 ID와 클라이언트 시크릿을 선택한 상태로 두십시오.  
	![](images/oauth_security_definition_2.png)
	g. 저장을 클릭하십시오.  
	h. **초안**으로 다시 이동하여 **제품**을 선택하십시오. Weather Provider 제품에 OAuth Endpoint API를 추가하십시오.  
	i. 제품을 저장하고 샌드박스로 스테이징하십시오.  
	![](images/oauth_security_definition_3a.png)

3. OAuth 보안 구성을 테스트하십시오.  
	a. 업데이트된 제품을 샌드박스에 공개하십시오. **대시보드 > 샌드박스**를 클릭한 다음 제품을 공개하십시오.  
	  ![](images/test_oauth_1.png)
	b. **탐색 > 샌드박스**를 클릭하십시오.  
      ![](images/test_oauth_2.png)
	c. **Weather Provider API**의 오퍼레이션 목록에서 **GET /current**를 클릭하십시오.  
	d. 오른쪽 패널에 클라이언트 ID와 클라이언트 시크릿이 이미 채워져 있습니다.  
	e. **매개변수** 섹션에서 우편번호를 입력하십시오.  
      ![](images/test_oauth_3.png)
	f. **권한** 섹션에서 **권한 부여**를 클릭하여 액세스 토큰을 가져오십시오.  
	g. 액세스 토큰을 받은 후 **오퍼레이션 호출**을 클릭하여 테스트를 완료하십시오.  
      ![](images/test_oauth_4.png)

4. 요청에는 액세스 토큰, 클라이언트 ID 및 클라이언트 시크릿이 포함됩니다. 요청을 통해 액세스 토큰만 전달하려면 Weather Provider API의 보안 요구사항에서 클라이언트 ID와 시크릿을 제거해야 합니다.  
    ![](images/test_oauth_5.png)

5. Weather Provider API를 저장하십시오. 그런 다음 샌드박스에 스테이징하여 공개하십시오. 탐색 도구에서 이전과 동일하게 테스트를 실행하십시오.  
    ![](images/test_oauth_6.png)
    
## 결론
이 튜토리얼에서는 OAuth Provider API를 작성하고 OAuth를 포함하도록 API의 보안 정의를 업데이트하며 보안 구성을 테스트하는 방법을 배웠습니다.

---

## 다음 단계

[개발자 포털을 설정 및 구성](tut_config_dev_portal.html)하여 API의 소셜화를 시작하십시오.

작성 > 관리 > **보안** > 소셜화 > 분석

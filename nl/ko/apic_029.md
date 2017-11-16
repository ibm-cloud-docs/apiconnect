---

copyright:
  years: 2017
lastupdated: "2017-09-28"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 새로운 기능

{{site.data.keyword.apiconnect_full}}에는 다음 개선사항이 포함되어 있습니다.

- **분석을 위해 개발자 포털 REST API 참조 및 지원 추가**: 개발자 포털 REST API를 사용하면 카탈로그 API를 분석할 수 있습니다. 자세한 정보는 [분석 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}을 참조하십시오.

- **API 작성 시 분석 섹션 추가**: API에 대한 분석 데이터를 수집하는 데 사용할 수 있는 API의 기존 매개변수를 정의하고
지정할 수 있습니다. 자세한 정보는 [REST API 정의 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window}을 참조하십시오.

- **개발자 포털에서 두 요소 인증 사용 장려**: 개발자 포털 사용자는 TFA 규칙 모듈을 적용하여 계정에서 두 요소 인증(TFA)을
설정하는 것이 좋습니다. 자세한 정보는 [개발자 포털 계정에서 두 요소 인증 설정 장려 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}을 참조하십시오.

- **통합 지불 청구 및 결제 관리에 추가된 기능**:
    관리자:
	* API 고객이 신용 카드로 등록할 수 있는 월별 선불 비용 청구 등록 플랜을 작성하십시오. 자세한 정보는 [제품 사용에 대한 비용 청구 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window}를 참조하십시오.
	* 스트라이프 계정을 활용하여 등록의 결제를 관리하십시오.
	* 새로운 등록자를 위해 등록 플랜의 무료 평가판 기간(일)을 지정하십시오. Payment automatically begins after the trial days expire.
	고객:
	* 하나 이상의 API를 포함하는 제품을 사용할 수 있도록 개발자 포털에서 요금 기반 플랜에 등록하십시오. 자세한 정보는 [튜토리얼: 가격이 책정되는 플랜에 등록 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window}을 참조하십시오.

- **게이트웨이에서 자동으로 호출 바꾸기**: 프록시에서 정책의 마지막 호출을 바꿀 수 있습니다. 이 작업은 성능을 향상시키기 위해
게이트웨이에서 자동으로 수행합니다. 자세한 정보는 [API 특성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}을 참조하십시오.

- **OAuth 범위는 써드파티 응답을 통해 수정 가능**: API 범위 값을 대체하도록 외부 서버를 구성할 수 있습니다. 자세한 정보는 [범위 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}을 참조하십시오.

- **새 API 이벤트 필드**: 다음 API 이벤트 필드가 추가되었습니다.
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

자세한 정보는 [API 이벤트 레코드 필드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} 및 [REST API 호출을 사용하여 분석 데이터 가져오기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window}을
참조하십시오.

- **경로 재지정 URL의 새 조회 매개변수**: 써드파티에 사용 가능한 정보에 새 조회 매개변수가 추가되었습니다. 새 매개변수는 <code>provider</code>, <code>providerid</code> 및
<code>g-transid</code>입니다. 자세한 정보는 [경로 재지정 URL을 통해
인증 및 권한 부여 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html)을 참조하십시오.{:new_window}.

- **테스트 도구에서 브라우저 CORS 경보 방지**: API Designer 테스트 도구에서 CORS 경보를 트리거할 수 있는 브라우저에서 요청을 보냅니다. CORS 경고를
방지하기 위해 브라우저가 아니라 API Designer를 호스트하는 서버에서 테스트 메시지를 보내도록 **프록시 사용** 선택란이 제공됩니다. 자세한 정보는
[API Designer 테스트 도구로 API 테스트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}을 참조하십시오.

- **Mobile First Foundation이 아니라 써드파티 OAuth로 API 보호**: IBM MobileFirst&tm; Platform Foundation 권한 서버가 아니라 써드파티 OAuth 제공자로 API를 보호합니다. 자세한 정보는
[써드파티 OAuth 제공자 통합 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}을 참조하십시오.

- **OIDC(OpenID Connect)로 API 보호**: OIDC 구성에 따라 사용자 정의하는 사전 제공된 샘플 OAuth Provider API를 사용하여
OIDC(OpenID Connect)로 API를 보호할 수 있습니다. 자세한 정보는 [OpenID Connect로
API 보호 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}를 참조하십시오.

- **SOAP 업데이트 조치를 통해 더 이상 API를 겹쳐쓰지 않음**: WSDL 정의에서 SOAP API를 업데이트할 때 새 WSDL의 영향을 받은 API의
섹션만 바뀌고 다른 섹션은 변경되지 않습니다. 이전 릴리스에서는
업데이트 조치를 수행하면 모든 디자인 특성과 어셈블리 구성을 포함하여 SOAP API 정의의
구성을 겹쳐씁니다. 자세한 정보는 [SOAP API
업데이트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}을 참조하십시오.

- **개발자 포털에서 스팸으로부터 보호하기 위해 Honeypot 사용**: Honeypot 보호에서는 스팸 봇이 양식을 제출하지 못하게 개발자 포털 사이트를 보호하는 보안 메커니즘을 제공합니다. 스팸 봇 활동이 발견되면 양식 제출이 차단됩니다. 자세한 정보는
[Honeypot을 사용하여 스팸으로 보호 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}를 참조하십시오.

- **개발자 포털에서 보기 모듈 사용**: 보기 UI 모듈을 사용하여 개발자 포털에서 애플리케이션, API 및 제품의 컨텐츠 목록 등의 새 보기를 작성하십시오. 자세한 정보는 [개발자 포털에서 보기 모듈 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}을 참조하십시오.

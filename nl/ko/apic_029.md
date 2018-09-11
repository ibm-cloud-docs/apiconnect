---

copyright:
  years: 2017-2018
lastupdated: "2018-05-23"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 새로운 기능

{{site.data.keyword.apiconnect_full}}에는 다음 개선사항이 포함되어 있습니다.


- **어셈블리 발견 구성에서 새 오류 케이스가 지원됨**: 새 오류 케이스 *BadRequestError*, *UnauthorizedError* 및 *ForbiddenError*가 API 어셈블리의 발견 구성에서 지원됩니다. [어셈블리 발견에서 지원되는 오류 케이스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){:new_window}를 참조하십시오.
- **선택한 API에 useBytesSent 조회 매개변수가 추가됨**: 분석 필드 *bytes_sent*가 사용량을 계산하는 데 사용될 수 있도록 하는 *useBytesSent* 매개변수가 추가되었습니다. 자세한 정보는 [지정된 애플리케이션에서 사용되는 모든 리소스에 대한 데이터 사용량 정보 리턴 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){:new_window}, [지정된 조직에서 사용되는 모든 리소스에 대한 데이터 사용량 정보 리턴 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){:new_window}, [지정된 애플리케이션에서 사용되는 모든 리소스에 대한 결합된 데이터 사용량 리턴 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){:new_window} 및 [지정된 조직에서 사용되는 모든 리소스에 대한 결합된 데이터 사용량 리턴 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){:new_window}을 참조하십시오.
**호출 또는 프록시 정책 대상 URL의 조회 매개변수 값에서 + 문자를 인코딩할 수 있음**: 새 *x-ibm-gateway-queryparam-encode-plus-char* API 특성이 있습니다. 이 특성의 값을 *true*로 설정하면 호출 및 프록시 정책 target-url의 조회 매개변수 값에 있는 모든 "+" 문자가 "%2F"로 인코딩됩니다. 이전 릴리스에서는 +가 항상 %2F로 인코딩되었습니다. 이제 기본 동작은 인코딩을 수행하지 않는 것입니다. [API 특성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}을 참조하십시오.
- **호출 또는 프록시 정책에 대한 응답 규칙에 JSON 구문 분석기를 적용할 수 있음**: 새 *x-ibm-gateway-api-enforce-response-limits* API 특성이 있습니다. 이 특성의 값을 *true*로 설정하면 응답 규칙에 JSON 구문 분석기를 적용할 수 있습니다. 응답 본문 크기가 DataPowere 도메인에 설정된 JSON 구문 분석기 한계보다 크면 상태 코드 500이 리턴됩니다. [API 특성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}을 참조하십시오.
- **맵 정책에 대한 성능 향상 가능성**: 매우 복잡한 스키마 정의가 정책 출력 정의에서 참조되는 경우 맵 정책에 대한 성능 향상을 제공할 수 있는 새 *x-ibm-gateway-optimize-schema-definition* API 특성이 있습니다. [API 특성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}을 참조하십시오.

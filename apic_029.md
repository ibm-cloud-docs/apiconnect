---

copyright:
  years: 2017-2019
lastupdated: "2018-05-23"

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal

subcollection: apiconnect

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# What's new
{: #apic_029}

{{site.data.keyword.apiconnect_full}} includes the following enhancements:


- **New error cases are supported by the assembly catch construct**: The following new error cases are supported by the catch construct in an API assembly: *BadRequestError*, *UnauthorizedError*, and *ForbiddenError*. See [Error cases supported by assembly catches ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/ref_toolkit_catch_errors.html){: #new_window}.
- **Added the useBytesSent query parameter to selected APIs**: The *useBytesSent* parameter was added that allows the analytics field *bytes_sent* to be used to calculate the usage. See [Return data usage information for all the resources used by a given application ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usageGET.html){: #new_window}, [Return data usage information for all the resources used by all applications in the given organization ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps_data-usageGET.html){: #new_window}, [Return combined data usage for all resources used by a given application ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_apps__appID__data-usage_allGET.html){: #new_window}, and [Return combined data usage for all the resources used by a given organization ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/apirest_reference_topics/rest_op_portal_orgs__orgID__analytics_data-usage_allGET.html){: #new_window} for more information.
**You can encode + characters in the query parameter values of the target URL of an Invoke or Proxy policy**: There is a new *x-ibm-gateway-queryparam-encode-plus-char* API property; if set to a value of *true*, all "+" characters in the query parameter values of the target-url of Invoke and Proxy policies are encoded to "%2F". In previous releases, + were always encoded to %2F. Now, the default behavior is to not do the encoding. See [API properties ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **You can enforce the JSON parser on the response rule for an Invoke or Proxy policy**: There is a new *x-ibm-gateway-api-enforce-response-limits* API property; setting this property to a value of *true* allows the JSON parser to be enforced on the response rule. If the response body size is higher than the JSON parser limit set in the DataPower domain, a status code of 500 is returned. See [API properties ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.
- **Potential for performance improvement to the map policy**: There is a new *x-ibm-gateway-optimize-schema-definition* API property that can provide a performance improvement to the map policy when a very complex schema definition is referenced by a policy output definition. See [API properties ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){: #new_window}.

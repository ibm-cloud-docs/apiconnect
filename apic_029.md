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

# What's new

{{site.data.keyword.apiconnect_full}} includes the following enhancements:

- **Added support and a reference for Developer Portal REST APIs for analytics**: Developer Portal REST APIs help you analyze your catalog APIs. For more information, see [Analytics ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apirest.doc/analytics.html){:new_window}.

- **Added the Analytics section when creating an API**: You can define and specify existing Parameters for your API that can be used to gather analytics
data about the API. See [Composing a REST API definition ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_creating_apis.html){:new_window} for more information.

- **Encourage the use of two-factor authentication in the Developer Portal**: You can encourage users of your Developer Portal to set up two-factor authentication (TFA) on
their account by applying a TFA Rules module. For more information, see [Encouraging users to set up two-factor authentication on their Developer Portal account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapim_portal_two_factor_auth_enforce.html){:new_window}.

- **Features added to the integrated billing and payment management**: 
    Administrator:
	* Create monthly prepaid billing subscription Plans that your API customers can subscribe to with a credit card. See [Billing for the use of your Products ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/capim_product_billing.html){:new_window} for more information.
	* Leverage a Stripe account to manage the payments for your subscriptions.
	* Specify a number of free trial days in your subscription Plan for new subscribers. Payment automatically begins after the trial days expire.
	Customer:
	* Subscribe to fee-based Plans in the Developer Portal that allow you to use Products that contain one or more APIs. See [Tutorial: Subscribing to a Plan with pricing ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_sub_paid_plan.html){:new_window} for more information.

- **Invoke automatically replaced in the gateway**: The last invoke in your policy might be replaced by a proxy. This is done automatically by the
gateway to improve performance. For more information, see: [API properties ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/configuration_props.html){:new_window}.

- **OAuth scope can be modified by third-party responses**: You can configure an external server to override the API scope value. For more information, see: [Scope ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_scope.html){:new_window}.

- **New API event fields**: Added the following API event fields:
    * billing.trial_period_days
	* billing.amount
	* billing.currency
	* billing.model
	* billing.provider
	* client_id
	* immediate_client_ip
	* latency_info2.task
	* latency_info2.ended

See [API event record fields ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/rapim_analytics_apieventrecordfields.html){:new_window} and [Obtaining analytics data by using REST API calls ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapim_exportanalytics_api_calls.html){:new_window} for more
information.

- **New query parameters for the Redirect URL**: New query parameters have been added to the information available for a third party. The new parameters are <code>provider</code>, <code>providerid</code>, and
<code>g-transid</code>. For more information, see [Authenticating
and authorizing through a redirect URL ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_apionprem_redirect_form_.html){:new_window}.

- **Preventing browser CORS alerts in the Test tool**: The API Designer Test tool sends requests from the browser that can trigger CORS alerts. To
prevent CORS alerts, the **Enable Proxy** check box is provided to send test messages from the server that hosts API Designer rather than from the browser. For more information,
see [Testing an API with the API Designer test tool ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/task_toolkit_testing.html){:new_window}.

- **Secure APIs with third party OAuth instead of Mobile First Foundation**: Secure your API with a third-party OAuth provider instead of the IBM MobileFirst&tm; Platform Foundation  authorization server. For
more information, see [Integrating third party OAuth provider ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_oauth_introspection.html){:new_window}.

- **Secure your APIs with OpenID Connect (OIDC)**: You can secure your APIs with OpenID Connect(OIDC) by using
a pre-supplied sample OAuth Provider API that you customize in accordance with your OIDC configuration. For
more information, see [Securing your APIs with OpenID Connect ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_sec_api_config_oidc.html){:new_window}.

- **SOAP update action no longer overwrites the API**: When you update a SOAP API from a WSDL definition, only those sections of the API that are
affected by the new WSDL are replaced, the other sections are unchanged. In previous releases, the
update action completely overwrote the configuration of the SOAP API definition, including all
design properties and assembly configuration. For more information, see [Updating a SOAP
API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.apionprem.doc/tapic_soap_update.html){:new_window}.

- **Use Honeypot for spam protection in the Developer Portal**: Honeypot protection provides security mechanisms to protect your Developer Portal site from form submission by spam bots. If spam bot activity is detected, form submission is blocked. For more
information, see [Using Honeypot for spam protection ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tapic_portal_honeypot.html){:new_window}.

- **Using the Views module in the Developer Portal**: Create new views in the Developer Portal, such as content lists of Products, APIs, and applications, by using the Views UI module. For more information, see [Using the Views module in the Developer Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_views.html){:new_window}.

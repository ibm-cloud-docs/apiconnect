---

copyright:
  years: 2017
lastupdated: "2017-07-14"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# What's new

{{site.data.keyword.apiconnect_full}} includes the following enhancements:
- **Integrated billing and payment management for your APIs**: API providers can use the monetization capability in {{site.data.keyword.apiconnect_short}} to create pricing plans and set rate limits for their API products, collect payments from API consumers, and analyze the usage of their monetized and free API plans. Usage analytics can either be processed by using the integrated API Connect analytics tools, or by offloading them to an existing external system. Your consumers can subscribe themselves to plans, and have their payments made through a credit card processing provider. For more information, see the API Connect developerWorks blog [To win in the API economy, you need a modern approach to API monetization](https://developer.ibm.com/apiconnect/2017/06/30/apic-5072-monetization-overview/).

- **Secure Gateway commands**: You can now use the developer toolkit command-line tool to generate a secure gateway ID and token, and publish a secure gateway product. For more information, see [Generating a secure gateway ID and token](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_secure_gateway.html) and [Publishing a secure gateway product through the CLI](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_pub_secure_gateway_cli.html).

- **(Technical preview) Create applications in the Swift programming language**: You can create applications in the Swift programming language by using Swift Server Generator. Swift Server Generator provides developer toolkit commands for creating Kitura Swift application based on data models that you define and attach to a data source. A full set of REST APIs for working with the back-end data is generated automatically. For more information, see [Using Swift Server Generator](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/capic_swift_overview.html).

- **Categorize APIs and Products in {{site.data.keyword.apiconnect_full}}**: You can define categories for APIs and Products in the API Designer or API Manager UI, and you have the option to expose them in the Developer Portal.  You can also configure taxonomies for your APIs and Products in the Developer Portal. For more information, see [Organizing your APIs and Products into categories](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/tapic_apionprem_categories.html) and [Displaying APIs and Products in categories](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/capic_portal_categories.html).

- **Creating and configuring Rules in the Developer Portal**: You can configure Rules to perform specific actions when they are triggered by specific events in the Developer Portal. For more information, see [Rules in the Developer Portal ](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.devportal.doc/tutorial_portal_rules.html).

- **Including metadata in the OAuth transaction**: You can include arbitrary information as metadata during the OAuth authentication handshake. When the Metadata URL is configured, {{site.data.keyword.apiconnect_short}} sends a request header to the URL and stores the response in the token or payload that contains the token. For more information, see [OAuth metadata](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/con_metadata.html).

- **Enabling OAuth debugging support**: You can activate debugging for OAuth that produces a more detailed report than just an error
message. For more information, see [Troubleshooting OAuth](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/rapic_oauth_troubleshoot.html).

- **Testing OAuth 2.0 with the Developer Portal test tool**: The testing tool in the Developer Portal supports the testing of OAuth 2.0 interactions. For more information, see [Troubleshooting OAuth](https://www.ibm.com/support/knowledgecenter/en/SSFS6T/com.ibm.apic.toolkit.doc/rapic_oauth_troubleshoot.html).

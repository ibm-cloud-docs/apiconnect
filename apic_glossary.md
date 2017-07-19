---

copyright:
  years: 2017
lastupdated: "2017-06-05"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Glossary

The {{site.data.keyword.apiconnect_short}} glossary of terms and definitions.

- **API Developer**: An API Developer creates and configures APIs, Products, and policies for provider organizations of which they are a member. An API Developer can be a member of one or more provider organizations. The API Developer focuses on the technical implementation of APIs more than they do on the business relationship with application developers.

- **API operation**: A unit of a REST API that can be invoked. An API operation comprises an HTTP verb and a URL path that is subordinate to the context root of the API.

- **API Designer**: The UI for creating APIs.

- **API Manager**: The UI for managing APIs, Plans, and Products.

- **application**: A piece of client code that accesses APIs to interact with a service, system, or content. Applications are typically web applications or mobile apps.

- **assembly**: Application programming interface that provides rich functionality for interacting with an application: makes side calls to external services and then transforms and aggregates the response before a response is relayed to the calling application.

- **Catalog**:  A Catalog is a staging target, and behaves as a logical partition of the gateway and the Developer Portal. The URLs for API calls and for the Developer Portal are specific to a particular Catalog.

- **client ID**:  A piece of information that identifies an individual application. An application can invoke an API only if it passes an application key that is recognized by the {{site.data.keyword.apiconnect_short}} system and is granted access to the API. The application key is passed by the client by using an HTTP query parameter.

- **client secret**:  A piece of information that is used together with the application key to verify the identity of an application. An API can be configured to require that client applications supply their application secret with their application key. The application secret functions effectively as a password known only to the application. The application secret is passed by the client by using an HTTP query parameter.

- **community**: A collection of developer organizations. It is used as a grouping construct when publishing APIs. Communities are used to restrict the visibility and accessibility of APIs.An API can be published to selected communities, which means that only application developers within those organizations can see the API.

- **LoopBack model**: A LoopBack model is a JavaScript object that represents application data and includes validation rules, data access capabilities, and business logic. LoopBack models provide a REST API by default, and connect to data sources for access to back-end data.

- **LoopBack data source**: A LoopBack data source is a JavaScript object that represents a back-end service such as a database, REST API (to be consumed), or SOAP web service . Data sources are backed by connectors that then communicate directly with the database or other back-end services.

- **organization**: The entity that owns APIs or applications that use APIs. A provider organization owns APIs and associated Plans, and can additionally own applications. A developer organization owns only applications. An organization has at least one owner. An organization can be a project team, department, or division.

- **Path**: A path defines the route through which users access REST APIs. A path consists of one or more HTTP operations such as GET or POST.

- **Plan**: The packaging construct by which APIs are made available to developers. A Plan makes available a collection of operations from one or more APIs, and is published to communities of application developers. Application developers gain access to APIs by registering applications to access Plans. A Plan carries with it a collection of policy settings. In the simplest form, a Plan defines a single quota policy that applies to all the API operations that are accessed through the Plan. In more advanced cases, additional policies can be associated with a Plan.

- **policy**: A policy is a piece of configuration that controls a specific aspect of processing in the Gateway server during the handling of an API invocation at run time. Policies are the building blocks of assembly flows. Policies provide the means to configure capability, such as security, logging, routing of requests to target services, and transformation of data from one format to
another. Policies can be configured in the context of an API or in the context of a Plan.

- **Product**: Products provide a method by which you can group APIs into a package that is intended for a particular use. Additionally, they contain Plans, which can be used to differentiate between different offerings. You can create Plans only within Products, and these Products are then published in a catalog.

- **proxy**: Application programming interface that forwards requests to a user-defined back-end resource and relays responses back to the calling application.

- **publish**: The process of moving an application or Product from staging so that the Plans and APIs included within it are available for application developers to access and use.

- **role**: A role defines permissions that can enable functionality for users. Each role has a different set of permissions.

- **Sandbox catalog**:  In a Sandbox catalog, approvals are bypassed for publishing and lifecycle actions. Pending approvals are cancelled when a non-Sandbox catalog is converted to a Sandbox. A Sandbox catalog is used for testing APIs that are under development.

- **security definition**: A security definition specifies all the settings for a particular aspect of API security; for example, the user registry that you use to authenticate access to the API.

- **SSL Profile**: An SSL profile is used to secure the transmission of data through web sites. SSL certificates guarantee that information you submit to web sites will not be stolen or tampered with.

- **stage**: The process of moving an application or product from draft status to a catalog in preparation for publishing.

- **subscription**:  A subscription is the means by which an application developer gains access to the resources provided by an API. An application developer uses the Developer Portal to subscribe to the plan in which the API is published.

- **user registry**: A user registry is a way of securing access to catalogs and APIs. The user can protect APIs with a user registry so that user credentials must be supplied when an API is called.

- **vendor extension**:  A vendor extension is added to a REST API to extend the OpenAPI (Swagger 2.0) specification.

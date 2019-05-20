---

copyright:
  years: 2017
lastupdated: "2017-10-10"

subcollection: apiconnect

keywords: IBM Cloud, APIs, lifecycle, catalog, manage, toolkit, develop, dev portal, tutorial

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 管理 API 和产品版本
{: #tut_manage_version_landing}

发布 API 以及包含该 API 的产品后，API 提供者通常希望或需要更新这些产品和 API。更新 API 产品可通过不同方式执行。  

- 将旧项替换为新项 - 自动更新所有预订
- 使用新项取代旧项 - 手动更新每个应用程序的预订

替换 API 后，可以通过执行以下步骤使 API 产品停止运行并将其除去：

- **弃用 API 产品**。这将阻止对 API 的任何新预订，但不会禁止其使用。
- **引退 API 产品**。这将阻止对 API 的任何使用，但不会将其除去。
- **归档 API 产品**。这将停止使用该 API，但不会将其完全删除；可以对其进行恢复。
- **删除 API 产品**。API 产品会彻底消失，无法检索到。

在此系列教程中，您将使 API 产品依次经历所有这些状态。请按以下顺序完成教程：

1. [替换 API 产品](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_replace)
2. [取代 API 产品](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_supercede)
3. [归档和删除 API 产品](/docs/services/apiconnect/tutorials?topic=apiconnect-tut_manage_remove)













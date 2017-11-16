---
copyright:
  years: 2017
lastupdated: "2017-09-19"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 安裝 API Connect Toolkit
**持續時間**：15 分鐘  
**技能水準**：初學者  

## 需要的項目
1. Node.js
2. Node 產品管理程式 (NPM)
3. {{site.data.keyword.apiconnect_short}} _精簡_

<table>
  <tr><td><b>Node.js</b>：用來建置及執行可擴充網路應用程式的非同步事件驅動 JavaScript 運行環境
    <br>
    <b>Node 產品管理程式</b>：JavaScript 套件管理程式及軟體登錄<br>
    <b>{{site.data.keyword.apiconnect_short}} _精簡_</b>：裝載於筆記型電腦上的免費 {{site.data.keyword.apiconnect_short}} 版本</td></tr>
  </table>  


## 安裝 node.js
1. 從以下兩個來源的其中一個下載及安裝 node.js：
   * [https://nodejs.org/en/download/ ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://nodejs.org/en/download/){:new_window}（附註：下載平台適用的 LTS 版本，而不是最新版本，否則可能會發生錯誤）。
      **或**
   * [https://developer.ibm.com/node/sdk/v6/ ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _安裝 node.js 時也會安裝 **npm**（Node 套件管理程式）_。

2.  下載並安裝 Node.js 之後，請確認它位在 _PATH_ 中。
    ![](images/verify-path.png)  

3. 更新 **npm**。在指令行中，輸入 `npm install -g npm`。  
   **附註：**設定 npm `--engine-strict` 或 `npm config set engine-strict true` 會防止完成安裝。


4. 檢查已安裝的版本及路徑。
   ![](images/screenshot_install_apic-1.png)  



## 安裝 API Connect Toolkit 及 Micro Gateway
1. 更新 npm config，以容許使用未受信任的憑證。  
   `npm config -g set strict-ssl false`  

2. 從 **npm** 中，安裝 {{site.data.keyword.apiconnect_short}} Toolkit。  
    `npm install -g apiconnect`

3. 檢查已安裝的版本。  
    `apic -v`

4. 在指令行上輸入下列指令：`npm install -g microgateway`。

我們將使用 Micro Gateway 作為本端測試伺服器。

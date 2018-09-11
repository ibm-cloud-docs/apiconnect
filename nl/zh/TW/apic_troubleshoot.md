---
copyright:
  years: 2017
lastupdated: "2017-12-15"
---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 疑難排解
{: #troubleshoot}

以下是有關在 {{site.data.keyword.Bluemix_notm}} 上使用 {{site.data.keyword.apiconnect_long}} 的常見疑難排解問題的答案。
{:shortdesc}

## 新增 API Connect {{site.data.keyword.Bluemix_notm}} 服務時所需的使用者名稱及密碼

將服務新增至「{{site.data.keyword.Bluemix_notm}} 儀表板」之後，當您嘗試開啟它時，系統會提示您輸入使用者名稱和密碼。 

### 症狀
{: #ts_sym_usernamepw}

當您開啟新的 {{site.data.keyword.apiconnect_short}} 時，需要登入 API Manager，而不是直接存取 {{site.data.keyword.Bluemix_notm}} 服務。

### 原因
{: #ts_cause_usernamepw}

您的瀏覽器已設為封鎖 Cookie，或層次已設為比 {{site.data.keyword.apiconnect_notm}} 所需更受限制的層次。

### 解決方法
{: #ts_res_usernamepw}

啟用或增加瀏覽器設定中 Cookie 的許可權層次，直到它開啟 {{site.data.keyword.Bluemix_notm}} 服務為止。

## 無法安裝 Developer Toolkit

佈建 API Connect 服務之後，嘗試安裝 Developer Toolkit，但安裝失敗。

### 症狀
{: #ts_sym_noinstalltk}

Developer Toolkit 安裝期間顯示下列錯誤：
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### 原因
{: #ts_cause_noinstalltk}

您沒有必要的權限，無法建立檔案或目錄。

### 解決方法
{: #ts_res_noinstalltk}

請變更指定目錄的權限，或使用
`sudo` 執行指令。在本端開發系統上，最好將目錄權限固定如下：

```
sudo chown -R $USER /usr/local
```
{:codeblock}

這個指令會讓您的使用者帳戶成為 `/usr/local` 目錄的擁有者。如此，您便不需要使用 sudo 安裝 Node，使用 npm 廣域地安裝套件。 
    **附註：**變更目錄所有權只適用於本端開發系統。請絕對不要在伺服器系統上這麼做。

此外，請不要對 `/usr/bin` 目錄使用前述的
`chown` 指令；這麼做可能會導致您的系統嚴重地配置錯誤。


如果您必須使用 `sudo`，請使用下列指令：
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## 無法在 Windows 上安裝 Developer Toolkit

佈建 {{site.data.keyword.apiconnect_short}} 服務之後，嘗試安裝 Developer Toolkit，但安裝失敗。

### 症狀
{: #ts_sym_noinstalltk_path}

您嘗試在 Windows 上安裝 Developer Toolkit，並且收到一則錯誤訊息，指出*路徑應該小於 248 個字元*。

### 原因
{: #ts_cause_noinstalltk_path}

Windows 系統上有路徑長度上限，當您嘗試在深層資料夾中安裝所有相依關係時超出此限制。

### 解決方法
{: #ts_res_noinstalltk_path}

您可以使用下列其中一種方式來修正此問題：

- 確定您已安裝正確的 Node.js 版本。如需相關資訊，請參閱[安裝 Developer Toolkit](creating_apis.html)。

- 如果您必須升級程式，請嘗試重新安裝。

如果這行不通，請將 {{site.data.keyword.apiconnect_short}} 安裝在比 `C:/program files/nodejs/bin/node_modules...` 這類資料夾高的層次上。如果您安裝於最上層目錄，則不會看到此錯誤。

## 無法在 Mac OS X 上安裝 Developer Toolkit

佈建 {{site.data.keyword.apiconnect_short}} 服務之後，嘗試安裝 Developer Toolkit，但安裝失敗。

### 症狀
{: #ts_sym_noinstalltk_mac}

Developer Toolkit 安裝期間顯示下列錯誤：
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### 原因
{: #ts_cause_noinstalltk_mac}

您最近升級或安裝了 Xcode，且尚未同意授權。

### 解決方法
{: #ts_res_noinstalltk_mac}

1. 輸入下列指令，以驗證 Xcode 授權：
```
sudo xcode-select
```
{:codeblock}

2. 重新安裝 Developer Toolkit。


## 無法在 Ubuntu 上安裝 Developer Toolkit

佈建 {{site.data.keyword.apiconnect_short}} 服務之後，嘗試安裝 Developer Toolkit，但安裝失敗。

### 症狀
{: #ts_sym_noinstalltk_ubu}

Developer Toolkit 安裝期間顯示下列錯誤：
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3 
node-pre-gyp install --fallback-to-build 
/usr/bin/env: node: No such file or directory 
npm WARN This failure might be due to the use of legacy binary "node" 
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian 
npm ERR! weird error 127 
npm ERR! not ok code 0
```

### 解決方法
{: #ts_res_noinstalltk_ubu}

請輸入下列指令以解決問題：
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## 無法針對 npm 安裝失敗進行除錯

當您遵循步驟安裝 Developer Toolkit 時，npm 安裝會失敗。

### 症狀
{: #ts_sym_npmfail}

npm 安裝失敗，而未提供任何有用的資訊以進行除錯。

### 解決方法
{: #ts_res_npmfail}

當安裝失敗時，npm 會在 `npm-debug.log</filepath>` 檔案中寫入一行，顯示錯誤所在位置。使用 `npm-debug.log` 檔案來判斷原因。

## 無法開啟 API Designer

您輸入指令 `apic edit`，但 API Designer 並未開啟。

### 症狀
{: #ts_sym_noopenapid}

輸入下列指令之後，無法開啟 API Designer 實例：
```
apic edit
```
並且顯示下列訊息：
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### 原因
{: #ts_cause_noopenapid}

您已從另一個指令視窗啟動 API Designer 實例。

### 解決方法
{: #ts_res_noopenapid}

若要修正此問題，您需要關閉其他指令視窗（如下列步驟所述）：

1. 在其他指令視窗中，按 **Ctrl+C**。

2. 顯示下列訊息。
```
Terminate Batch job (Y/N)?
```

3. 鍵入 `Y`，然後按 Enter 鍵。

## 無法配置產品的計費資訊

部分計費資訊無法用來配置或確定到正式作業環境。 

### 症狀
{: #ts_sym_nobill}

  - 當您查看「產品」的「管理」區段時，未顯示「計費」標籤。
  - 當您嘗試在指定計費資訊的情況下發佈「產品」時，收到錯誤。 

### 原因
{: #ts_cause_nobill}

您必須具有正確的 {{site.data.keyword.apiconnect_short}} 帳戶及許可權，才能啟用計費資訊。

## 無法訂閱具有「產品」的計費「方案」

「分段」限制每一個客戶最多只能有 25 個訂閱。請確定您未超出此限制。如果超出，則只能在移除另一個訂閱後才能新增此訂閱。

### 症狀
{: #ts_sym_nosubscribe}

雖然您已配置其他「方案」，但是當您嘗試訂閱具有計費的「方案」時，會看到錯誤。

### 原因
{: #ts_cause_nosubscribe}

「分段」信用卡處理服務容許每個帳戶最多有 25 個訂閱。

### 解決方法
{: #ts_res_nosubscribe}

請確定您有 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} 服務的「企業」層次帳戶，而且實例少於 25 個。如果您有最大服務數目，請移除服務。

## 取得 API Connect 的協助及支援

如果您在使用 {{site.data.keyword.apiconnect_short}} 時有問題或疑問，可以透過搜尋資訊或透過討論區提出問題來取得協助。您也可以開立支援問題單。

使用討論區提出問題時，請標記您的問題，讓 {{site.data.keyword.Bluemix_notm}} 開發團隊可以看到它。 

- 如果您有關於使用 {{site.data.keyword.apiconnect_short}} 開發或部署應用程式的技術問題，請將問題張貼到 Stack Overflow，並使用 "ibm-cloud" 和 "api connect" 來標記問題。

- 若為關於服務及開始使用指示的問題，請使用 IBM DeveloperWorks dW Answers 討論區。請包含 "ibm cloud" 和 "api connect" 標籤。如需使用討論區的詳細資料，請參閱「取得協助」。 

如需開立 IBM 支援問題單的相關資訊，或支援層次與問題單嚴重性的相關資訊，請參閱「與支援中心聯絡」。




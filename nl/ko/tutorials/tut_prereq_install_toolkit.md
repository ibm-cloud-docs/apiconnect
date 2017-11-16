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

# API Connect 툴킷 설치
**기간**: 15분  
**스킬 레벨**: 초보자  

## 필요한 항목
1. Node.js
2. NPM(Node Product Manager)
3. {{site.data.keyword.apiconnect_short}} _Lite_

<table>
  <tr><td><b>Node.js</b>: 확장 가능 네트워크 애플리케이션을 빌드하고 실행하는 데 사용한 비동기 이벤트 중심 JavaScript 런타임
    <br>
    <b>노드 제품 관리자</b>: JavaScript 패키지 관리자 및 소프트웨어 레지스트리<br>
    <b>{{site.data.keyword.apiconnect_short}} _Lite_</b>: 랩탑에서 호스팅되는 무료 버전의 {{site.data.keyword.apiconnect_short}}</td></tr>
  </table>  


## node.js 설치
1. 다음 두 소스 중 하나에서 node.js를 다운로드하여 설치하십시오.
   * [https://nodejs.org/en/download/ ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://nodejs.org/en/download/){:new_window}(참고: 최신 버전이 아니라 플랫폼의 LTS 버전을 다운로드하십시오. 그렇지 않으면 오류가 발생할 수 있습니다.)
      **또는**
   * [https://developer.ibm.com/node/sdk/v6/ ![외부 링크 아이콘](../../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/node/sdk/v6/){:new_window}  

    _node.js를 설치하면 **npm**(Node Package Manager)도 설치됩니다_.

2.  Node.js를 다운로드하여 설치하고 난 후 _PATH_에 있는지 확인하십시오.
    ![](images/verify-path.png)  

3. **npm**을 업데이트하십시오. 명령행에서 `npm install -g npm`을 입력하십시오.  
   **참고:** npm `--engine-strict` 또는 `npm config set engine-strict true`를 설정하면 설치가 완료되지 않습니다.


4. 설치된 버전과 경로를 확인하십시오.
   ![](images/screenshot_install_apic-1.png)  



## API Connect 툴킷 및 Microgateway 설치
1. 신뢰되지 않는 인증서를 사용할 수 있도록 npm 구성을 업데이트하십시오.  
   `npm config -g set strict-ssl false`  

2. **npm**에서 {{site.data.keyword.apiconnect_short}} 툴킷을 설치하십시오.  
    `npm install -g apiconnect`

3. 설치된 버전을 확인하십시오.  
    `apic -v`

4. 명령행에서 다음 명령을 입력하십시오. `npm install -g microgateway`.

Microgateway를 로컬 테스트 서버로 사용합니다.

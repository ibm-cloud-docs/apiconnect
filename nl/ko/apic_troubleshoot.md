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

# 문제점 해결
{: #troubleshoot}

{{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.apiconnect_long}} 사용과 관련된 공통 문제점 해결 질문에 대한 답변입니다.
{:shortdesc}

## API Connect {{site.data.keyword.Bluemix_notm}} 서비스를 추가할 때 필요한 사용자 이름과 비밀번호

{{site.data.keyword.Bluemix_notm}} 대시보드에 서비스를 추가한 후 열려고 하면 사용자 이름과 비밀번호를 입력하도록 프롬프트가 표시됩니다. 

### 증상
{: #ts_sym_usernamepw}

{{site.data.keyword.apiconnect_short}}를 열 때 {{site.data.keyword.Bluemix_notm}} 서비스에 직접 액세스하는 것이 아니라 API Manager에 로그인해야 합니다.

### 원인
{: #ts_cause_usernamepw}

브라우저에서 쿠키를 차단하도록 설정되어 있거나 레벨이 {{site.data.keyword.apiconnect_notm}}에 필요한 것보다 더 제한된 레벨로 설정되어 있습니다.

### 해결
{: #ts_res_usernamepw}

{{site.data.keyword.Bluemix_notm}} 서비스를 열 때까지 브라우저 설정에서 쿠키를 사용하거나 쿠키의 권한 레벨을 늘리십시오.

## 개발자 툴킷을 설치할 수 없음

API Connect 서비스를 프로비저닝한 후 개발자 툴킷의 설치를 시도하지만
설치에 실패합니다.

### 증상
{: #ts_sym_noinstalltk}

개발자 툴킷 설치 동안 다음 오류가
표시됩니다.
```
npm ERR! Error: EACCES, mkdir '/usr/local/lib/node_modules/apiconnect'
...
npm ERR! Please try running this command again as root/Administrator
...
```

### 원인
{: #ts_cause_noinstalltk}

사용자에게 파일 또는 디렉토리를 작성할 수 있는 필수 권한이 없습니다.

### 해결
{: #ts_res_noinstalltk}

지정된 디렉토리에 대한 권한을 변경하거나 `sudo`를 사용하여
명령을 실행하십시오. 로컬 개발 시스템에서는 다음과 같이 디렉토리 권한을 수정하는 것이
좋습니다.
```
sudo chown -R $USER /usr/local
```
{:codeblock}

이 명령은 사용자 계정이 `/usr/local` 디렉토리의 소유자가 되게 합니다. 그 다음에는 npm으로 패키지를 글로벌로 설치하거나
노드를 설치하기 위해 sudo를 사용할 필요가 없습니다. 
    **참고:** 디렉토리 소유권 변경은 로컬 개발 시스템에만 해당합니다. 서버 시스템에서는 수행하지 마십시오.

또한 이전의 `chown` 명령을
`/usr/bin` 디렉토리에 사용하지 마십시오.
명령을 실행하면 시스템을 심각하게 잘못 구성할 수 있습니다.

`sudo`를 사용해야 하는 경우
다음 명령을 사용하십시오.
```
sudo npm install -g --unsafe-perm install apiconnect
```
{:codeblock}

## Windows에 개발자 툴킷을 설치할 수 없음

{{site.data.keyword.apiconnect_short}}
서비스를 프로비저닝한 이후 개발자 툴킷의 설치를 시도하지만 설치에 실패합니다.

### 증상
{: #ts_sym_noinstalltk_path}

Windows에서 개발자 툴킷의 설치를 시도 중이며 *경로는 248자 미만이어야 함*으로 기술된 오류 메시지를 수신합니다.

### 원인
{: #ts_cause_noinstalltk_path}

Windows 시스템에는 최대 경로 길이가 있으며, 딥 레벨 폴더에서
모든 종속 항목의 설치를 시도하면 이 길이를 초과하게 됩니다.

### 해결
{: #ts_res_noinstalltk_path}

다음 방법 중 하나로 이 문제점을 해결할 수 있습니다.

- 올바른 버전의 Node.js를 설치했는지 확인하십시오. 자세한 정보는 [개발자 툴킷 설치](creating_apis.html)를 참조하십시오.

- 프로그램을 업그레이드해야 하는 경우에는 설치를 다시 시도하십시오.

그래도 문제가 해결되지 않으면 `C:/program files/nodejs/bin/node_modules...` 폴더보다
높은 레벨에서 {{site.data.keyword.apiconnect_short}}를 설치하십시오. 
최상위 레벨 디렉토리에서 설치하면 이 오류가 나타나지 않습니다.

## Mac OS X에 개발자 툴킷을 설치할 수 없음

{{site.data.keyword.apiconnect_short}}
서비스를 프로비저닝한 이후 개발자 툴킷의 설치를 시도하지만 설치에 실패합니다.

### 증상
{: #ts_sym_noinstalltk_mac}

개발자 툴킷 설치 동안 다음 오류가
표시됩니다.
```
Agreeing to the Xcode/iOS license requires admin 
privileges, please re-run as root via sudo
```

### 원인
{: #ts_cause_noinstalltk_mac}

사용자는 최근에 Xcode를 업그레이드하거나 설치했으며 아직 라이센스에 동의하지
않았습니다.

### 해결
{: #ts_res_noinstalltk_mac}

1. 다음 명령을 입력하여 Xcode 라이센스의 유효성을 검증하십시오.
```
sudo xcode-select
```
{:codeblock}

2. 개발자 툴킷을 다시 설치하십시오.


## Ubuntu에 개발자 툴킷을 설치할 수 없음

{{site.data.keyword.apiconnect_short}}
서비스를 프로비저닝한 이후 개발자 툴킷의 설치를 시도하지만 설치에 실패합니다.

### 증상
{: #ts_sym_noinstalltk_ubu}

개발자 툴킷 설치 동안 다음 오류가
표시됩니다.
```
sqlite3@3.1.1 install /usr/local/lib/node_modules/strong-pm/node_modules/minkelite/node_modules/sqlite3
node-pre-gyp install --fallback-to-build
/usr/bin/env: node: No such file or directory
npm WARN This failure might be due to the use of legacy binary "node"
npm WARN For further explanations, please read /usr/share/doc/nodejs/README.Debian
npm ERR! weird error 127
npm ERR! not ok code 0
```

### 해결
{: #ts_res_noinstalltk_ubu}

다음 명령을 입력하여 문제점을
해결하십시오.
```
$ update-alternatives --install /usr/bin/node node /usr/bin/nodejs 99
```

## npm 설치 실패를 디버그할 수 없음

개발자 툴킷을 설치하기 위해 다음 단계를 따르면 npm 설치가
실패합니다.

### 증상
{: #ts_sym_npmfail}

npm 설치가 디버그를 위한 유용한 정보를 제공하지 않고
실패합니다.

### 해결
{: #ts_res_npmfail}

설치가 실패하면 npm이 `npm-debug.log</filepath>` 파일에 행을 작성하여
오류가 있는 위치를 보여줍니다. `npm-debug.log` 파일을 사용하여
원인을 판별하십시오.

## API Designer를 열 수 없음

`apic edit` 명령을 입력해도 API Designer가
열리지 않습니다.

### 증상
{: #ts_sym_noopenapid}

명령을 입력한 후에 API Designer의 인스턴스를 열 수 없습니다.
```
apic edit
```
and the following message is displayed:
```
<time stamp>. 329Z ERROR apiConnect: listen EADDRINUSE <ip address> :9000
```

### 원인
{: #ts_cause_noopenapid}

다른 명령 창에서 사용자가 이미 API Designer의 인스턴스를
시작했습니다.

### 해결
{: #ts_res_noopenapid}

이 문제점을 해결하려면 다음 단계에서 설명한 대로 다른 명령 창을
닫아야 합니다.

1. 다른 명령 창에서 **Ctrl + C**를 누르십시오.

2. 다음 메시지가 표시됩니다.
```
Terminate Batch job (Y/N)?
```

3. `Y`를 입력하고 Enter를 누르십시오.

## 제품의 비용 청구 정보를 구성할 수 없음

일부 비용 청구 정보는 구성하거나 프로덕션을 커미트할 수 없습니다. 

### 증상
{: #ts_sym_nobill}

  - 제품의 관리 섹션에 비용 청구 탭이 표시되지 않습니다.
  - 비용 청구 정보가 지정된 제품을 공개하려고 하면 오류가 표시됩니다. 

### 원인
{: #ts_cause_nobill}

비용 청구 정보를 사용하려면 올바른 {{site.data.keyword.apiconnect_short}} 계정과 권한이 있어야 합니다.

## 제품으로 비용 청구 플랜에 등록할 수 없음

스트라이프는 각 고객을 최대 25개의 등록으로 제한합니다. 이 한계를 초과하지
않도록 하십시오. 초과하는 경우 다른 등록을 제거해야만 이 등록을 추가할 수 있습니다.

### 증상
{: #ts_sym_nosubscribe}

다른 플랜이 구성되어 있는 상태에서 비용 청구가 있는 플랜에 등록하려고 하면 오류가 표시됩니다.

### 원인
{: #ts_cause_nosubscribe}

스트라이프 신용카드 처리 서비스를 사용하면 계정당 최대 25개의 등록이 가능합니다.

### 해결
{: #ts_res_nosubscribe}

{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.apiconnect_short}} 서비스의 엔터프라이즈 레벨 계정이 있으며 인스턴스가 25개 미만인지 확인하십시오. 최대수의 서비스가 있으면 서비스를 제거하십시오.

## API Connect에 대한 도움말 및 지원

{{site.data.keyword.apiconnect_short}} 사용과 관련된 문제점 또는 질문이 있는 경우, 정보를 검색하거나 포럼에 질문하여 도움을 받을 수 있습니다. 또한 지원 티켓을 열 수도 있습니다.

포럼을 통해 질문하는 경우 {{site.data.keyword.Bluemix_notm}} 개발 팀이 확인할 수 있도록 질문에 태그를 지정하십시오. 

- {{site.data.keyword.apiconnect_short}}로 앱을 개발하거나 배치하는 데 대한 기술 질문이 있으면 스택 오버플로우에 대한 질문을 게시하고 질문을 "ibm-cloud" 및 "api connect"로 태그 지정하십시오.

- 서비스 및 시작하기 지시사항에 대한 질문은 IBM DeveloperWorks dW Answers 포럼을 사용하십시오. "ibm cloud" 및 "api connect" 태그를 포함하십시오.
포럼 사용에 대한 세부사항은 도움 받기를 참조하십시오. 

IBM 지원 티켓 열기 또는 지원 레벨과 티켓 심각도에 대한 정보는 지원 문의를 참조하십시오.




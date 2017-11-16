---

copyright:
  years: 2017
lastupdated: "2017-09-26"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 작성
{: #creating_apis}

개발자 툴킷을 다운로드하고 명령행 인터페이스(CLI) 또는 API Designer를 사용하여
API를 작성할 수 있습니다. 

## 개발자 툴킷 CLI
{: #dev_tk_cli notoc}

개발자 툴킷은 {{site.data.keyword.apiconnect_long}}에
API를 공개하기 위해 사용할 수 있는 명령행 인터페이스를 제공합니다.
사용자는 제품에 API를 포함한 후에 이 제품을 공개하여 해당 API를 공개합니다. 
사용자는 로컬 파일 시스템에서 YAML 정의 파일을 작성하고 이의 유효성을 검증하여
API 및 제품을 정의합니다. 그리고 툴킷 명령을 사용하여
{{site.data.keyword.apiconnect_long}}와 상호작용할 수 있습니다. 

## API Designer
{: #designer notoc}

API Designer는 개발자 툴킷 내의 오프라인 그래픽 사용자 인터페이스이며,
API를 작성하고 구성하는 기능을 제공합니다.
API Designer는 명령행 인터페이스에서 편집 명령을 사용하여 실행됩니다. 편집 명령을 사용하면
API Designer가 기본 브라우저에서 열립니다. 또는 명령을 실행할 때 표시되는 로컬 호스트 포트를 통해
이에 액세스할 수 있습니다. 

## 개발자 툴킷 설치
{: #install_dev_tk}

### 전제조건
{: #prereq_install_dev_tk}

시작하기 전에 툴킷을 사용할 시스템에 [Node.js ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://nodejs.org/en/){:new_window}를
설치하고 `node`가 `PATH`에 있는지 확인하십시오.

개발자 툴킷을 설치하면 다음 항목이 설치됩니다. 

- {{site.data.keyword.apiconnect_short}} 명령행 도구
- {{site.data.keyword.apiconnect_short}} 그래픽 편집기
- 로컬 {{site.data.keyword.apiconnect_short}} 마이크로 게이트웨이


1. 툴킷을 설치하려면 관리자로 명령 프롬프트를 열고 다음 명령을
입력하십시오. 

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **참고:** 설치 중에 `node-gyp` 모듈에서 오류가 발생할 수 있습니다. 
이 오류는 선택적 종속 항목에서 발생하는 오류이며, 설치는 정상적으로 완료됩니다. 

2. 모든 툴킷 명령의 요약 사용법 도움말을 보려면 다음 명령을 입력하십시오. 

    ```
    apic
    ```
	{: codeblock}

3. 명령의 사용법 도움말을 보려면 `--help` 옵션을 사용하십시오.
예: 

    ```
    apic validate --help
    ```
	{: codeblock}
	
## LoopBack 커넥터 설치
{: #install_lb_conn}

LoopBack 데이터 소스를 사용하여 백엔드 시스템의 데이터(예: 데이터베이스)에 액세스하려면,
우선 데이터 소스 커넥터를 설치해야 합니다. 인메모리 및 이메일 커넥터는 LoopBack에서 기본 제공되므로
설치하지 않아도 됩니다. 

### 전제조건
{: #prereq_install_lb_conn}

Oracle, DB2 및 SQLLite 커넥터는 C 컴파일러가 있어야 2진 확장기능을
빌드하고 설치할 수 있습니다. 정확한 요구사항은 다음 표에서 설명하는 대로
운영 체제마다 다릅니다. 

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>표 1. 운영 체제별 설치 요구사항</caption>
<thead>
<tr>
<th style="width: 33.3%" id="th_d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="th_d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="th_d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" > [Microsoft .NET Framework 4 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.microsoft.com/en-us/download/details.aspx?id=17851) <a href="https://www.microsoft.com/en-us/download/details.aspx?id=17851" rel="external" target="blank" title="(새 탭 또는 창에 열림)" >Microsoft .NET Framework 4</a></td>
<td style="width: 33.3%">Python v2.7(v3.x는 지원되지 않음)</td>
<td style="width: 33.3%" > [Python Releases for Mac OS X ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.python.org/downloads/mac-osx/) <a href="https://www.python.org/downloads/mac-osx/" rel="external" target="blank" title="(새 탭 또는 창에 열림)" >Python
Releases for Mac OS X</a></td>
</tr>
<tr><td style="width: 33.3%" > [Visual Studio ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.visualstudio.com/downloads/download-visual-studio-vs) <a href="https://www.visualstudio.com/downloads/download-visual-studio-vs" rel="external" target="blank" title="(새 탭 또는 창에 열림)" >Visual Studio</a></td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" > [Xcode ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716) <a href="https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716" rel="external" target="blank" title="(새 탭 또는 창에 열림)" >Xcode</a></td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" > [Python v2.7.10 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.python.org/downloads/release/python-2710/) <a href="https://www.python.org/downloads/release/python-2710/" rel="external" target="blank" title="(새 탭 또는 창에 열림)" >Python v2.7.10</a></td>
<td style="width: 33.3%">C/C++ 컴파일러 도구 체인(예: GCC 버전 4.2 이상). </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" > [Microsoft Windows SDK for Windows 7 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.microsoft.com/en-gb/download/details.aspx?id=8279) <a href="https://www.microsoft.com/en-gb/download/details.aspx?id=8279" rel="external" target="blank" title="(새 탭 또는 창에 열림)">Microsoft Windows SDK for Windows 7</a></td>
<td style="width: 33.3%">Debian 및 Debian에서 파생된 배포(Ubuntu, Mint 등)에서는 다음 명령을 사용하십시오.
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm 버전 3. 다음 참고 사항을 참조하십시오.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**참고:** Windows 설치의 경우:

- Visual Studio Enterprise를 구매하고자 하는 경우가 아니라면 Visual Studio Community를 사용하십시오. 설치 프로그램을
실행하고 "Programming Languages" 아래의 "Visual C++"를 선택한 후에 기본 설치 위치를
승인하십시오. 

- Node.js 및 원시 모듈의 64비트 빌드인 경우에는 Windows&trade; 7 64비트 SDK도 필요합니다. 
설치에 실패한 경우에는 우선 설치된 C++ 2010 x64&amp;x86 Redistributable을 설치 제거해 보십시오. 64비트 컴파일러가 설치되지 않았다는 오류가 발생하면,
Windows&trade; SDK 7.1에 대한 컴파일러 업데이트가 필요할 수도 있습니다. 
- 다음 명령을 입력하여 npm 버전 3을 설치하십시오. 
  ```
  npm install -g npm
  ```
  {: codeblock}
  그리고 npm 명령이 올바른 버전을 사용하는지 확인하십시오.
  ```
  npm -v
  ```
  {: codeblock}
  표시된 버전이 3.x.x가 아닌 경우에는 시스템 PATH를 편집하여 `C:\Users\username\AppData\Roaming\npm` 이 기타 항목을 대체하도록 하십시오.


1. **선택사항**:
API Designer를 사용 중이면 새 쉘 창을 여십시오. 

2. 운영 체제에 필요한 컴파일러 도구가 설치되어 있으면 프로젝트 루트 디렉토리에
다음 명령을 사용하여 커넥터를 설치하십시오. 

```
npm install --save <connector-package>
```
{: codeblock}
여기서, `<connector-package>`은(는) 표에 표시된 대로 LoopBack 커넥터에 대한 npm 패키지의 이름입니다.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>표 3. LoopBack 커넥터</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="th_new_d70e1489" class="thleft style-scope doc-content">데이터 소스</th>
<th style="width: 50%" id="th_new_d70e1491" class="thleft style-scope doc-content">커넥터 패키지</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP 웹 서비스</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST 웹 서비스</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## CLI를 사용하여 LoopBack API 작성
{: #create_lb_api}

다음 프로시저는 명령 인터페이스를 사용하여 LoopBack&reg; API를 작성하는 방법을 설명합니다. 


### 전제조건
{: #prereq_create_lb_api}

시작하기 전에, 바로 사용하고자 하는
카탈로그의 카탈로그 ID를 가져오십시오.
카탈로그 ID를 가져오려면 다음 단계를 완료하십시오.   

1. {{site.data.keyword.apiconnect_short}} **대시보드**로 이동하십시오. 

2. 사용할 카탈로그에 대해 **카탈로그 ID 표시**
아이콘 <img alt="카탈로그 ID를 표시하기 위한 체인 링크 아이콘" src="images/chain_link_icon.png">을 클릭하십시오. 

3. 카탈로그 ID를 복사하십시오. 예:   
  ```
  apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
  ```
  {: codeblock}
    여기서,

    - `<region>`은(는) {{site.data.keyword.Bluemix_short}} 지역입니다.

    - `<username_string>`은(는) 기호가 없는 {{site.data.keyword.Bluemix_short}} 조직 ID입니다. 예를 들어,
    `joe@mycompany.com`은 `joemycompanycom`입니다.

    - `<catalog>`은(는) 카탈로그의 이름입니다.  

CLI를 사용하여 LoopBack API를 작성하려면 다음 단계를 완료하십시오.

1. 프로젝트를 작성하려면 명령행을 열고 다음을 입력하십시오. 
  ```
  apic loopback
  ```
  {: codeblock}

2. 다음에 표시되는 프롬프트에서, 사용자는 애플리케이션 이름을 지정하도록 요청을 받습니다. 이름을 입력한 후
**Enter**를 누르십시오.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    도구에서 프로젝트가 작성될 디렉토리의 이름을 입력하도록 프롬프트를
    표시합니다.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. **Enter**를 눌러서 이전에 입력한 이름을 사용하거나 새 이름을 입력한 후에 **Enter**를 누르십시오. 도구에서 작성할 애플리케이션의 유형을 선택하도록 프롬프트를
표시합니다. 
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 사용할 애플리케이션을 선택하고 **Enter**를 누르십시오.
이 도구는 프로젝트 디렉토리를 작성한 다음 여러 디렉토리와 파일을 추가하면서
여러 메시지를 표시합니다. 또한 `package.json`에 지정된 대로
`npm install`을 실행하여 모든 프로젝트 종속 항목을 설치합니다.
이 프로세스는 다소 시간이 걸릴 수 있습니다. 

5. 모델을 작성하기 전에 현재 작업 디렉토리가 프로젝트 최상위 레벨
디렉토리인지 확인해야 합니다. 이를 수행하려면 다음 명령을 입력하십시오. 
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. 모델을 작성하려면 다음 명령을 입력하십시오. 
    ```
    apic create --type model
    ```
    {: codeblock}

    도구에서 모델의 이름을 입력하도록 프롬프트를 표시합니다.

    ```
    ? Enter the model name:
    ```

7. Enter a name for the model.
    일반적으로, 모델 이름에는 영숫자 문자, 대시 및 밑줄을 사용할 수
    있습니다.
    프로젝트에 추가한 모든 데이터 소스가 나열되며,
    도구에서 사용할 데이터 소스를 선택하도록
    프롬프트를 표시합니다.
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. 사용할 데이터 소스를 선택하고 **Enter**를 누르십시오. 도구에서 모델의 기본 클래스를 선택하도록 프롬프트를
표시합니다.
    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
    각 옵션에 대한 자세한 정보는 [기본 제공 모델 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://loopback.io/doc/en/lb3/Using-built-in-models.html){:new_window}을 참조하십시오.

9. 기본 클래스를 선택하고 **Enter**를 누르십시오. 도구에서 모델의 REST API를 노출하고자 하는지
묻습니다.
```
? Expose branch via the REST API? (Y/n)
```
모델이 REST로 노출되면
모든 표준 작성, 읽기, 업데이트 및 삭제 오퍼레이션을 REST 엔드포인트를 통해
사용할 수 있습니다.

10. 선택사항을 입력하고 **Enter**를 누르십시오. REST에서 모델을 노출하도록 선택한 경우 도구에서
모델 이름의 복수 양식에 대한 프롬프트를 표시합니다.

```
? Custom plural form (used to build REST URL):
```

11. **Enter**를 눌러 복수화에 대해 기본 표준 영어 규칙을
사용하십시오.
서버 전용 모델을 작성할지 아니면 서버 또는 클라이언트 LoopBack&reg; API 모두에서
사용 가능한 공통 모델을 작성할지 여부를 묻는 프롬프트를 도구에서
표시합니다.
```
? Common model or server only? (Use arrow keys)
```

12. 화살표 키를 사용하여 선택하고 **Enter**를 누르십시오.
도구에서 모델에 특성을 추가하도록 프롬프트를 표시합니다.
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. 특성 이름을 입력하십시오.
도구에서 특성의 데이터 유형을 선택하도록 프롬프트를
표시합니다.
```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. string 유형을 선택하고 **Enter**를 누르십시오.
도구에서 해당 특성이 필요한지 여부를
묻습니다.
```
? Required? (y/N)
```

15. `y` 또는 `n`을 입력하고
**Enter**를 누르십시오.
도구에서 다른 특성을 추가하도록 프롬프트를
표시합니다.
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. 필요하면 다른 특성 이름을 추가하십시오. 추가로 특성이 필요하지 않으면
**Enter**를 눌러서 모델 추가를 완료하십시오. 

기본적으로, LoopBack&reg; 프로젝트는 개발 및 테스트 용도에 알맞게 인메모리 데이터 소스로 구성되어 제공됩니다. 하지만 언젠가 사용자는 자신의 모델을 실제 모델(예: 데이터베이스 서버)에 연결하고자 할 수 있습니다. 데이터 소스를 추가하려면 다음 단계를 완료하십시오. 

1. 다음 명령을 입력하십시오.
```
apic create --type datasource
```
{: codeblock}
도구에서 데이터 소스의 이름을 입력하도록 프롬프트를 표시합니다.
```
? Enter the data-source name:
```

2. 데이터 소스의 이름을 입력하십시오. 데이터 소스 이름에는 영숫자 문자, 대시 및 밑줄을
사용할 수 있습니다. 도구에서 데이터 소스에 사용할 커넥터를 선택하도록 프롬프트를 표시합니다. 
```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. 화살표 키를 사용하여 사용할 커넥터를 선택한 후에 **Enter**를
누르십시오.
그러면 도구에서 데이터 소스를 프로젝트에 추가합니다. 

4. 호스트, 포트, 사용자, 비밀번호 및 데이터베이스 신임 정보를 입력하십시오.
도구에서 LoopBack&reg; 커넥터를 설치하도록 프롬프트를 표시합니다.
```
Install loopback-connector-<connector>?
```

5. `Yes`를 입력하십시오.
도구에서 커넥터를 설치합니다. 

참고: Oracle 커넥터를 선택한 경우에는 Oracle 앱이 시작할 수 있도록
{{site.data.keyword.Bluemix_short}}에서 환경 변수를 설정해야 합니다. 
이를 수행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.Bluemix_short}} UI에서
**컴퓨팅**을 클릭하십시오. 

2. CF 애플리케이션에서 작업할 애플리케이션을 선택하십시오. 

3. **런타임**을 클릭하십시오. 

4. **환경 변수**를 선택하십시오. 

5. 사용자 정의 섹션에서 **추가**를 클릭하십시오. 

6. **이름** 필드에서 `LD_LIBRARY_PATH`를 입력하십시오. 

7. **값** 필드에서
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`를 입력하십시오. 

8. **저장**을 클릭하십시오. 

### LoopBack 프로젝트 테스트
{: #test_lb_proj}

LoopBack&reg; 프로젝트를 테스트하려면 다음 단계를 완료하십시오.

1. **선택사항**: 현재 작업 디렉토리가 프로젝트 최상위 레벨 디렉토리인지 확인하십시오. 다음 명령을
입력하십시오.
```
cd <loopback-project-dir>
```
여기서, `<loopback-project-dir>`은(는) 프로젝트를 포함하는 디렉토리의 이름입니다.
2. 다음 명령을 입력하십시오.
```
apic start
```
그러면 LoopBack&reg; 프로젝트(API) 및 Micro Gateway가 로컬로 실행됩니다. 다음 메시지가 표시됩니다.
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
여기서, `<loopback-project>`은(는) 프로젝트를 포함하는 디렉토리의
이름입니다.

그리고 예를 들어 `curl`을 사용하여 API 엔드포인트를 테스트할 수 있습니다.
웹 브라우저를 사용하여 API를 로드하려면
브라우저에서 `http://localhost:4001`을 여십시오. 기본 LoopBack&reg;(비어 있음 또는 hello-world) 프로젝트의 경우에는 아래와 유사한 내용이 표시됩니다.
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### CLI에서 Bluemix로 LoopBack 애플리케이션 공개
{: #pub_lb_app_cli}

명령행에서 {{site.data.keyword.Bluemix_short}}에 LoopBack 애플리케이션을 공개하려면 다음 단계를 완료하십시오.

1. 다음 명령을 입력하여 Loopback 프로젝트 디렉토리에 있는지 확인하십시오.
```
cd <loopback-project-dir>
```
2. 다음 명령을 입력하여 {{site.data.keyword.apiconnect_short}} 및 {{site.data.keyword.Bluemix_short}}에 로그인하십시오.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
여기서,
  * `<username>`은(는) {{site.data.keyword.apiconnect_short}} 조직 ID입니다.
  * `<password>`은(는) {{site.data.keyword.apiconnect_short}} 비밀번호입니다.
3. 스페이스바를 눌러 **1회성 패스코드** 브라우저 페이지를 자동으로 여십시오.
4. **재생성**을 클릭하고 1회성 패스코드를 복사하십시오.
5. CLI에 돌아가서 패스코드를 붙여넣기하여 로그인을 완료하십시오. 다음 메시지가 표시됩니다.
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. 다음 명령을 입력하십시오.
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
여기서,
  * `<region>`은(는) {{site.data.keyword.Bluemix_short}} 지역입니다.예: 
  * `eu`({{site.data.keyword.Bluemix_short}} London을 사용 중인 경우)
  * `us`({{site.data.keyword.Bluemix_short}} Dallas를 사용 중인 경우)
  * `au`({{site.data.keyword.Bluemix_short}} Sydney를 사용 중인 경우)

  확실하지 않은 경우 메뉴 표시줄의 {{site.data.keyword.avatar}} 아이콘 <img src="images/i-avatar-icon.svg" alt="avatar icon"/>을 클릭하여 계정 및 지원 위젯을 열고 지역 필드를 확인하여 지역을 알 수 있습니다.
7. 다음 명령을 입력하여 애플리케이션을 {{site.data.keyword.Bluemix_short}}에 공개하십시오. 
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
여기서,
  * `<app>`은(는) 앱의 이름입니다.
  * `<org>`은(는) {{site.data.keyword.Bluemix_short}} 조직의 이름입니다.
  * `<region>`은(는) {{site.data.keyword.Bluemix_short}} 지역입니다.
다음과 같은 출력이 리턴됩니다.
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. 그다음, 공개 시간 중에 리턴된 값으로 제품 정의를 수정해야 합니다. 이를 수행하려면 다음 단계를 완료하십시오. 

    1. API Designer UI에서 **API**를 클릭하십시오. 
    2. API를 선택하십시오. 
    3. **어셈블**을 클릭하십시오. 
    4. 어셈블리 편집기에서 **필터 정책** 아이콘을 클릭하십시오. 
    5. **DataPower Gateway 정책**을 선택하십시오. 
    6. **호출**을 두 번 클릭하십시오. 
    7. 7단계에서 검색한 값으로 다음 필드를 업데이트하십시오.
        - **URL 호출**: API 대상 URL을 삽입하십시오. 보안 프로토콜 HTTPS를 지정해야 합니다. 
        예:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        이 값을 기록해 두지 않은 경우 7단계에서 리턴된 관리 URL로 이동하여 검색할 수 있습니다.
        {{site.data.keyword.Bluemix_short}}에 로그인한 후 앱 정보를 확인하여 이 값을 검색할 수도 있습니다.
        - **TLS 프로파일**: API invoke tls-profile을 삽입하십시오. 예: 
        ```
        client:Loopback-client
        ```
    8. **저장**을 클릭하여 API를 저장하십시오. 

## API Designer를 사용하여 LoopBack API 작성
{: #create_lb_api_design}

다음 프로시저는 API Designer를 사용하여 LoopBack&reg; API를 작성하는 방법에 대해 설명합니다.
{:shortdesc}

### 전제조건
{: #prereq_create_lb_api_design}

**참고**: 다음 지시사항에서는 최신 버전의 개발자 툴킷을
사용한다고 가정합니다. 최신 버전을 확인하려면 [npm ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.npmjs.com/package/apiconnect){:new_window} 패키지 페이지를 참조하십시오.

우선 CLI를 통해 LoopBack&reg; 프로젝트를 작성해야 합니다. 이 작업을 수행하려면 다음 단계를 완료하십시오.

1. 프로젝트를 작성하려면 명령행을 열고 다음을 입력하십시오. 
  ```
  apic loopback
  ```
  {: codeblock}

2. 다음에 표시되는 프롬프트에서, 사용자는 애플리케이션 이름을 지정하도록 요청을 받습니다. 이름을 입력한 후
**Enter**를 누르십시오.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    도구에서 프로젝트가 작성될 디렉토리의 이름을 입력하도록 프롬프트를
    표시합니다.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. **Enter**를 눌러서 이전에 입력한 이름을 사용하거나 새 이름을 입력한 후에 **Enter**를 누르십시오. 도구에서 작성할 애플리케이션의 유형을 선택하도록 프롬프트를
표시합니다. 
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. 사용할 애플리케이션을 선택하고 **Enter**를 누르십시오.
이 도구는 프로젝트 디렉토리를 작성한 다음 여러 디렉토리와 파일을 추가하면서
여러 메시지를 표시합니다. 또한 `package.json`에 지정된 대로
`npm install`을 실행하여 모든 프로젝트 종속 항목을 설치합니다.
이 프로세스는 다소 시간이 걸릴 수 있습니다. 

5. 모델을 작성하기 전에, 사용자는 현재 작업 디렉토리가 프로젝트 최상위 레벨 디렉토리인지
확인해야 합니다. 이를 수행하려면 다음 명령을 입력하십시오. 
```
cd <project directory name>
```

**참고**: 현재 작업 디렉토리를 프로젝트 최상위 레벨 디렉토리로 설정하면
API Designer를 열 때 모델 및 데이터 소스를 추가하는 옵션을 사용할 수 있습니다. 
디렉토리를 변경하지 않고 API Designer를 열면 모델 및 데이터 소스를 추가할 수
없습니다. 

API Designer를 열려면 다음 단계를 완료하십시오.
1. 명령행을 열고 다음을 입력하십시오. 
```
apic edit
```
    잠시 후에 다음 메시지가 표시됩니다.
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    API Designer가 기본 웹 브라우저에서 열립니다.

2. 로그인 페이지에서 Bluemix&reg; ID 및 비밀번호를 입력하십시오. **로그인**을 클릭하십시오. 

3. **모델**을 클릭하십시오. 

4. **추가**를 클릭하십시오. LoopBack&reg; **모델** 창이 열립니다.

5. 모델 이름을 입력하십시오.
일반적으로, 모델 이름에는 영숫자 문자, 대시 및 밑줄을 사용할 수
있습니다. 

6. **새로 작성**을 클릭하십시오. 

7. 모델 편집기 페이지에서 특성으로 이동하고 **추가**를 클릭하십시오. 

8. 특성 이름을 입력하고 유형을 선택하십시오. 

9. 모델에 대한 특성 입력이 완료되면 **저장**을 클릭하십시오. 

기본적으로, 비어 있는 LoopBack&reg; 프로젝트에는 데이터 소스가 정의되어 있지 않습니다. 데이터 소스를 정의하려면 다음 단계를 완료하십시오. 
1. **데이터 소스**를 클릭하십시오. 

2. **추가** 아이콘을 클릭하십시오.
새로운 LoopBack&reg; **모델** 창이 열립니다.

3. 데이터 소스 이름을 입력하십시오. 데이터 소스 이름에는 영숫자 문자, 대시 및 밑줄을
사용할 수 있습니다. 

4. **새로 작성**을 클릭하십시오.
데이터 소스가 데이터 소스의 목록에 나타나며, 편집기가 새 데이터 소스의 설정으로
`server/datasources.json` 파일을 업데이트합니다. 

5. 데이터 소스를 클릭하여 해당 설정을 보십시오. 

6. 커넥터 설정을 필요한 커넥터로 변경하십시오. 

7. API Designer가 시작된 콘솔로 되돌아가서 다음 명령을 입력하여 커넥터를
설치하십시오. 
```
npm install --save <connector-package>
```
여기서, `<connector-package>`은(는) 사용자가 선택한 LoopBack&reg; 커넥터의 npm 패키지 이름입니다. 커넥터 패키지의 목록은 다음 표를 참조하십시오.

**참고:** 인메모리 및 이메일 커넥터는 LoopBack&reg;에서 기본 제공되므로 설치하지 않아도 됩니다.

<table>
<caption>표 3. LoopBack 커넥터</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="3rd_d70e1489" class="thleft style-scope doc-content">데이터 소스</th>
<th style="width: 50%" id="3rd_d70e1491" class="thleft style-scope doc-content">커넥터 패키지</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP 웹 서비스</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST 웹 서비스</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

자세한 정보는 [LoopBack 문서 - 커넥터 빌드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://http://loopback.io//doc/en/lb3/Defining-data-sources.html){:new_window}을 참조하십시오.

**참고:** Oracle 커넥터를 선택한 경우에는 Oracle 앱이 시작할 수 있도록
{{site.data.keyword.Bluemix_short}}에서 환경 변수를 설정해야 합니다. 
이를 수행하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.Bluemix_short}} UI에서
**컴퓨팅**을 클릭하십시오. 

2. CF 애플리케이션에서 작업할 애플리케이션을 선택하십시오. 

3. **런타임**을 클릭하십시오. 

4. **환경 변수**를 선택하십시오. 

5. 사용자 정의 섹션에서 **추가**를 클릭하십시오. 

6. **이름** 필드에서 `LD_LIBRARY_PATH`를 입력하십시오. 

7. **값** 필드에서
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`를 입력하십시오. 

8. **저장**을 클릭하십시오. 

LoopBack&reg; 프로젝트를 테스트하려면 다음 단계를 완료하십시오.
1. **서버 시작** 아이콘을 클릭하십시오.
다음 메시지가 표시됩니다.
```
http://localhost:<4001/>Running
```
프로젝트 구성 및
기타 프로세스가 실행 중인지 여부에 따라 다른 포트 번호가 표시될 수
있습니다.

2. **localhost:4001**을 클릭하여 API 루트 엔드포인트를 표시하십시오. 기본
LoopBack&reg;(비어 있음 또는 hello-world) 프로젝트의 경우에는
아래와 유사한 내용이 표시됩니다.
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

다음으로 제품을 작성해야 합니다. 자세한 정보는 [제품 작성](managing_products.html#create_products)을 참조하십시오.
**팁**: 새 명령 프롬프트를 시작할 때마다, 현재 작업 중인 디렉토리가
프로젝트 최상위 레벨 디렉토리인지 확인하십시오. 이를 수행하려면 다음 명령을
입력하십시오. 
```
cd <project directory name>
```

## 개발자 툴킷 설치 제거
{: #uninstall_dev_tk}

### 전제조건
{: #prereq_uninstall_dev_tk}

시작하기 전에, 다음 명령을 입력하여 로컬로 실행 중인 앱을 중지해야
합니다. 
```
apic stop --all
```

개발자 툴킷을 설치 제거하려면 다음 단계를 완료하십시오.

1. 다음 명령을 입력하십시오.
```
npm rm -g apiconnect
```
{: codeblock}

2. npm 캐시를 지우십시오. 
```
npm cache clean
```
{:codeblock}
  
Windows를 사용하는 경우 다음을 수행하십시오.

3. `C:\Users\username\AppData\Local\Temp`에서 해당 이름이 `npm-`로 시작하는 모든 파일을 삭제하십시오. 
4. `<home_dir>\.apiconnect` 디렉토리를 삭제하십시오. 여기서 `<home_dir>`은(는) 툴킷이 이전에 설치된 사용자 계정의 홈 디렉토리입니다.

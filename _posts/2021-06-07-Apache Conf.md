---
layout: post
title:  "Apache Configuration(1) - httpd.conf"
categories: Apache Configuration httpd.conf
---
### Apache Configuration(1) - httpd.conf
Apache Configuration File은 다양한 종류로 나누어 저장 가능

그 중 기본이자 핵심 설정 파일인 httpd.conf 파일 핵심 기능 파악해보고자 한다.

#### httpd.conf 항목 분석
- ServerRoot "[디렉토리 위치]": Apache 서버의 Root 디렉토리 설정
<br>
ex)
```
ServerRoot "/etc/httpd"
```
<br>
- Keepalive [On(default)/Off]: 클라이언트의 지속적인 요청 작업들을 계속 처리하도록 허용할 것에 대한 여부 설정(성능 직접적 연관 있음)
    - maxkeppaliverequest [숫자]: Keepalive On 인 경우 최대 숫자 만큼 연결 제한
    - KeepAliveTimeout [숫자]
- Listen [Port]: 들어오는 포트 지정
- Servername [도메인]: 서버 도메인 설정
- LoadModule [${ServerRoot}/modules]: 모듈 읽어들이고 사용가능 모듈 추가.
- Include [설정파일]: Apache 설정 파일 (vhost, ssl 등) 분산되어있는 설정파일을 로드 할 수 있도록 한다.
- Directoryindex [파일1, 파일2, ...]: 웹 디렉토리 접근 시 인식되는 파일 순서
- &lt;VirtualHost&gt; ~ &lt;/VirtualHost&gt; : 여러 주소와 포트에 대해 다른 행동을 지정할 수 있도록 설정 가능
    ```
    80포트 - http
    443포트 - https
    이렇게 두 프로토콜에 대한 설정을 모두 할 수 있다.

    <VirtualHost *:80>
    ServerAdmin hong@example.com
    DocumentRoot "/www/hong/pages"
    ServerName hong.blog.com
    </VirtualHost>

    <VirtualHost *:443>
    ServerAdmin hong@example.com
    DocumentRoot "/www/hong/pages"
    ServerName hong.blog.com
    </VirtualHost>
    ```
- &lt;Directory "[위치]"&gt; ~ &lt;/Directory&gt; : 서버 일부분에만 적용되게 하기 위해서 해당 블록들을 사용 VirtualHost와 거의 비슷
- Files 섹션 : 해당 파일에 대한 접근 허용 및 거부가 가능.
    ```
    ex) private.html 에 해당하는 접근 거부
    <Files private.html>
    Order allow,deny
    Deny from all
    </Files>

    이런 식으로 directory와 결합하여 사용하여 특정 위치의 파일에 한해서 접근 거부 가능.
    <Directory /var/web/dir1>
        <Files private.html>
        Order allow,deny
        Deny from all
        </Files>
    </Directory>
    ```


추가 사항 계속 업로드 예정

### 참조
https://httpd.apache.org/docs/2.4/en/
---
layout: post
title:  "SSL Offloding"
categories: SSL LoadBalancer
---
### SSL Offloding?
#### SSL?
Secure Socket Layer로 보안 프로토콜의 한 종류.

TCP/IP 계층 구조에서 전송 계층과 응용 계층 사이에서 암호화 해주는 계층으로 TLS와 함께 보안 계층이라는 독립적인 프로토콜 계층으로 존재(간단히 암호화 하는 계층)
HTTPS는 HTTP와 TLS(SSL)가 조합된 프로토콜을 말함.

#### SSL Offloading 방식?
SSL을 통해 전송된 정보는 서버쪽에서는 암호화를 풀고 처리를 해야하는데
복호화하는 동작을 서버가 아닌 그 앞단에서 처리하여 서버는 복호화/암호화하는 리소스가 없도록 별도에 장치(서버)에서 처리하는 방식을 말함.
별도의 장치들 중에 대표적으로 Load Balancer SSL Offloading이 있다.

#### Load Balancer?
일반적으로 시중에 이용되는 서비스들은 하나의 서버가 아닌 다중 서버로 이루어져 있다.
이러한 다중 서버를 사용하여 서버별 부하를 적절히 나누어주기 위해 Load Balancer가 존재.
<br>
이 Load Balancer에서 SSL을 처리하여 서버에게 전달하여 좀더 빠르게 서비스가 가능함.

### 참조
https://blog.naver.com/skinfosec2000/222135874222
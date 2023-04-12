---
layout: post
title: "시스템 공격 기법의 종류와 개념"
date: 2023-04-12
categories: "소프트웨어 개발 보안 설계"
---

1. DoS(Denial of Service)

* 개념

~DoS~ 공격은 시스템을 악의적으로 공격, 그에 따라 해당 시스템의 자원을 지나치게 많이 소모하게 하여, 본 의도에 따라 자원을 사용하지 못해 '서비스 제공 거부/불가'를 유도하는 공격을 말한다.

특정 서버에서 수많은 접속 시도를 생성하여 다른 이용자들이 정상적으로 서비스를 이용하지 못하게 하는 방식, 서버 내의 TCP 연결을 소진시키는 등의 방식이 있다.

* 종류

| 공격기법 | 설명 |
| :------ | :---- |
| SYN Flooding | 서버의 동시 가용 사용자 수 만큼 SYN 패킷만 전송하여 서버를 점유, 다른 사용자가 사용할 수 없도록 하는 공격 |
| UDP Flooding | 대량의 UDP 패킷을 생성하여 서버의 임의 포트로 전송하여, 그에 따른 응답 메시지를 서버에서 생성하게 하여 지속적인 자원 고갈을 야기하는 공격 |
| Smurf, Smurfing | 공격 대상의 IP로부터 네트워크 전체에게 응답 메시지 Echo 패킷을 직접 브로트캐스팅하여 마비시키는 공격 (바운스 사이트라 하는 제 3의 사이트를 이용해 공격) |
| Ping of Death | 응답 메시지의 패킷을 정상적인 크기보다 아주 크게 만들어 전송, 패킷 재조합 과정에서 서버의 자원 고갈을 야기하거나 버퍼의 오버플로우를 일으키는 공격 |
| LAND Attack | 출발지와 목적지의 IP를 같은 패킷 주소로 만들어 루프를 생성시키는 가용성 침해 공격 |
| Tear Drop | IP 패킷 재조합 과정에서 IP Fragment Offset 값이 서로 중첩되도록 조작하여 전송, 그에 따라 재조합 과정에서 오류 발생을 야기시키는 공격 |
| Bonk | 프로토콜 오류 제어 이용, 같은 시퀀스 번호를 지속적으로 전송하여 패킷 재조립 발생, 그에 따른 시스템 과부하 유발 |
| Boink | 프로토콜 오류 제어 이용, 일정한 간격으로 시퀀스 번호에 빈 공간을 생성하여 패킷 재전송 발생, 그에 따른 시스템 과부하 유발 |



2. DDoS(Distributed DoS)

* 개념

~DDoS~ 공격은 DoS 공격의 한 형태로써 여러 대의 공격자를 분산 배치하여 동시에 동작하게 하는 DoS 공격을 말한다.

* 구성 요소

| 구성요소 | 형태 | 설명 |
| :------ | :--: | :---- |
| Attacker | 컴퓨터 | 공격을 주도 (해커) |
| Master | 시스템 | 공격자에게서 직접 명령 수신, 에이전트 관리 |
| Agent | 시스템 | 공격 대상에게 직접 공격 |
| Handler | 프로그램 | 마스터 시스템의 역할을 수행 |
| Daemon | 프로그램 | 에이전트 시스템의 역할을 수행 |

* 공격 도구

| 공격도구 | 설명 |
| :------ | :---- |
| Tirinoo | UDP Flooding을 유발하는 데 사용되는 도구 |
| Tribe Flood Network | Trinoo와 유사하지만, UDP Flooding 뿐만 아니라 SYN Flooding, Smurf 공격 수행 가능 |
| Stacheldraht | Linux 및 Solaris 시스템용 멀웨어 도구로, ICMP/SYN/UDP Flooding과 Smurf 등의 공격 수행 가능 |

* 종류

| 구분 | 종류 | 상세 유형 |
| :-----: | :--- | :---- |
| 대역폭 소진 공격 (3, 4 계층) | UDP/ICMP Traffic Flooding | UDP/ICMP Flooding, DNS Query Flooding |
|  | TCP Traffic Flooding | SYN Flooding, SYN+ACK Flooding |
|  | IP Flooding | LAND Attack, Teardrop |
| 서비스(앱) 마비 공격 | HTTP Traffic Flooding | GET Flooding, GET with Cache-Control |
|  | HTTP Header/Option Spoofing | Slowris, Slowloris, Slow HTTP Read DoS |
|  | Other L7 Service Flooding | Hash DoS, Hulk DoS, FTP/SMTP Attack |



3. DRDoS(Distributed Reflection DoS)

* 개념

~DRDoS~ 공격은 공격자가 출발지 IP를 공격대상 IP로 위조하여 다수의 반사 서버로 요청 정보를 전송, 공격 대상자는 반사(reflection) 서버로부터 다량의 응답을 받아 서비스 거부(DoS)를 유도하는 공격이다.

* 공격 도구

| 순서 | 절차 | 설명 |
| :-: | :-----: | :---- |
| 1 | 출발지 IP 변조 | 공격자가 출발지 IP를 목적지 IP로 Spoofing 하여 SYN 패킷을 경유지 서버로 전송 |
| 2 | 공격 대상자 서버로 응답 | SYN 패킷을 수신한 경유지 서버는 Spoofing된 IP(목적지)로 SYN/ACK 전송 |
| 3 | 서비스 거부(DoS) | 목적지(공격 대상지) 서버는 수많은 SYN/ACK를 수신하여 서비스 거부 발생 |




4. Session Hijacking(세션 하이재킹)

* 개념

~Session Hijacking~ 공격은 TCP Sequence Number의 보안 취약점을 이용한 공격 방법으로, 피해자와 서버 사이의 패킷을 Sniffing하여 Sequence Number를 획득하고 강제로 피해자와 서버 사이를 비동기화시킨 후 공격하는 방식이다.
피해자-서버 간 비동기화에 따라 패킷이 유실되어 재전송 패킷이 증가하게 되고, 이에 ACK Storm 증가, 네트워크 부하 증가를 야기한다.




5. Application Attack(어플리케이션 공격)

* 종류

| 공격기법 | 설명 |
| :------ | :---- |
| Flooding (HTTP GET Flooding) | Cache Control Attack 공격으로, 과도한 Get 메시지를 이용해 웹 서버의 과부하를 야기, HTTP 캐시 옵션을 조작하여 캐싱 서버가 아닌 웹 서버가 직접 처리하도록 유도하여 웹 서버 자원을 소진시키는 DoS 공격 |
| Slow HTTP Header DoS (Slowloris) | HTTP GET 메서드를 사용, 헤더의 최종 개행 문자열을 전송하지 않아 웹 서버와의 연결상태를 장시간 지속시키는 DoS 공격 |
| Slow HTTP POST DoS (RUDY) | 요청 헤더의 Content-Length를 비정상적으로 크게 설정, 메시지 바디를 매우 소량으로 보내 웹 서버와의 연결상태를 장시간 지속시키는 DoS 공격 |
| Slow HTTP Read DoS | TCP 윈도 크기와 데이터 처리율을 감소시킨 상태에서 다수의 HTTP 패킷을 지속적으로 전송하여 웹 서버와의 연결상태를 장시간 지속시키는 DoS 공격 |
| Hulk Dos | 공격 대상 웹 사이트 URL을 지속적으로 변경하면서 다량의 GET 요청을 발생시키는 DoS 공격 |
| Hash Dos | 조작된 많은 수의 해시 파라미터를 POST하여 다수의 해시 충돌을 발생시키는 DoS 공격 |




5. Network Attack(네트워크 공격)

* 종류

| 공격기법 | 설명 |
| :------ | :---- |
| Sniffing | 직접 공격하지 않고 데이터만 몰래 들여다보는 공격 |
| Scanner/Sniffer | 네트워크 HW/SW 구성의 취약점 파악을 위해 공격자가 취약점을 탐색하는 도구 |
| Password Cracking | Dictionary Cracking - ID와 패스워드가 될 가능성이 있는 단어를 파일로 만들어 놓고 이 파일의 단어를 대입하여 크랙 |
|  | Brute Force Cracking - 무작위 패스워드를 대입하여 크랙 |
|  | Password Hybrid Attack - 사전 공격과 무차별 대입공격을 결합하여 크랙 |
|  | Rainbow Table Attack - 패스워드 별 해시 값을 미리 생성하여 테이블에 모아두고 크랙하고자하는 해시 값을 테이블에서 역으로 검색 |
| IP Spoofing | 본인의 패킷 헤더를 인증된 호스트의 IP 주소로 위조하여 타깃에 전송 |
| ARP Spoofing | 특정 호스트의 MAC 주소를 자신의 MAC 주소로 위조한 ARP Replay를 만들어 피해자에게 지속적으로 전송, 피해자로부터 특정 호스트로 나가는 패킷을 스니핑 |
| ICMP Redirect | 3계층에서 스니핑 시스템을 라우터로 속여 패킷의 흐름을 바꾸고, ICMP Redirect 메시지를 원하는 형태로 생성하여 패킷을 스니핑 |
| Trojan horses | 악성 루틴이 숨어있는 프로그램으로, 겉으로는 정상적으로 보이나 실행하면 악성 코드를 실행 |


# 개요
- 리눅스에서 현재 서버의 포트 상태를 확인하는 명령어이다. 

## 자주 사용하는 서비스 포트 번호 

| 포트번호 | TCP/UDP | 서비스명 |
|-------| ------|-------|
| 20 | tcp | FTP 데이터|
| 21 | tcp | FTP |
| 22 | tcp | SSH |
| 25 | tcp | SMTP |
| 53 | tcp, udp | DNS | 
| 80 | tcp, udp | HTTP |
| 110 | tcp | POP3 | 
| 161 | udp | SNMP | 
| 443 | tcp | HTTPS | 

- 일반적으로 포트는 방화벽에서 열어준다.
- 다시 말해서, 방화벽이 내려져 있다는 것은 모든 포트에서의 접근을 허용한다는 말
- 포트는 도착지 쪽 서버를 열어줘야 한다. (출발지 쪽이 아니다.)

## 포트 상태 확인법 
- netstat 명령어를 사용한다.
- 만약 netstat 명령어가 없다면 yum install net-tools로 설치하자. 

```
netstat -nap | grep 포트번호 or 서비스명 
// 원하는 특정 포트 번호, 서비스명이 열려있는지 확인하기 

netstat -nap 
// 현재 열려있는 모든 포트 / 서비스를 표시 
```

> 옵션
- n : HOST 명으로 표시 
- a : 모든 소켓 표시 
- p : 프로세스 ID와 프로그램명 표시
- l : 연결 가능 상태 표시 
- t/u : tcp / udp 
- r : 라우팅 테이블
- s : 네트워크 통계


## 자주 사용하는 명령어 
> netstat -nap 
- 연결을 기다리는 목록과 프로그램 표시 
> netstat -an | grep 포트번호
- 특정 포트 사용 중인지 표시 
> netstat -an | grep LISTEN 
- 현재 열려있는 모든 포트 표시 
> netstat -nlpt 
- TCP listening 상태의 포트와 프로그램 표시 
> netstat -an | grep ESTABLISH 
- 연결되어있는 모든 포트 표시 

## 상태 확인 
- LISTEN : 표트가 열려있는 상태, 연결 대기 
- SYS_SENT : 클라이언트가 연결 요청 상태 
- SYN_RECEIVED : 연결 요청 응답 후 확인 대기 
- CLOSE : 연결이 끊어짐 
- CLOSE_WAIT : 연결이 종료되기를 기다리는 상태 
- ESTABLISH : 연결이 되어있는 상태 

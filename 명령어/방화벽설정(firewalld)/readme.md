# firewalld

자료 참고
- [자료1](https://it-serial.com/6)
 
# 개요
- CentOS 7에서는 firewalld 서비스가 기본 방화벽으로 활성화되어있다. 
  - 이전에는 Iptables를 사용했으나 7 버전부터 변경되었다. 

- 방화벽에는 Zone(영역)이라는 것이 존재합니다. 
  - 개방된 네트워크와 연결되어있을 경우 Public Zone에 있는 Rule을 적용 
  - 개인 네트워크에 연결되어있을 경우 다른 Rule을 적용
  - 보통 서버용도로 사용하기 때문에 Public Zone으로 사용하고, Default값도 Public Zone이다. <br>
  ( /usr/lib/firewalld/ 위치에서 확인가능하다.) 
  
  - Zone은 보안그룹과 유사한 역할을 수행한다. 방화벽 설정을 묶어놓고 상황에 따라서 다르게 적용한다. 
  - 시스템 개별 설정은 /etc/firewalld 에 있으며 firewalld 동작은 /etc/firewalld/firewalld.conf에서 설정할 수 있다. 
  
# 명령어

## 방화벽 시작 및 종료
```
systemctl start firewalld  # 방화벽 시작
systemctl enable firewalld # 재부팅시에 자동실행

systemctl stop firewalld   # 방화벽 중지
systemctl disable firewalld # 재부팅시에 자동실행하지 않음 
```

## 방화벽 설정 후 적용
```
firewall-cmd --reload

# (주의!) 설정을 저장하고 재시작하지 않으면 적용이 되지 않습니다. 
```

## 방화벽에 Port 추가/제거
```
firewall-cmd --permanent --zone=public --add-port=[포트번호]/[프로토콜]
# firewall-cmd --permanent --zone=public --add-port=8080/tcp 
# --permanent : 영구적으로 적용
# --zone=public : public zone(default)에 적용
# --add-port= : 포트 추가 

firewall-cmd --permanent --zone=public --remove-port=[포트번호]/[프로토콜]
# firewall-cmd --permanent --zone=public --remove-port=8080/tcp

# 항상 설정한 뒤에는 firewall-cmd --reload 로 재시작해야 한다. 
```

## 방화벽 상태 확인 
```
# 활성화된 포트/서비스 확인
firewall-cmd --list-ports 
firewall-cmd --list-services

# 설정된 내용 모두 확인
firewall-cmd --list-all

# 현재 상태 확인
firewall-cmd --state

# 현재 적용되고 있는 zone 확인
firewall-cmd --get-default-zone

# 활성화되어있는 zone 확인
firewall-cmd --get-active-zone
```




  


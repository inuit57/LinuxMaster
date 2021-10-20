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
  
  
  


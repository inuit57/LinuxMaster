자료 참고
- [자료1](https://happist.com/553442/%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-%EC%9E%90%EB%8F%99-%EC%8B%A4%ED%96%89%EC%9D%84-%EA%B0%80%EB%8A%A5%EC%BC%80-%ED%95%B4%EC%A3%BC%EB%8A%94-crontab%ED%81%AC%EB%A1%A0%ED%83%AD-%EC%84%A4%EC%A0%95)


# 개요
- UNIX 계열에서 특정 시간마다 예약된 작업을 수행하도록 하는 **Cron** 이라는 Daemon이 있다.
- 그리고 cron이 작업할 내용들을 특정 파일에 작성하는 명령어가 **crontab** 입니다.
- Windows OS에 존재하는 작업스케줄러와 유사한 기능이라고 이해하면 됩니다. 


# 설정하는 방법
1) 명령어를 사용하는 방법 : crontab -e
2) 파일에 직접 작성하는 방법 : /etc/crontab 파일을 수정 (권장 X) 

변경한 뒤에는 cron 명령어를 입력해서 변경사항이 적용되도록 해줘야 한다. 
```
service cron status # checks if cron is running
service cron start  # 단순리 크론을 다시 시작하라는 명령으로 기존 아직 끝나지 않는 명령 리스트를 그대로 가지고 시작한다.  
service cron restart  # 기존 크론 작업 리스트를 버리고 새로운 작업 리스트로 작업
service cron stop   # stops it
```

## crontab 명령어
- 옵션
  1) crontab -e : 명령을 등록, 편집 – 맨 처음에 사용 시 편집기를 선택할 수 있다.
  2) crontab -d : 등록된 명령을 삭제
  3) crontab -l : 현재 등록된 리스트 출력
  4) crontab -l -u otheruser : otheruser 사용자가 등록한 crontab 리스트 출력
  5) crontab -r : 현재 사용자가 등록한 crontab **전체 삭제**


## 설정 가이드
1) 한줄에 하나의 명령어만 사용합니다. 
2) #을 이용해서 주석을 남길 수 있습니다. (쉘 스크립트처럼)
3) 로그 남기기 : * * * * * doitnow.sh > /var/log/crontab.kog 2>%1
4) 백업 남기기 : 00 00 * * * crontab -l > /home/crontab_bak (주기적으로 크론템 파일을 백업)


# 사용예시
![image](https://user-images.githubusercontent.com/24216471/137835528-21ab0ba0-1eeb-4e87-8e88-36394c6f1fba.png)

- 분 / 시 / 일 / 월 / 요일(0: 일요일)
- '*'로 두면 디폴트 값으로 설정된다.
- '*' 대신 해당 위치에 "값"을 넣어준다면 **설정한 시간**마다 반복해서 실행된다. 
- ' * ' 대신 해당 위치에 "*/값"을 넣어주면 **해당 단위 간격**으로 반복해서 실행된다. 

### 값 설정 예시
```
1 * * * * test.sh # 매 시간 1분 간격으로 반복 실행
* 1 * * * tets.sh # 매일 오전 1시에 반복 실행
* * 1 * * test.sh # 매월 1일에 반복 실행
* * * 1 * test.sh # 매년 1월에 반복 실행
* * * * 1 test.sh # 매주 월요일(1) 마다 반복 실행
```

### '*/값' 설정 예시
```
*/1 * * * * test.sh # 1분 간격 실행
* */1 * * * test.sh # 1시간 간격 실행
* * */1 * * test.sh # 1일 간격 실행
* * * */1 * test.sh # 월 간격 실행
```

---------------
## 1분마다 실행할 것
```
* * * * * doitnow.sh
```

## 동일 프로세스를 10분마다 실행
```
*/10 * * * * doitnow.sh
```
## 매시 15분마다 실행
```
15 * * * * doitnow.sh
```
## 1시간마다 실행
```
0 * * * * doitnow.sh
```
## 2시간마다 실행
```
0 */2 * * * doitnow.sh
```
## 오전 11시와 오후 4시마다 실행
```
00 11,16 * * * /home/ramesh/bin/incremental-backup
```
## 근무시간(9시 ~ 오후 6) 내 매시간 실행
특정 작업이 근무 시간에만 실행되도록 설정하기 위해서는 시간을 09-18과 같은 표현을 사용합니다.

00 09-18 * * * /home/ramesh/bin/check-db-status

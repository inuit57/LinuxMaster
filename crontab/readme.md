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

## crontab 명령어
- 옵션
  1) crontab -e : 명령을 등록, 편집 – 맨 처음에 사용 시 편집기를 선택할 수 있다.
  2) crontab -d : 등록된 명령을 삭제
  3) crontab -l : 현재 등록된 리스트 출력
  4) crontab -l -u otheruser : otheruser 사용자가 등록한 crontab 리스트 출력
  5) crontab -r : 현재 사용자가 등록한 crontab 전체 삭제


## 설정 가이드
1) 한줄에 하나의 명령어만 사용합니다. 
2) #을 이용해서 주석을 남길 수 있습니다. (쉘 스크립트처럼)
3) 로그 남기기 : * * * * * doitnow.sh > /var/log/crontab.kog 2>%1
4) 백업 남기기 : 00 00 * * * crontab -l > /home/crontab_bak (주기적으로 크론템 파일을 백업)

자료 참고
- [자료1](https://happist.com/553442/%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-%EC%9E%90%EB%8F%99-%EC%8B%A4%ED%96%89%EC%9D%84-%EA%B0%80%EB%8A%A5%EC%BC%80-%ED%95%B4%EC%A3%BC%EB%8A%94-crontab%ED%81%AC%EB%A1%A0%ED%83%AD-%EC%84%A4%EC%A0%95)


# 개요
- UNIX 계열에서 특정 시간마다 예약된 작업을 수행하도록 하는 **Cron** 이라는 Daemon이 있다.
- 그리고 cron이 작업할 내용들을 특정 파일에 작성하는 명령어가 **crontab** 입니다.
- Windows OS에 존재하는 작업스케줄러와 유사한 기능이라고 이해하면 됩니다. 


# 설정하는 방법
1) 명령어를 사용하는 방법 : crontab -e
2) 파일에 직접 작성하는 방법 : /etc/crontab 파일을 수정


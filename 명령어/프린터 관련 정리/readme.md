# 프린터 시스템 
- LPRng 에서 CUPS 로 전환되었습니다. 
- CUPS는 애플에서 만들어진 오픈소스 프린팅 시스템입니다. 


## 명령어 (BSD 계열)
1. 프린트 작업등록
```
]# lpr [파일명]

-# [매수] : 인쇄할 숫자를 지정

-P : 작업할 프린터 지정

-r : 출력한 뒤 파일 삭제

-l : 필터링 없이 직접 보낸다.
```
- 문제로 출제된 것은 출력한 뒤 파일삭제를 하는 명령어 ( lpr -r test.txt ) 

2. 프린트 작업 내역 (Queue) 
```
]# lpq 

-a : 설정된 모든 프린터의 작업정보 출력

-l  : 작업내역 자세히 출력

-P : 특정 프린터명 지정 후 출력
```

3. 작업목록 삭제,취소 (remove)
```
]# lprm  [파일명]

- : 모든 작업 취소

-U : 특정 사용자의 작업 취소

-P : 프린터명 지정

-h : 지정 서버의 작업 취소
```

## 명령어 (System V 계열)
1. 프린터 인쇄 명령 (= lpr)
```
]# lp [파일명]

-d : 다른 프린터 지정

-n : 인쇄 매수 지정
```

2. 프린터 큐의 상태 출력 ( = lprq)
```
]# lpstat

-p : 프린터의 인쇄 가능여부 출력

-t : 프린터 상태정보 출력

-a : 받아들이는 요청상태 출력
```

3. 프린터 작업 취소 (= lprm)
```
]# cancel

-a : 모든 작업 취소
```

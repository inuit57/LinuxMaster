# 개요
- 리눅스에서 파일의 문자열을 바꾸는 방법에 대해서 기술한다.
- 추가적으로, 여러 파일에서 특정 문자열을 찾아서 바꾸는 것에 대해서도 적어본다. 


## 파일 1개인 경우
- vi 편집기를 사용하여 처리한다. 
```
: [범위] / [찾을 문자열] / [바꿀 문자열] / [옵션]
```
- [자료출처1](https://danguria.tistory.com/171)
- [자료출처2(옵션)](https://techlog.gurucat.net/297)

### 옵션
|옵션명| 설명|
|-----|----|
| g | 모두 선택 |
| c | 확인 후 처리 |
| i | 대소문자 구분 안함 |


### 예시
| 명령어 | 설명|
|-----------|------------|
| :s/old/new | 현재 행에서 처음 찾은 old를 new로 치환 | 
| :s/old/new/g | 현재 행에서 모든 old를 new로 치환 | 
| :10,20s/old/new/g | 10~20행의 모든 old를 new로 치환 | 
| :%s/old/new/g | 문서 전체에서 모든 old를 new로 치환 |
| :%s/old/new/gc | 문서 전체에서 모든 old를 new로 확인해서 치환 | 


## 파일이 여러 개인 경우
- find와 perl 명령어를 적절하게 사용해주면 된다. 
- [자료참고](https://itholic.github.io/linux-find-replace-files/)
- [자료참고2](https://javafactory.tistory.com/470)

```
#perl -pi -e  's/원본문자열/바꿀문자열/g' <파일명>

-e : 주어진 perl 명령어 실행
-p : 지정한 파일을 대상으로 작업
-i : 원본파일을 결과파일로 대체 
```


```
#find . -name "*.sh" -exec perl -pi -e 's/hello/bye/g' {} \;
#find ./ -name '*.html' -exec perl -pi -e 's/EUC_KR/UTF-8/g' {} \;

- {} : find 에서 찾아낸 검색 결과가 하나씩 들어가는 부분
- \  : -exec 다음부분에 나와있는 명령어 를 실행하라는 부분
```


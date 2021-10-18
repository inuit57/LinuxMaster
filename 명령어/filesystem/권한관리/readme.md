참고자료 
- https://recipes4dev.tistory.com/175
- https://eunguru.tistory.com/93?category=667830


## 1. 접근 권한 관리 (chmod) 
- 기존 파일 또는 디렉터리에 대한 접근 권한(file mode)을 변경하는 명령어
- File Mode의 변경은 파일 소유자 혹은 Super User만 가능

### 사용법
- chmod [option] ...Mode... FILE

- Mode : 알파벳 소문자 또는 숫자로 설정가능한 접근권한 모드 표기
- FILE : 변경할 파일 또는 디렉터리명을 작성. 

### 주요 옵션
- -R : (Recursive) 하위 디렉터리와 파일에게도 해당 변경사항을 적용시킨다. 

## 1-1. 접근 권한 표기
### 기호(문자)로 표기
- 크게 변경할 사용자(대상), 수행할 명령, 설정할 접근권한(permission)으로 분류된다. 
- 다른 대상의 속성을 건드리지 않고 한 대상 속성만을 설정가능. 
- 복수 지정은 콤마(,)를 사용하여 구분한다. 


<table>
    <thead>
        <tr>
            <th>구분</th>
            <th>기호</th>
            <th>설명</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>사용자<br>(유저)</td>
            <td>u</td>
            <td>user의 약자, 파일이나 디렉터리 소유자를 의미</td>
        </tr>
        <tr>
            <td>g</td>
            <td>그룹 소유자</td>
        </tr>
        <tr>
            <td>o</td>
            <td>others, 기타 사용자를 의미</td>
        </tr>
        <tr>
            <td>a(default)</td>
            <td>All, u+g+o 모두를 의미</td>
        </tr>
    </tbody>
    <tbody>
        <tr>
            <td rowspan=3>수행할 명령<br>(연산)</td>
            <td>+</td>
            <td>추가</td>
        </tr>
        <tr>
            <td>-</td>
            <td>제거</td>
        </tr>
        <tr>
            <td>=</td>
            <td>변경, 기존의 값은 사라짐.</td>
        </tr>
    </tbody> 
    <tbody>
        <tr>
            <td rowspan=3>설정할 접근권한<br>(permission)</td>
            <td>r</td>
            <td>읽기</td>
        </tr>
        <tr>
            <td>w</td>
            <td>쓰기</td>
        </tr>
        <tr>
            <td>x</td>
            <td></td>
        </tr>
    </tbody>
</table>


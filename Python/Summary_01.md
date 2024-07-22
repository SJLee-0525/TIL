# CLI
### 명령어  
- `ls` : 현재 작업 중인 디렉토리 내부의 폴더 / 파일 목록을 출력

- `touch` : 파일명.확장자 : 파일 생성

- `mkdir` : 새 디렉토리 생성make directory (폴더명 뒤에 / 생성)

- `cd 폴더명/` :  현재 작업중인 디렉토리를 변경 change directory (cd .. : 상위 디렉토리로 이동)

- `start 파일명.확장자` : 폴더 / 파일 열기 (mac: open)

- `rm 파일명.확장자` : 해당 파일 제거 (디렉토리는 제거 불가능)
    
    - `rm -r 폴더명/` : 디렉토리 제거하는 명령어
    
- `ctrl + L` : clear

### 경로
- **절대 경로:** Root 디렉토리부터 목적 지점까지 거치는 **모든 경로**를 전부 작성
    
    `C:/Users/ssafy/Desktop`
    
- **상대 경로:** 현재 작업하고 있는 디렉토리를 기준으로 계산된 **상대 위치**를 작성
    
    현재 작업하고 있는 C:/Users일 때: `ssafy/Desktop`

- **CLI에서 ‘.’의 역할:**
    
    - `.` = 현재 디렉토리   

    - `..` = 현재의 상위 디렉토리

    - `~` = 홈 디렉토리 [ /c/Users/SSAFY ]

# GIT
### 명령어
- `git init` : 로컬 저장소 설정 (초기화)  

- `git add 파일명` : 변경 사항이 있는 파일을 Staging Area에 추가   

- `git commit -m “first commit”` : Staging Area에 있는 파일들을 저장소에 기록 

- `git status` : Git의 상태를 확인 
    - `git log` : status가 보여주지 history 보기

    - `git log —oneline` : commit 목록 한 줄로 보기

- `git config` : Git의 설정
    - `git config —global [user.email](http://user.email) “이메일”`

    - `git config —global [user.name](http://user.name) “이름”`

    - `git config —global -l` : git global 설정 정보 보기  

- `git remote add origin remote_repo_url` : 로컬 저장소에 원격 저장소 추가
    - `git remote -v` : 경로 등록된 것 확인

    - `git push origin master` : 원격 저장소에 commit 목록을 업로드
    - `git pull` : push와 대조 / 원격 저장소가 업데이트 되었기 때문에 변경 사항만을 다운로드

    - `git clone remote_repo_url` : 저장소 전체를 복제 / 처음 받을 때 사용함

- `git revert <commit id>` : 변경 사항을 실행취소 할 수 있도록 하는 순방향 실행 취소 작업 (commit을 없던 일로)

- *실행하면 VIM이 실행됨.* 
- *알아서 commit 메시지를 생성해주긴 함*  
    - **명령 모드**: 커서 이동 불가능 / `esc`  

    - **입력 모드**: 커서 이동 가능 /  `i` (insert)  

        - **이름 수정**: 입력모드 → 이름 입력 → 명령모드 → shift + ; →  wq (write, quit) ```
                                    

- `git revert —no-edit <id>` : commit 메시지 작성을 위한 편집기를 열지 않음

- `git revert —no-commit <id>` : 자동으로 commit 하지 않고 Staging Area에만 업로드

- `git reset [옵션] <commit id>` : 특정 commit으로 되돌아가는 작업 (삭제)
    - `git reset —mixed` : 삭제된 commit의 기록을 working directory에 남김 **(빨강: add 전)**
    - `git reset —hard` : 삭제된 commit의 기록을 **남기지 않음**

- `git reflog` : HEAD가 이전에 가리켰던 모든 commit을 보여줌
    - —hard로 지워진 commit도 reflog로 조회하여 복구 가능
    - `git reflog —hard <복구하고자 하는 id>`

- `git restore 파일명` : Modified 상태의 파일 되돌리기 (수정 전으로)

- **Unstage**: **Staging Area**에서 **Working Directory**로 **반환하는 작업**
    - `git rm —cached 파일명` : git 저장소에 **commit이 없을 경우**
    - `git restore —staged 파일명` : git 저장소에 **commit이  존재하는 경우**

- `git commit —amend` : 바로 직전에 생성한 Commit 수정하기
    - **Staging Area가 비어있을 때: 바로 직전의 commit 메시지 수정**
    - **Staging Area에 파일이 있을 때: 바로 직전의 commit에 누락된 파일 업로드**

# PYTHON
### 산술 연산자
| 기호 | 연산자 |
|-----|-------|
| - | 음수 부호 |
| +	| 덧셈 |
| - | 뺄셈 |
| *	| 곱셈 |
| /	 | 나눗셈 |
| // | 정수 나눗셈 (몫) |
| %	 | 나머지 |
| ** |지수 (거듭제곱) |


### 연산자 우선 순위
| 연산자 | 연산 |
|-------|------|
| ** | 지수 |
| -n | 음수 부호 |
| *, /, //, % | 곱셈, 나눗셈, 정수 나눗셈, 나머지 |
| +, - | 덧셈, 뺄셈 |

```python
# 실행 해보기 1
print(-2 ** 4) # -16
print(-(2 ** 4)) # -16
print((-2) ** 4) # 16
```

---

### 복합 연산자

| 기호 | 예시 |	의미 |
|------|------|------|
| += | a += b | a = a + b |
| -= a | -= b |	a = a - b |
| *= a | *= b |	a = a * b |
| /= a | /= b |	a = a / b |
| //= a | //= b | a = a // b |
| %= a | %= b |	a = a % b |
| **= a | **= b | a = a ** b |

---

### 비교 연산자
| 기호 | 내용 |
|------|------|
| <	| 미만 |
| <= | 이하 |
| >	| 초과 |
| >= | 이상 |
| == | 같음 |
| != | 같지 않음 |
| is | 같음 |
| is not | 같지 않음 |

#### is 비교 연산자

- 매모리 내에서 같은 객체를 참조하는지 확인

- `==` 는 동등성(equality): **값이 같은지만 확인**

- `is` 는 식별성(identity): **값 뿐만 아니라 주소까지 같은지 확인**

- 값을 비교하는 `==` 와 다름

- 주로 None, Bool 구분할 때 사용

```python
print(3 > 6)  # False
print(2.0 == 2)  # True
print(2 != 2)  # False
print('HI' == 'hi')  # False
print(1 == True)  # True

# SyntaxWarning: "is" with a literal. Did you mean "=="?
# ==은 값(데이터)을 비교하는 것이지만 is는 레퍼런스(주소)를 비교하기 때문
# 아래 조건은 항상 False이기 때문에 is 대신 ==를 사용해야 한다는 것을 알림
print(1 is True)  # False
print(1 == True)  # True

print(2 is 2.0)  # False
print(2.0 == 2)  # True
```

---

### 논리 연산자
| 기호 | 연산자 | 내용 |
|------|------|------|
| and | 논리곱 | 두 피연산자 모두 True인 경우에만      전체 표현식을 True로 평가 |
| or | 논리합 | 두 피연산자 중 하나라도 True인   경우 전체 표현식을 True로 평가 |
| not | 논리부정 | 단일 피연산자를 부정 |

```python
print(True and False) # False

print(True or False) # True

print(not True) # False

print(not 0) # True
```

### 단축 평가
논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작

#### 단축평가 동작

- **and**
    - 첫 번째 피연산자가 False인 경우, 전체 표현식은 False로 결정.
        - 두 번째 피연산자는 평가되지 않고 그 값이 무시

    - 첫 번째 피연산자가 True인 경우, 전체 표현식의 결과는 두 번째 피연산자에 의해 결정.
        - 두 번째 피연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환
- **or**
    - 첫 번째 피연산자가 True인 경우, 전체 표현식은 True로 결정.
        - 두 번째 피연산자는 평가되지 않고 그 값이 무시

    - 첫 번째 피연산자가 False인 경우, 전체 표현식의 결과는 두 번째 피연산자에 의해 결정.
        - 두 번째 피연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환

```python
vowels = 'aeiou'

print(('a' and 'b') in vowels)  # False: b in vowels
print(('b' and 'a') in vowels)  # True
'b' = T / 'a' = T : T and T : # 뒤에 것이 반환됨

print(3 and 5)  # 5 : 앞에서 True가 나왔기에 뒤에 것 봄
print(3 and 0)  # 0 : 앞에서 True가 나왔기에 뒤에 것 봄
print(0 and 3)  # 0 : 앞에서 False가 나왔기에 뒤에 것 보지 않음 (단축)
print(0 and 0)  # 0 : 앞에서 False가 나왔기에 뒤에 것 보지 않음 (단축)

print(5 or 3)  # 5 : 앞에서 True가 나왔기에 뒤에 것 보지 않음 (단축)
print(3 or 0)  # 3 : 앞에서 True가 나왔기에 뒤에 것 보지 않음 (단축)
print(0 or 3)  # 3 : 앞에서 False가 나왔기에 뒤에 것 봄
print(0 or 0)  # 0 : 앞에서 False가 나왔기에 뒤에 것 봄
```

#### 단축평가 이유

- **코드 실행을 최적화하고, 불필요한 연산을 피할 수 있도록 함**

---

### 멤버십 연산자

- 특정 값이 시퀀스나 다른 컬렉션에 속하는지 여부를 확인

| 기호 | 내용 |
|------|------|
| in | 왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하는지를 확인 |
| not in | 왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하지 않는지를 확인 |

```python
word = 'hello'
numbers = [1, 2, 3, 4, 5]

print('h' in word)  # True
print('z' in word)  # False

print(4 not in numbers)  # False
print(6 not in numbers)  # True
```

---

### 시퀀스형 연산자

| 연산자 | 내용 |
|------|------|
| +	| 결합 연산자 |
| *	| 반복 연산자 |

**`+` 와 `` 는 시퀀스 (str, list, tuple ..) 간 연산에서 산술 연산자일 때와 다른 역할을 가짐**

---


## 변수
#### 변수 할당
```python
degrees = 36.5
방향 = <--
```
1. **할당 연산자(=) 오른쪽에 있는 표현식을 평가해서 값(메모리 주소)을 생성**

2. **값의 메모리 주소를 ‘=‘ 왼쪽에 있는 변수에 저장**

    - **존재하지 않는 변수라면**

        - 새 변수를 생성

    - **기존에 존재했던 변수라면**

        - 기존 변수를 재사용해서 변수에 들어 있는 메모리 주소를 변경

- ex) 변수 double에는 값 20의 주소가 들어 있으니 여전히 20을 참조
    
    ```python
    number = 10
    double = 2 * number
    print(double)  # 20
    number = 5
    print(double)  # 20
    ```
    
> 변수 double에는 **값 20의 주소가 들어 있으니 여전히 20을 참조**

#### 변수명 규칙

- 영문 알파벳, 언더스코어(_), 숫자로 구성

- 숫자로 시작할 수 없음

- 대소문자를 구분

- 파이썬 내부 예약어는 사용할 수 없음

#### 객체
> **“값이 들어있는 상자”**

- 타입을 갖는 **메모리 주소 내의 값** : *주소: 491734*

---

### Style Guide
- 코드의 일관성과 가독성을 향상시키기 위한 규칙과 권장 사항들의 모음

    - **변수명**은 무엇을 위한 변수인지 **직관적인 이름**을 가져야 함

    - **공백(spaces) 4칸**을 사용하여 코드 블록을 **들여쓰기**

    - **한 줄의 길이는 79자**로 제한하며, 길어질 경우 **줄 바꿈을 사용**

    - **문자와 밑줄(_)을 사용**하여 **함수, 변수, 속성의 이름을 작성** (snake_case)

    - 함수 정의나 클래스 정의 등의 **블록 사이에는 빈 줄을 추가**

### Python Tutor
- 파이썬 프로그램이 어떻게 실행되는지 도와주는 시각화 도우미
    
    > https://pythontutor.com/

---

### 주석

- 프로그램 코드 내에 작성되는 설명이나 메모

- 인터프리터에 의해 실행되지 않음

```python
# 이것은
age = 10

# 주석입니다
print(age)

"""
여러 줄 주석
""" 
```

#### 목적
- 코드의 특정 부분을 설명하거나 임시로 코드를 비활성화할 때

- 코드를 이해하거나 문서화하기 위해

- 다른 개발자나 자신에게 코드의 의도나 동작을 설명하는 데 도움

---

## Data Type
- **Numeric Types**
    - `int`, `float`, `complex` (복소수)

- **Text Sequence Type**
    - `str`

- **Sequence Types**
    - `list`, `tuple`, `range`

- **Non-sequence Types** : 순서 X
    - `set`, `dict`

- **기타**
    - `Boolean`, `None`, `Functions`

---

### 1. Numeric Types
#### INT : 정수 자료형
```python
a = 10
b = 0
c = -5
```
- **진수 표현**
```python
print(0b10) # 2진수(binary) : `0b`  
print(0o30) # 8진수(octal) : `0o`
print(0x10) # 16진수(hexadecimal) : `0x`

# 2, 24, 16
```

---

#### FLOAT : 실수 자료형
```python
d = 3.14
e = -2.7
```

- **유한 정밀도**
    - 프로그래밍 언어에서 float는 실수에 대한 근삿값

    - 컴퓨터 **메모리 용량이 한정**돼 있고 **한 숫자에 대해 저장하는 용량이 제한** 됨

    - 0.6666666666666666과 1.6666666666666667은 제한된 양의 메모리에 저장할 수 있는 2/3과 5/3에 **가장 가까운 값**

```python
# 0.6666666666666666
print(2 / 3)

# 1.6666666666666667
print(5 / 3)
```

- **부동소수점 ERROR**  

    컴퓨터가 실수를 표현하는 방식으로 인해 발생하는 작은 오차
- **원인**
    - 실수를 2진수로 **변환하는 과정에서 발생하는 근사치 표현**
    
- **해결법**  
    - `decimal` 모듈을 사용
```python
# 해결 전
a = 3.2 - 3.1
b = 1.2 - 1.1
print(a)  # 0.10000000000000009
print(b)  # 0.09999999999999987
print(a == b) # False

# 해결 후
from decimal import Decimal

a = Decimal('3.2') - Decimal('3.1')
b = Decimal('1.2') - Decimal('1.1')

print(a)  # 0.1
print(b)  # 0.1
print(a == b)  # True
```

- **지수 표현**  
    `e` 또는 `E`를 사용한 지수 표현
```python
# 314 ∗ 0.01 (10 ** -2)
number = 314e-2

# 3.14
print(number)
```

---

### 2. Sequence Types  
> 여러 개의 값들을 순서대로 나열하여 저장하는 자료형

#### Sequence Type 특징

1. **순서(Sequence)**
    - 값들이 **순서대로 저장** (정렬 X)
    
2. **인덱싱(Indexing)**
    - **각 값에 고유한 인덱스(번호)를 가지고** 있으며, **인덱스를 사용**하여 **특정 위치의 값을 선택하거나 수정할 수 있음**

3. **슬라이싱(Slicing)**
    - **인덱스 범위를 조절**해 부분적인 **값을 추출**할 수 있음

4. **길이(Length)**
    - **len() 함수**를 사용하여 **저장된 값의 개수(길이)**를 구할 수 있음

5. **반복(Iteration)**
    - **반목문**을 사용하여 **저장된 값들을 반복적으로 처리**할 수 있음

---

#### STR : 문자 자료형
- 문자열은 단일 문자나 여러 문자의 조합으로 이루어짐

- **작은따옴표(`'`)** 또는 큰따옴표(`"`) 감싸서 표현

- **중첩 따옴표**

    **따옴표 안에 따옴표를 표현할 경우**

    - 작은따옴표가 들어 있는 경우는 큰따옴표로 문자열 생성

    - 큰따옴표가 들어 있는 경우는 작은따옴표로 문자열 생성

```python
# 문자열 안에 '작은따옴표'를 사용하려면 큰따옴표로 묶는다.
print("문자열 안에 '작은따옴표'를 사용하려면 큰따옴표로 묶는다.")

# 문자열 안에 "큰따옴표"를 사용하려면 작은 따옴표로 묶는다.
print('문자열 안에 "큰따옴표"를 사용하려면 작은 따옴표로 묶는다.')
```

#### Escape sequence

- **역슬래시(backslash, `\`)**뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합
- 파이썬의 일반적인 문법 규칙을 잠시 탈출한다는 의미

|     예약   문자    	|      내용(의미)    |
|:------------------:|:------------------:|
|         `\\n`        |      줄  바꿈     |
|         `\\t`        |         탭        |
|         `\\\\`       |       백슬래시     |
|         `\\’`        |     작은 따옴표    |
|         `\\"`        |     큰   따옴표    |

#### f-string
- 문자열에 `f` 또는 `F` 접두어를 붙이고 표현식을 `{expression}`로 작성하는 문법

- 문자열에 파이썬 표현식의 값을 삽입할 수 있음

```python
bugs = 'roaches'
counts = 13
area = 'living room'

# Debugging roaches 13 living room
print(f'Debugging {bugs} {counts} {area}')
```

---

#### 인덱스 : INDEX
- **시퀀스 내의 값들에 대한 고유한 번호**로, 각 값의 **위치를 식별**하는 데 사용되는 숫자

- 음수 인덱스 또한 제공

**index 예시**

|         "    	|      h    	|      e    	|      l    	|      l    	|      o    	|     "    	|
|-------------:|:---------:|:---------:|:---------:|:---------:|:---------:|----------|
|     index    	|      0    	|      1    	|      2    	|      3    	|      4    	|          	|
|     index    	|     -5    	|     -4    	|     -3    	|     -2    	|     -1    	|          	|

#### 슬라이싱 : `slicing`

**시퀀스의 일부분을 선택하여 추출**하는 작업

> 시작 인덱스**(이상)**와 끝 인덱스**(미만)**를 지정하여 **해당 범위의 값을 포함하는 새로운 시퀀스를 생성**
```python
my_str = 'hello'
my_str[2:4]
# ll
```
```python
my_str = 'hello'
my_str[:3]
# hel
```
```python
my_str = 'hello'
my_str[3:]
# lo
```
- Step 지정
```python
my_str = 'hello'
my_str[0:5:2]
# hlo
```
```python
my_str = 'hello'
my_str[::-1]
# olleh
```
**문자열은 불변 (변경 불가): 불변 객체**
```python
my_str = 'hello'

# TypeError: 'str' object does not support item assignment
my_str[1] = 'z'
```

---

#### List : 리스트
여러 개의 값을 순서대로 저장하는 **변경 가능한 시퀀스 자료형**

### 리스트 표현

- **0개 이상의 객체를 포함**하며 데이터 목록을 저장

- 대괄호(`[]`)로 표기

- 데이터는 **어떠한 자료형도 저장할 수 있음**

```python
my_list_1 = []

my_list_2 = [1, 'a', 3, 'b', 5]

my_list_3 = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
```
- **특징**
```python
my_list = [1, 'a', 3, 'b', 5]

# 인덱싱
print(my_list[1])  # a

# 슬라이싱
print(my_list[2:4])  # [3, 'b']
print(my_list[:3])  # [1, 'a', 3]
print(my_list[3:])  # ['b', 5]
print(my_list[0:5:2])  # [1, 3, 5]
print(my_list[::-1])  # [5, 'b', 3, 'a', 1]

# 길이
print(len(my_list))  # 5
```

- **중첩된 리스트에 접근**
```python
my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
print(len(my_list))  # 5
print(my_list[4][-1])  # !!!
print(my_list[-1][1][0])  # w
```

- **List는 가변 객체
```python
my_list = [1, 2, 3]
my_list[0] = 100

print(my_list)  # [100, 2, 3]
```

---

#### Tuple : 튜플
여러 개의 값을 순서대로 저장하는 **변경 불가능한 시퀀스 자료형**
- **0개 이상의 객체를 포함**하며 데이터 목록을 저장

- 소괄호(`()`)로 표기

- 데이터는 **어떠한 자료형도 저장할 수 있음**

```python
my_tuple_1 = ()

my_tuple_2 = (1,) # 요소가 한 개인 튜플을 제작할 때 마지막에 ',' 첨부

my_tuple_3 = (1, 'a', 3, 'b', 5)
```

- **특징**
```python
my_tuple = (1, 'a', 3, 'b', 5)

# 인덱싱
print(my_tuple[1])  # a

# 슬라이싱
print(my_tuple[2:4])  # (3, 'b')
print(my_tuple[:3])  # (1, 'a', 3)
print(my_tuple[3:])  # ('b', 5)
print(my_tuple[0:5:2])  # (1, 3, 5)
print(my_tuple[::-1])  # (5, 'b', 3, 'a', 1)

# 길이
print(len(my_tuple))  # 5
```

- **튜플은 불변 (변경 불가)**
```python
my_tuple = (1, 'a', 3, 'b', 5)

# TypeError: 'tuple' object does not support item assignment
my_tuple[1] = 'z'
```
- **용도**
    - 튜플의 **불변 특성을 사용한 안전하게 여러 개의 값을 전달, 그룹화, 다중 할당** 등

    - 개발자가 직접 사용하기 보다 **‘파이썬 내부 동작’**에서 주로 사용됨

---

#### Range
연속된 정수 시퀀스를 생성하는 **변경 불가능한 자료형**
- **`range(시작 값, 끝 값, 증가 값)`**

- `range(n)`
    - 0부터 n-1까지의 숫자의 시퀀스

- `range(n, m)`
    - n부터 m-1까지의 숫자 시퀀스

- **특징**

    - 증가 값이 없으면 1씩 증가

    - 증가 값이 음수이면 감소 / 증가 값이 양수이면 증가

    - 증가 값이 0이면 에러  

    - 증가 값이 음수이면 시작 값이 끝 값보다 커야 함

    - 증가 값이 양수이면 시작 값이 끝 값보다 작아야 함

---

### 3. Non-Sequence Types  


#### Dict : 딕셔너리

- **key - value 쌍**으로 이루어진 **순서와 중복이 없는 변경 가능한 자료형**

    - **몇번째 요소와 같은 순서 없음: 인덱스가 없음.**

**딕셔너리 표현**

- **key**는 **변경 불가능한 자료형만 사용 가능 *(str, int, float, tuple, range …)***

- **value**는 **모든 자료형 사용 가능**

- 중괄호(`{}`)로 표기

**리스트와의 검색 차이점:**

- 리스트는 특정한 정보를 찾으려면 정보를 순차적으로 탐색해야 함 (O(N))

- **딕셔너리는 키에 바로 접근하기에 정보 찾는 속도가 빠름**

```python
my_dict = {'apple': 12, 'list': [1, 2, 3]}
print(my_dict['apple'])  # 12
print(my_dict['list'])  # [1, 2, 3]

# 추가
my_dict['banana'] = 50
print(my_dict) # {'apple': 12, 'list': [1, 2, 3], 'banana': 50}

# 변경
my_dict['apple'] = 100
print(my_dict) # {'apple': 100, 'list': [1, 2, 3], 'banana': 50}
```

---

#### Set : 세트

- 순서와 중복이 없는 변경 가능한 자료형


**세트 표현**
- 수학에서의 집합과 동일한 연산 처리 가능

- 중괄호(`{}`)로 표기

```python
my_set_1 = {1, 2, 3}
my_set_2 = {3, 6, 9}

# 합집합
print(my_set_1 | my_set_2)  # {1, 2, 3, 6, 9}

# 차집합
print(my_set_1 - my_set_2)  # {1, 2}

# 교집합
print(my_set_1 & my_set_2)  # {3} 
```

---

### 4. Other Types
#### None
파이썬에서 ‘**값이 없음’을 표현**하는 자료형
- 값이 없는 게 아님!!!!!!

---

#### Boolean
- 참(True)과 거짓(False)을 표현하는 자료형

- 비교 / 논리 연산의 평가 결과로 사용됨

- 주로 조건 / 반복문과 함께 사용
```python
bool_1 = True
bool_2 = False

print(bool_1)  # True
print(bool_2)  # False
print(3 > 1)  # True
print('3' != 3)  # True
```
---
### 반복 가능한 객체 `iterable`

- **반복문에서 순회할 수 있는 객체** (**sequence** 객체 뿐만 아니라 **dict, set** 등도 포함)
---

## Collection
- 여러 개의 항목 또는 요소를 담는 자료 구조

- **str, list, tuple, set, dict |** ***range는 없음***

### 컬렉션 정리

|     컬렉션    	|     변경 가능 여부    |     순서 여부    |          	|
|:-------------:|:---------------------:|:----------------:|:--------:|
|     str     |          X          |         O        	|  시퀀스  	|
|     list     |         O        	|         O        	|  시퀀스  	|
|     tuple   	|          X          |         O        	|  시퀀스  	|
|     dict    	|          O         |         X        | 비시퀀스 	|
|      set     	|          O        	|         X        	| 비시퀀스 	|

#### 불변과 가변의 차이 (1/2)
```python
my_str = 'hello'
# TypeError: 'str' object does not support item assignment
my_str[0] = 'z'

my_list = [1, 2, 3]
my_list[0] = 100
# [100, 2, 3]
print(my_list) 
```
- 가변은 메모리 주소를 가져오는 것임 (값이 아닌, 주소를 바꾸는 것)

    - (리스트 내의 값들은 사실 값이 아니라 값이 담긴 메모리 주소를 갖고 있는 것이기에 메모리 주소를 바꾸는 것을 통해 변할 수 있음)

- 불변은 통째로 메모리 주소를 갖고 있기에 부분적으로 바꿀 수 없음.

---

## Functions : 함수
#### 개요

- 특정 작업을 수행하기 위한 **재사용 가능한 코드 묶음**

#### 함수를 사용하는 이유

- 두 수의 합을 구하는 함수를 정의하고 사용함으로써 **코드의 중복을 방지**

- **재사용성**이 높아지고, 코드의 **가독성과 유지보수성 향상**

### 함수 구조
```python
# 함수 정의
def greet(name):
    """입력된 이름(name) 값에
    인사를 하는 메세지('Hello, ')를 만드는 함수 (Docstring)
    """
    message = 'Hello, ' + name
    return message

# 함수 호출 및 반환 값 할당
result = greet('Alice')
print(result)
```
#### 함수 정의(정의)

- 함수 정의는 `def` 키워드로 시작

- def 키워드 이후 함수 이름 작성

- 함수 이름은 **어떤 역할을 하는지 알 수 있도록 (동사)**

- **괄호안에 매개변수**를 정의할 수 있음

- 매개변수(parameter)는 **함수에 전달되는 값**을 나타냄

- 함수는 **한 가지 역할**만 할 수 있도록 구성

#### 함수 body

- 콜론(`:`) 다음에 들여쓰기 된 코드 블록

- 함수가 실행 될 때 수행되는 코드를 정의

- **Docstring**은 함수 body 앞에 선택적으로 작성 가능한 함수 설명서

#### 함수 반환 값

- 함수는 필요한 경우 결과를 반환할 수 있음

- `return` 키워드 이후에 **반환할 값을 명시**

- `return` 문은 함수의 실행을 종료하고, 결과를 호출 부분으로 반환

- `return` 밑에 코드를 쓰면, 작동되지 않음

- `return` 을 쓰지 않으면 **파이썬이 알아서 None을 반환**해 정상 종료할 수 있도록 함

    > - 출력과 리턴은 다름
    > - 리턴은 반환되는 값이 있고, **할당할 수 있음**
    > - 출력은 반환되는 값이 없고 그저 출력할 뿐임.  
  

#### 함수 호출

- 함수를 사용하기 위해서는 호출이 필요

- 함수의 이름과 소괄호를 활용해 호출

- 필요한 경우 **인자(argument)를 전달**해야 함

- 호출 부분에서 **전달된 인자는 함수 정의 시 작성한 매개변수에 대입**됨

---

### 매개변수와 인자

#### 매개변수 `parameter`

- 함수를 **정의**할 때, **함수가 받을 값**을 나타내는 변수
    - 위치에 대한 기능을 할 뿐이지, 특별한 기능을 수행하지는 않음.

#### 인자 `argument`

- 함수를 **호출**할 때, **실제로 전달되는 값**

```python
def add_numbers(x, y): # x와 y는 매개변수(parameter)
    result = x + y
    return result

a = 2
b = 3
sum_result = add_numbers(a, b) # a와 b는 인자(argument)
print(sum_result)
```

### 인자의 종류
#### 1. Positional Arguments (위치 인자)

- 함수 **호출 시 인자의 위치에 따라 전달되는 인자**

- **위치 인자는 함수 호출 시 반드시 값을 전달해야 함 (누락되면 안 됨)**
```python
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')

greet('Alice', 25) # 안녕하세요, Alice님! 25살이시군요
```
#### 2. Default Argument Values (기본 인자 값)
- 함수 정의에서 **매개변수에 기본 값을 할당**하는 것

- 함수 호출 시 **인자를 전달하지 않으면, 기본값이 매개변수에 할당**됨

    - 위치 인자에서 값이 누락되면 오류가 발생하는 것을 보완
```python
def greet(name, age=30):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet('Bob') # 안녕하세요, Bob님! 30살이시군요.
greet('Charlie', 40) # 안녕하세요, Charlie님! 40살이시군요.
```

#### 3. Keyword Arguments (키워드 인자)

- 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자

- **매개변수와 인자의 위치를 일치시키지 않고, 특정 매개변수에 값을 할당**할 수 있음

- 인자의 **순서는 중요하지 않으며, 인자의 이름을 명시하여 전달**

- **단, 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함**

```python
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet(name='Dave', age=35)  # 안녕하세요, Dave님! 35살이시군요.
greet(age=35, 'Dave')  #  positional argument follows keyword argument
```

#### 4. Arbitrary Argument Lists (임의의 인자 목록)

- **정해지지 않은 개수의 인자를 처리**하는 인자

- 함수 정의 시 매개변수 앞에 **`‘*’`**를 붙여 사용하며, **여러 개의 인자를 tuple로 처리**
```python
def calculate_sum(*args):
    print(args)
    total = sum(args)
    print(f'합계: {total}')


"""
(1, 2, 3)
합계: 6
"""
calculate_sum(1, 2, 3)
```

#### 5. Arbitrary Keyword Argument Lists (임의의 키워드 인자 목록)

- **정해지지 않은 개수의 키워드 인자를 처리**하는 인자

- 함수 정의 시 매개변수 앞에 `‘**’`를 붙여 사용하며, 여러 개의 인자를 **dictionary로 묶어 처리**

```python
def print_info(**kwargs):
    print(kwargs)

print_info(name='Eve', age=30) # {'name': 'Eve', 'age': 30}
```
### 함수 인자 권장 작성순서

- **위치 -> 기본 -> 가변 -> 가변 키워드**

- 호출 시 인자를 전달하는 과정에서 혼란을 줄일 수 있도록 함

- 단, 모든 상황에 적용되는 절대적인 규칙은 아니며, 상황에 따라 유연하게 조정될 수 있음

```python
def func(pos1, pos2, default_arg='default', *args, **kwargs):
    print('pos1:', pos1) # 1
    print('pos2:', pos2) # 2
    print('default_arg:', default_arg) # 3
    print('args:', args) # (4, 5, 6)
    print('kwargs:', kwargs) # {key1='value1', key2='value2'}

func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')

"""
pos1: 1
pos2: 2
default_arg: 3
args: (4, 5, 6)
kwargs: {'key1': 'value1', 'key2': 'value2'}
"""
```
---

### 재귀 함수
함수 내부에서 자기 자신을 호출하는 함수
```python
def factorial(n):
    # 종료 조건 (base Case): n이 0이면 1을 반환
    if n == 0:
        return 1
    else:
        # 재귀 호출: n과 n-1의 팩토리얼을 곱한 결과를 반환
        return n * factorial(n - 1) # 자기 자신을 또 호출함
# 팩토리얼 계산 예시
print(factorial(5))  # 120

# 자기 자신을 다시 호출할 때 n을 그대로 두면, 무한 순회하니 주의
# 종료 조건을 명확히 하고, 종료 조건을 향해 나아갈 수 있도록!
```
- factorial 함수는 **자기 자신을 재귀적으로 호출**하여 입력된 숫자 n의 팩토리얼을 계산

- 재귀 호출은 **n이 0이 될 때까지 반복**되며, **종료 조건을 설정**하여 **재귀 호출이 멈추도록** 함

- 재귀 호출의 결과를 이용하여 **문제를 작은 단위의 문제로 분할하고**, **분할된 문제들의 결과를 조합하여 최종 결과를 도출**

#### 재귀 함수 특징

- **특정 알고리즘 식을 표현**할 때 **변수의 사용이 줄어들며, 코드의 가독성이 높아짐 (항상 X)**
- 1개 이상의 **base case(**종료되는 상황)가 존재하고, **수렴하도록 작성**

#### 재귀 함수를 사용하는 이유

- 문제의 **자연스러운 표현**
    - 복잡한 문제를 **간결하고 직관적으로 표현** 가능
- 코드 **간결성**
    - **상황에 따라** 반복문보다 알고리즘 코드가 **더 간결하고 명확해질 수 있음**
- **수학적 문제 해결**
    - 수학적 정의가 재귀적으로 표현되는 경우, 직접적인 구현 가능

#### 재귀 함수 활용 시 기억해야 할 것

1. **종료 조건을 명확히**

2. **반복되는 호출이 종료 조건을 향하도록**

--- 

### 내장 함수
- 파이썬이 **기본적으로 제공하는 함수** (별도의 import 없이 바로 사용 가능)

- **내장 함수 ↔ 함수** (외장 함수가 아님)

```python
# 자주 사용되는 내장 함수 예시
numbers = [1, 2, 3, 4, 5]

print(len(numbers))  # 5 길이
print(max(numbers))  # 5 최대값
print(min(numbers))  # 1 최소값
print(sum(numbers))  # 15 합계
print(sorted(numbers, reverse=True))  # [5, 4, 3, 2, 1] 정렬 (기본은 오름차순)
```
--- 
### map( )
> map(function(함수), iterable(반복 가능한 객체)) 

- 순회 가능한 **데이터구조(iterable)**의 **모든 요소에 함수를 적용**하고, 그 **결과를 map object로 반환**

- **요소 하나하나에 함수를 적용하기에, 반복(순회) 가능한 객체를 대입해야 함**

- **확장성:** 함수 자리에 내가 만든 함수도 적용이 가능함

```python
numbers = [1, 2, 3]
result = map(str, numbers)

print(result)  # <map object at 0x00000239C915D760> map 덩어리로 반환
print(list(result))  # ['1', '2', '3']
```
---
### zip(*iterable)
> 임의의 iterable(반복이 가능한 것)을 모아 튜플을 원소로 하는 zip object를 반환
```python
girls = ['jane', 'ashley']
boys = ['peter', 'jay']

pair = zip(girls, boys)

print(pair)  # <zip object at 0x000001C76DE58700> zip object로 반환
print(list(pair))  # [('jane', 'peter'), ('ashley', 'jay')]
```
- **동시 조회**
```python
# 여러 리스트 동시 조회

kr_scores = [10, 20, 30, 50]
math_scores = [20, 40, 50, 70]
en_scores = [40, 20, 30, 50]

for student_scores in zip(kr_scores, math_scores, en_scores):
    print(student_scores)

"""
(10, 20, 40)
(20, 40, 20)
(30, 50, 30)
(50, 70, 50)
"""
```
```python
# 2차원 리스트의 같은 column 요소를 동시에 조회할 때

scores = [
    [10, 20, 30],
    [40, 50, 39],
    [20, 40, 50],
]

for score in zip(*scores):
    print(score)

"""
(10, 40, 20)
(20, 50, 40)
(30, 39, 50)
"""
```
---
### 함수와 Scope
**함수는 코드 내부에 `local scope`를 생성하며, 그 외의 공간인 `global scope`로 구분**

### 범위와 변수 관계

- **scope**
    - **global scope (전역)**  : **코드 어디에서든 참조**할 수 있는 공간

    - **local scope (지역**) : 함수가 만든 scope (**함수 내부에서만 참조 가능**)

- **variable**
    - **global variable** : global scope에 정의된 변수

    - **local variable** : local scope에 정의된 변수

```python
def func():
    num = 20
    print('local', num)  # local 20

func()

print('global', num)  # NameError: name 'num' is not defined

# num은 local scope에 존재하기 때문에 global에서 사용할 수 없음
```
### 변수 수명주기(lifecycle)

- 변수의 수명주기는 변수가 선언되는 위치와 스코프에 따라 결정됨
1. **built-in scope**
    - **파이썬이 실행된 이후부터 영원히 유지** (built in function)
2. **global scope**
    - 모듈이 **호출된 시점 이후 혹은 인터프리터가 끝날 때까지** 유지
3. **local scope**
    - **함수가 호출될 때 생성되고, 함수가 종료될 때까지** 유지

### 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)들은 특정한 이름공간(namespace)에 저장되어 있음

- 아래와 같은 순서로 이름을 찾아 나가며, LEGB Rule이라고 부름

    1. Local scope : 지역 범위(현재 작업 중인 범위)

    2. Enclosed scope : 지역 범위 한 단계 위 범위 (함수 안의 함수일 때)

    3. Global scope : 최상단에 위치한 범위

    4. Built-in scope : 모든 것을 담고 있는 범위 (정의하지 않고 사용할 수 있는 모든 것)

- 함수 내에서는 바깥 Scope의 변수에 접근 가능하나 수정은 할 수 없음

```python
a = 1
b = 2


def enclosed():
    a = 10
    c = 3

    def local(c):
        print(a, b, c) # 10 2 500

    local(500)
    print(a, b, c) # 10 2 3


enclosed()
print(a, b) # 1 2

# 지역 영역에서부터 요소가 없을 때마다 확장해 나가면서 해답을 찾기: 매개변수 헷갈리지 말기
# 글로벌과 같은 바깥 영역에서는 안쪽 지역변수에서 값을 찾을 필요 없음
```

### `global` 키워드

- **변수의 스코프를 전역 범위로 지정**하기 위해 사용

- 일반적으로 **함수 내에서 전역 변수를 수정하려는 경우**에 사용
```python
num = 0 # 전역 변수


def increment():
    global num # num를 전역 변수로 선언
    num += 1


print(num) # 0

increment()
print(num) # 1
```
#### 주의 사항
- global 키워드 선언 전에 참조 불가
```python
num = 0


def increment():
    # SyntaxError: name 'num' is used prior to global declaration
    print(num) # global 선언 전에 참조 X
    global num
    num += 1
```

- 매개변수에는 global 키워드 사용 불가
```python
num = 0


def increment(num): # 매개변수 X
    # "num" is assigned before global declaration
    global num
    num += 1
```

### lambda 표현식
- 익명 함수를 만드는 데 사용되는 표현식

- 한 줄로 간단한 함수를 정의

- 함수를 매개변수로 전달하는 경우에도 유용하게 활용

```python
lambda 매개변수: 표현식 
```
- `lambda` 키워드
    - 람다 함수를 선언하기 위해 사용되는 키워드입니다.

- 매개변수
    - 함수에 전달되는 매개변수들
    - 여러 개의 매개변수가 있을 경우 쉼표로 구분

- 표현식
    - 함수의 실행되는 코드 블록으로, 결과값을 반환하는 표현식으로 작성

```python
# 람다 함수 미적용 코드
def addition(x, y):
    return x + y

result = addition(3, 5)
print(result) # 8

'-----------------------------------'

# 람다 함수 적용 코드
addition = lambda x, y: x + y

result = addition(3, 5)
print(result) # 8
```
```python
numbers = [1, 2, 3, 4, 5]
def square(x):
    return x**2

# lambda 미사용
squared1 = list(map(square, numbers))
print(squared1)  # [1, 4, 9, 16, 25]

# lambda 사용
squared2 = list(map(lambda x: x**2, numbers))
print(squared2)  # [1, 4, 9, 16, 25]
```
---
## Packing & Unpacking

### Packing `패킹`

- 여러 개의 값을 하나의 변수에 묶어서 담는 것

#### 패킹 예시

- 변수에 담긴 값들은 **튜플(tuple**) 형태로 묶임
```python
packed_values = 1, 2, 3, 4, 5
# 1개의 변수에 여러개의 값을 지정: 1개의 튜플로 묶어서 할당

print(packed_values)  # (1, 2, 3, 4, 5)
```

#### `‘*’`을 활용한 패킹

- `b`는 **남은 요소들을 리스트로 패킹하여 할당**
```python
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers

print(a) # 1
print(b) # [2, 3, 4] # 남은 요소들은 리스트로 할당됨
print(c) # 5
```
---
### Unpacking `언패킹`

- 패킹된 변수의 값을 개별적인 변수로 분리하여 할당하는 것

#### 언패킹 예시

- 튜플이나 리스트 등의 객체의 요소들을 개별 변수에 할당
```python
packed_values = 1, 2, 3, 4, 5

a, b, c, d, e = packed_values
print(a, b, c, d, e)  # 1 2 3 4 5

# 개수 안 맞으면: a, b, c, d, e, f = packed_values
```
#### `‘*’`을 활용한 언패킹

- **`*`** 는 리스트의 요소를 언패킹하여 인자로 전달
```python
def my_function(x, y, z):
    print(x, y, z)

names = ['alice', 'jane', 'peter']
my_function(*names) # alice jane peter
# 인자로 넣을 때 '*'는 언패킹의 의미를 가짐
```

#### `‘**’`을 활용한 언패킹

- **`**`** 는 딕셔너리의 키-값 쌍을 함수의 키워드 인자로 언패킹
```python
def my_function(x, y, z):
    print(x, y, z)


my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict)  # 1 2 3

# 인자로 넣을 때 '**'는 언패킹의 의미를 가짐
# 딕셔너리로 할 때는, 매개 변수와 key가 같아야 함 
```
---
### `*` 패킹 / 언패킹 연산자 정리

- `‘*’`
    - **패킹 연산자**로 사용될 때, **여러 개의 인자를 하나의 튜플로 묶음**
    - **언패킹 연산자**로 사용될 때, **시퀀스나 반복 가능한 객체를 각각의 요소로 언패킹하여 함수의 인자로 전달**
- `‘**’`
    - **언패킹 연산자**로 사용될 때, **딕셔너리의 키-값 쌍을 언패킹하여 함수의 키워드 인자로 전달**
---
## Method - 매서드

- **객체에 속한 함수**

- **객체의 상태를 조작**하거나 **동작을 수행**

### 메서드 특징

- 메서드는 **클래스(class) 내부에 정의**되는 **함수**
  
- **클래스**는 '파이썬에서 타입을 표현하는 방법’이며 이미 은연중에 사용해왔음
  
- 예를 들어 help 함수를 통해 str을 호출해보면 class 였다는 것을 확인 가능

> - **메서드**는 어딘가(클래스)에 속해 있는 함수이며,  
> 각 **데이터 타입 별로 다양한 기능을 가진 메서드가 존재**

#### 매서드 호출
```python
'hello'.capitalize() 
# 객체.함수이름() : 객체 안에 속한 함수
```
## 시퀀스 데이터 구조

### 문자열 
#### 문자열 조회/탐색 및 검증 메서드
| 메서드 | 설명 |
|------|------|
| **s.find(x)**	| x의 첫 번째 위치를 반환. 없으면, -1을 반환 |
| **s.index(x)** | x의 첫 번째 위치를 반환. 없으면, 오류 발생 |
| **s.isupper()** | 대문자 여부 |
| **s.islower()** | 소문자 여부 |
| **s.isalpha()** | 알파벳 문자 여부 (* 단순 알파벳이 아닌 유니코드 상 Letter, 한국어도 포함) |

#### 문자열 조작 메서드 (새 문자열 반환)

- **str은 불변객체**이기 때문에: 새 문자열로 반환함.

| 메서드 | 설명 |
|------|------|
| **s.replace(old, new[,count])** |	바꿀 대상 글자를 새로운 글자로 바꿔서 반환 [,count]는 선택인자 (횟수만큼 바꿈) |
| **s.strip([chars])** | 공백이나 특정 문자를 제거
| **s.split(sep=None, maxsplit=-1)**	| 공백이나 특정 문자를 기준으로 분리 |
| **'separator'.join(iterable)** | 구분자로 iterable(반복 가능한) 문자열을 연결한 문자열을 반환 |
| **s.capitalize()** | 가장 첫 번째 글자를 대문자로 변경 |
| **s.title()** | 문자열 내 띄어쓰기 기준으로 각 단어의 첫 글자는 대문자로, 나머지는 소문자로 변환 |
| **s.upper()** | 모두 대문자로 변경 |
| **s.lower()**	| 모두 소문자로 변경 |
| **s.swapcase()** | 대 ↔ 소문자 서로 변경 |

### 리스트
#### ### 리스트 값 추가 및 삭제 메서드

- List는 **가변 객체**이기에 원본 객체에 변화를 가할 수 있음

| 메서드 | 설명 |
|------|------|
| **L.append(x)** | 리스트 마지막에 항목 x를 추가
| **L.extend(m)** | Iterable m의 모든 항목들을 리스트 끝에 추가 (+=과 같은 기능) |
| **L.insert(i, x)** |리스트 인덱스 i에 항목 x를 삽입 |
| **L.remove(x)** | 리스트 가장 왼쪽에 있는 항목(첫 번째) x를 제거, 항목이 존재하지 않을 경우 ValueError |
| **L.pop()** | 리스트 가장 오른쪽에 있는 항목(마지막)을 반환 후 제거 |
| **L.pop(i)** | 리스트의 인덱스 i에 있는 항목을 반환 후 제거 |
| **L.clear()** | 리스트의 모든 항목 삭제 |

#### 리스트 탐색 및 정렬 메서드
| 문법 | 설명 |
|------|------|
| **L.index(x)** | 리스트에 있는 항목 중 가장 왼쪽에 있는 항목 x의 인덱스를 반환 |
| **L.count(x)** | 리스트에서 항목 x의 개수를 반환 |
| **L.reverse()** | 리스트의 순서를 역순으로 변경 (정렬 X) |
| **L.sort()** | 리스트를 정렬 (매개변수 이용 가능) |

## 비시퀀스 데이터 구조
### 세트 `set`

- 고유한 항목들의 정렬되지 않은 컬렉션

#### 세트 메서드
| 메서드 | 설명 |
|-------|-------|
| **s.add(x)** | 세트 s에 항목 x를 추가. 이미 x가 있다면 변화 없음 |
| **s.clear()** | 세트 s의 모든 항목을 제거 |
| **s.remove(x)** | 세트 s에서 항목 x를 제거. 항목 x가 없을 경우 Key error |
| **s.pop()** | 세트 s에서 랜덤하게 항목을 반환하고, 해당 항목을 제거 |
| **s.discard(x)** | 세트 s에서 항목 x를 제거 |
| **s.update(iterable)** | 세트 s에 다른 iterable 요소를 추가 |

#### 세트의 집합 메서드
| 메서드 | 설명 | 연산자 |
|-------|-------|-------|
| **set1.difference(set2)** | set1에는 들어있지만 set2에는 없는 항목으로 세트를 생성 후 반환	| **set1 – set2** |
| **set1.intersection(set2)** | set1과 set2 모두 들어있는 항목으로 세트를 생성 후 반환 | **set1 & set2** |
| **set1.issubset(set2)** | set1의 항목이 모두 set2에 들어있으면 True를 반환 | **set1 <= set2** |
| **set1.issuperset(set2)** | set1가 set2의 항목을 모두 포함하면 True를 반환	 | **set1 >= set2** |
| **set1.union(set2**) | set1 또는 set2에(혹은 둘 다) 들어있는 항목으로 세트를 생성 후 반환 | **set1** |

### 딕셔너리 `dictionary`

- 고유한 항목들의 정렬되지 않은 컬렉션

#### 딕셔너리 메서드
| 메서드 | 설명 |
|------|------|
| **D.clear()** | 딕셔너리 D의 모든 키/값 쌍을 제거 |
| **D.get(k)** | 키 k에 연결된 값을 반환 (키가 없으면 None을 반환) |
| **D.get(k, v)** | 키 k에 연결된 값을 반환하거나 키가 없으면 기본 값으로 v를 반환 |
| **D.keys()** | 딕셔너리 D의 키를 모든 객체를 반환 |
| **D.values()** | 딕셔너리 D의 값을 모든 객체를 반환 |
| **D.items()** | 딕셔너리 D의 키/값 쌍을 모은 객체를 반환 |
| **D.pop(k)** | 딕셔너리 D에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 오류) | 
| **D.pop(k, v)** | 딕셔너리 D에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 v를 반환) |
| **D.setdefault(k)** |딕셔너리 D에서 키 k와 연결된 값을 반환 |
| **D.setdefault(k, v)** | 딕셔너리 D에서 키 k와 연결된 값을 반환. k가 D의 키가 아니면 값 v와 연결한 키 k를 D에 추가하고 v를 반환 |
| **D.update(other)** | other 내 각 키에 대해 D에 있는 키면 D에 있는 그 키의 값을 other에 있는 값으로 대체. other에 있는 각 키에 대해 D에 없는 키면 키/값 쌍을 D에 추가 |

## 참고
### 문자 유형 판별 메서드
- `isdecimal()` : 가장 엄격
    - 문자열이 모두 숫자 문자(0~9)로만 이루어져 있어야 True

- `isdigit()`
    - isdecimal()과 비슷하지만, 유니코드 숫자도 인식 ('①’ 도 숫자로 인식)

- `isnumeric()` : 가장 느슨
    - isdigit()과 유사하지만, 몇 가지 추가적인 유니코드 문자들을 인식(분수, 지수, 루트 기호도 숫자로 인식)

| isdecimal() | isdigit() | isnumeric() |	예시 |
|------|------|------|------|
| True | True | True | "038", "੦੩੮", "０３８" |
| **False** | True | True | "⁰³⁸", "🄀⒊⒏", "⓪③⑧" |
| **False** | **False**	| True | "⅛⅘", "ⅠⅢⅧ", "⑩⑬㊿", "壹貳參" |
| **False** | **False** | **False** | "abc", "38.0", "-38" (float 안 됨) |

---
## Module
### 모듈 Module
- 한 파일로 묶인 변수와 함수의 모음

- 특정한 기능을 하는 코드가 작성된 파이썬 파일(`.py`)

--- 

#### 모듈 가져오기
**`import` 문 사용**  
```python
import math 
# import를 사용할 때는 이후에 모델명을 붙여야 함

print(math.sqrt(4))
```

**`from` 절 사용**
```python
from math import sqrt
# from을 사용할 때는 이후에 모델명을 붙일 필요 없음

print(sqrt(4))
```
> - **`from`절 사용 시 무슨 모델의 함수인지, 자체 제작한 모델의 함수인지 구분하기 어려움**
> - **`import` 문 사용해서 작성하는 것을 추천**
---
#### 모듈 사용하기
`'.'` (dot) 연산자

- "점의 왼쪽 객체에서 점의 오른쪽 이름을 찾아라“ 라는 의미
```python
# 모듈명.변수명
print(math.pi)

# 모듈명.함수명
print(math.sqrt(4))

# math 객체에서 sqrt이름을 찾아라
```
---
#### 주의 사항
- 서로 다른 모듈이 **같은 이름의 함수를 제공할 경우 문제 발생**

- 마지막에 `import`된 이름으로 대체됨

#### as 키워드
- as 키워드를 사용하여 **별칭(alias)을 부여**

    - 두 개 이상의 모듈에서 **동일한 이름의 변수, 함수 클래스 등을 가져올 때 발생하는 이름 충돌 해결**

```python
from math import sqrt
from my_math import sqrt as my_sqrt

sqrt(4)
my_sqrt(4) # my_math에 있는 sqrt를 가져온 것
```
---
## 파이썬 표준 라이브러리
파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음

### 패키지 `Package`

- **연관된 모듈들을 하나의 디렉토리에 모아 놓은 것**
    - .py들을 하나의 **폴더에 모아놓은 것이 패키지**
    - 이런 **패키지와 모듈들을 다 모으면 라이브러리**
        
        라이브러리 > 패키지 > 모듈

#### PSL 내부 패키지

- **설치 없이** 바로 **`import`하여 사용**

#### 외부 패키지

- **`pip`를 사용하여 설치 후 `import` 필요**

--- 
### pip `파이썬 패키지 관리자`

- **외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템**
- PyPI(Python Package Index)에 저장된 외부 패키지들을 설치
    
    > https://pypi.org/
    > 

### 패키지 설치 (중요)

- **최신 버전 / 특정 버전 / 최소 버전을 명시하여 설치할 수 있음**
```python
$ pip install SomePackage # 최신 버전

$ pipinstallSomePackage==1.0.5 # 특정 버전

$ pip install SomePackage>=1.0.4 # 최소 버전 명시

$ pip list # 설치된 패키지 목록 확인
```
**requests 외부 패키지 설치 및 사용 예시**
```python
# 외부 API에게 자료를 요청할 때 사용
$ pip install requests 

import requests

url = 'https://random-data-api.com/api/v2/users'
response = requests.get(url).json()
# requests의 .json이 딕셔너리로 전환해줌: 원래는 문자열임
# 요청, 응답, 변환 다 해주는 코드니 기억하기

print(response)
```
### 패키지 사용 목적

- 모듈들의 이름공간을 구분하여 충돌을 방지
- 모듈들을 효율적으로 관리하고 재사용할 수 있도록 돕는 역할

## 제어문
- 코드의 **실행 흐름을 제어**하는 데 사용되는 구문

- **조건에 따라 코드 블록을 실행**하거나 **반복적으로 코드를 실행**

### 조건문
- `if`  
  
- `elif`  
  
- `else`
  
**복수 조건문**

- 조건식을 동시에 검사하는 것이 아니라 순차적으로 비교
```python
dust = 35

if dust > 150:
    print('매우 나쁨')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```

**중첩 조건문**
```python
dust = 480

if dust > 150:
    print('매우 나쁨')
    """
    중첩 조건문
    """
    if dust > 300:
        print('위험해요! 나가지 마세요!')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```

### 반복문
- **주어진 코드 블록을 여러 번 반복해서 실행**하는 구문

  1. 특정 작업을 **반복적**으로 수행
   
  2. 주어진 조건이 **참인 동안 반복해서 실행**
   
#### `for`
    - 특정 작업을 반복적으로 수행
    - 종료 조건이 명확함
  
#### for 문 원리

- 리스트 내 첫 항목이 반복 변수에 할당되고 코드 블록이 실행
- 다음으로 반복 변수에 리스트의 2번째 항목이 할당되고 코드 블록이 다시 실행
- ... 마지막으로 반복 변수에 리스트의 마지막 요소가 할당되고 코드 블록이 실행

#### - 문자열 순회
- 문자열도 sequence 데이터임
```python
country = 'Korea'

for char in country:
    print(char)

"""
K
o
r
e
a
"""
```

#### - range 순회
- 굳이 list(range(i))로 변환하지 않아도, 반복 가능한 객체로 출력
```python
for i in range(5):
    print(i)

"""
0
1
2
3
4
"""
```

#### - dict 순회
- 기본적으로 dict는 for문 사용시 **key를 뱉어냄**
- 
    - key를 활용해서 value를 출력하자!
  
```python
my_dict = {
    'x': 10,
    'y': 20,
    'z': 30,
}

for key in my_dict:
    print(key)
    print(my_dict[key])
    
"""
x
10
y
20
z
30
"""
```

#### - 인덱스로 리스트 순회
- 리스트의 요소가 아닌 인덱스로 접근하여 해당 요소들을 변경하기
  
```python
numbers = [4, 6, 10, -8, 5]

for i in range(len(numbers)):
    numbers[i] = numbers[i] * 2

print(numbers) # [8, 12, 20, -16, 10]
```

#### - enumerate(iterable, start=0)
- iterable 객체의 각 요소에 대해 인덱스와 함께 반환하는 내장함수
```python
fruits = ['apple', 'banana', 'cherry']

for index, fruit in enumerate(fruits):
print(f'인덱스 {index}: {fruit}')

"""
인덱스 0: apple
인덱스 1: banana
인덱스 2: cherry
"""
```

#### `while`
    - 주어진 조건이 참인 동안 반복해서 실행
      - 조건식이 거짓(False)가 될 때 까지 반복
    - 종료 조건이 없다면 무한히 돌아감

```python
a = 0

while a < 3:
    print(a)
    a += 1

print('끝')

"""
0
1 
2 
끝
"""
```

#### 적절한 반복문 활용하기

- **`for`**
    - **반복 횟수가 명확하게 정해져 있는 경우에 유용**
    - 예를 들어 **리스트, 튜플, 문자열 등과 같은 시퀀스 형식의 데이터**를 처리할 때
- **`while`**
    - **반복 횟수가 불명확하거나 조건에 따라 반복을 종료해야 할 때** 유용
    - 예를 들어 **사용자의 입력을 받아서 특정 조건이 충족될 때까지 반복하는 경우**

### ### 반복 제어

- for문과 while은 매 반복마다 본문 내 모든 코드를 실행하지만
때때로 일부만 실행하는 것이 필요할 때가 있음

### 반복문 제어 키워드

- **`break`**
    - 반복을 **즉시 중지**
```python
# break

for i in range(10):
    if i == 5:
        break # 중지
    print(i)  # 0 1 2 3 4
```
- **`continue`**
    - **다음 반복으로 건너뜀**
```python
# continue

for i in range(10):
    if i % 2 == 0:
        continue # 다음 반복으로 
    print(i)  # 1 3 5 7 9
```
```python
# 리스트에서 홀수만 출력하기
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# 현재 반복문의 남은 코드를 건너뛰고 다음 반복으로 넘어감
for num in numbers:
    if num % 2 == 0:
        continue
    print(num)

"""
1
3
5
7
9
"""
```

- **`pass`**
    - 아무런 동작도 **수행하지 않고 넘어감**
```python
# pass

for i in range(10):
    pass  # 아무 작업도 안함 (에러 방지 등)
```
1. 코드 작성 중 미완성 부분
    ◦ 구현해야 할 부분이 나중에 추가될 수 있고, 코드를 컴파일하는 동안 오류가 발생하지 않음
```python
def my_function():
    pass  
```

2. 조건문에서 아무런 동작을 수행하지 않아야 할 때
```python
if condition:
    pass  # 아무런 동작도 수행하지 않음
else:
    # 다른 동작 수행
```

3. 무한 루프에서 조건이 충족되지 않을 때 pass를 사용하여 루프를 계속 진행하는 방법
```python
while True:
    if condition:
        break
    elif condition:
        pass  # 루프 계속 진행
    else:
        print('..')
```

### List Comprehension

- 간결하고 효율적인 리스트 생성 방법

#### List Comprehension 구조
```python
[expression for 변수 in iterable]
list(expression for 변수 in iterable)

# expression: 변수에 할당할 수식
```
```python
[expression for 변수 in iterable if 조건식]
list(expression for 변수 in iterable if 조건식)
```

#### List Comprehension 사용 전/후 비교
```python
# List Comprehension 미사용

numbers = [1, 2, 3, 4, 5]
squared_numbers = []

for num in numbers:
    squared_numbers.append(num**2)

print(squared_numbers)  # [1, 4, 9, 16, 25]


# List Comprehension 사용

numbers = [1, 2, 3, 4, 5]
squared_numbers = [num**2 for num in numbers]

print(squared_numbers)  # [1, 4, 9, 16, 25]
```
```python
# if문 포함
squared_numbers_3 = [num ** 2 for num in numbers if num % 2 == 1]
print(squared_numbers_3)
```
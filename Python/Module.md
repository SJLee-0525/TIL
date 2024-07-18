# Module

## 모듈

### 개요

- 과학자, 수학자가 모든 이론을 새로 만들거나 증명하지 않는 것처럼개발자 또한 프로그램 전체를 모두 혼자 힘으로 작성하는 것은 드문 일
- 이미 다른 프로그래머가 이미 작성해 놓은 수천, 수백만 줄의 코드를 사용하는것은 생산성에서 매우 중요한 일

### 모듈 `Module`

- 한 파일로 묶인 변수와 함수의 모음
- 특정한 기능을 하는 코드가 작성된 파이썬 파일(`.py`)

### 모듈 예시

- math 내장 모듈 (math.py)
- 파이썬이 미리 작성해 둔 수학 관련 변수와 함수가 작성된 모듈
    
    ```python
    **import math**
    
    print(math.pi)  # 3.141592653589793
    
    print(math.sqrt(4))  # 2.0
    ```
    

> 참고 문서 : https://docs.python.org/3/library/math.html
> 

**실행 해보기**

```python
# 실행 해보기 1
**import math**

print(math.pi)

print(math.sqrt(4))
```

## 모듈 활용

**모듈 import**

### 모듈을 가져오는 방법

- `import` 문 사용
    
    ```python
    **import math** 
    # import를 사용할 때는 이후에 모델명을 붙여야 함
    
    print(math.sqrt(4))
    ```
    
- `from` 절 사용
    
    ```python
    **from math import sqrt**
    # from을 사용할 때는 이후에 모델명을 붙일 필요 없음
    
    print(sqrt(4))
    ```
    
- **`from`절 사용 시 무슨 모델의 함수인지, 자체 제작한 모델의 함수인지 구분하기 어려움**
- **`import` 문 사용해서 작성하는 것을 추천**

### 모듈 사용하기

- `'.' (dot)` 연산자
    - "점의 왼쪽 객체에서 점의 오른쪽 이름을 찾아라“ 라는 의미
        
        ```python
        # 모듈명.변수명
        print(math.pi)
        
        # 모듈명.함수명
        print(math.sqrt(4))
        
        **# math 객체에서 sqrt이름을 찾아라**
        ```
        

### 모듈 주의사항

- 서로 다른 모듈이 **같은 이름의 함수를 제공할 경우 문제 발생**
- 마지막에 `import`된 이름으로 대체됨
    
    ```python
    from math import pi, sqrt
    from my_math import sqrt
    ```
    
    ```python
    # 그래서 **모듈 내 모든 요소를 한번에 import 하는 * 표기는 권장하지 않음**
    
    **from math import ***
    ```
    

### `as` 키워드

- as 키워드를 사용하여 **별칭(alias)을 부여**
    - 두 개 이상의 모듈에서 **동일한 이름의 변수, 함수 클래스 등을 가져올 때 발생하는 이름 충돌 해결**
    
    ```python
    **from math import sqrt
    from my_math import sqrt as my_sqrt**
    
    sqrt(4)
    my_sqrt(4) # my_math에 있는 sqrt를 가져온 것
    ```
    

**실행 해보기**

```python
# 실행 해보기 1
**import math**

help(math)
```

```python
# 실행 해보기 2
**import math**

print(math.pi)

print(math.sqrt(4))
```

```python
# 실행 해보기 3
**from math import pi, sqrt**

print(pi)

print(sqrt(4))
```

**사용자 정의 모듈**

### 직접 정의한 모듈 사용하기

1. 모듈 my_math.py 작성
2. 두 수의 합을 구하는 add 함수 작성
3. my_math 모듈 import 후 add 함수 호출

![이미지](https://github.com/ragu6963/TIL/assets/32388270/16905377-6a9c-4ba5-9d3e-0ce5a77da4f1)

## 파이썬 표준 라이브러리

### 파이썬 표준 라이브러리 `Python Standard Library`

- **파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음**

> 참고 문서 : https://docs.python.org/ko/3/library/index.html
> 

### 패키지 `Package`

- **연관된 모듈들을 하나의 디렉토리에 모아 놓은 것**
    - .py들을 하나의 **폴더에 모아놓은 것이 패키지**
    - 이런 **패키지와 모듈들을 다 모으면 라이브러리**
        
        라이브러리 > 패키지 > 모듈
        

### 패키지 사용하기 (1/2)

- 아래와 같은 디렉토리 구조로 작성
- 패키지 3개 : my_package / math, statistics (서브 패키지)
- 모듈 2개 : my_math, tools
- 디렉토리 전체 구조
    
    ```markdown
    📦...
     ┣ 📜sample.py
     ┣ 📂my_package
     ┃ ┣ 📂math
     ┃ ┃ ┗ 📜my_math.py
     ┃ ┣ 📂statistics
     ┃ ┃ ┗ 📜tools.py
    ```
    

![이미지](https://github.com/ragu6963/TIL/assets/32388270/01f0ca51-45b2-4468-8a38-b81c6db14b24)

### 패키지 사용하기 (2/2)

- 각 패키지의 모듈을 `import` 하여 사용하기
    
    ```python
    # sample.py
    
    from my_package.math import my_math
    from my_package.statistics import tools
    
    print(my_math.add(1, 2))  # 3
    print(tools.mod(1, 2))  # 1
    
    ```
    

### PSL 내부 패키지

- **설치 없이** 바로 **`import`하여 사용**

### 외부 패키지

- **`pip`를 사용하여 설치 후 `import` 필요**

### pip `파이썬 패키지 관리자`

- **외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템**
- PyPI(Python Package Index)에 저장된 외부 패키지들을 설치
    
    > https://pypi.org/
    > 

### 패키지 설치 (중요)

- 최신 버전 / 특정 버전 / 최소 버전을 명시하여 설치할 수 있음
    
    ```python
    $ pip install SomePackage # 최신 버전
    
    $ pipinstallSomePackage==1.0.5 # 특정 버전
    
    $ pip install SomePackage>=1.0.4 # 최소 버전 명시
    ```
    

**requests 외부 패키지 설치 및 사용 예시**

```python
**# 외부 API에게 자료를 요청할 때 사용**
$ pip install requests 

import requests

url = 'https://random-data-api.com/api/v2/users'
**response = requests.get(url).json()**
# **requests의 .json이 딕셔너리로 전환해줌**: 원래는 문자열임
# 요청, 응답, 변환 다 해주는 코드니 기억하기

print(response)
```

- **위 방식대로 패키지 설치 시 글로벌에 설치가 됨: 전역 설치**

### 패키지 사용 목적

- 모듈들의 이름공간을 구분하여 충돌을 방지
- 모듈들을 효율적으로 관리하고 재사용할 수 있도록 돕는 역할
### 05 Functions

# Functions

## 함수 `Functions`

### 개요

- 특정 작업을 수행하기 위한 **재사용 가능한 코드 묶음**

### 함수를 사용하는 이유

- 두 수의 합을 구하는 함수를 정의하고 사용함으로써 **코드의 중복을 방지**
- **재사용성**이 높아지고, 코드의 **가독성과 유지보수성 향상**
    
    ```python
    # 두 수의 합을 구하는 코드
    num1 = 5
    num2 = 3
    
    sum_result = num1 + num2
    print(sum_result)
    ```
    
    ```python
    # 두 수의 합을 구하는 함수
    def get_sum(num1, num2):
        return num1 + num2
    
    # 함수 사용하여 결과 출력
    num1 = 5
    num2 = 3
    sum_result = get_sum(num1, num2)
    print(sum_result)
    ```
    

**실행 해보기**

```python
# 실행 해보기 1
num1 = 5
num2 = 3

sum_result = num1 + num2
print(sum_result)
```

```python
# 실행 해보기 2
def get_sum(num1, num2):
    return num1 + num2

num1 = 5
num2 = 3
sum_result = get_sum(num1, num2)
print(sum_result)
```

### 함수의 구조

### 함수 구조

![이미지](https://github.com/ragu6963/TIL/assets/32388270/fe4bb4a9-f88d-43f8-9e6e-915e3c790b48)

### 함수의 정의와 호출 1

- 함수 정의(정의)
    - 함수 정의는 `def` 키워드로 시작
    - def 키워드 이후 함수 이름 작성
    - **괄호안에 매개변수**를 정의할 수 있음
    - 매개변수(parameter)는 **함수에 전달되는 값**을 나타냄
    
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
    

### 함수의 정의와 호출 2

- 함수 body
    - 콜론(`:`) 다음에 들여쓰기 된 코드 블록
    - 함수가 실행 될 때 수행되는 코드를 정의
    - **Docstring**은 함수 body 앞에 선택적으로 작성 가능한 함수 설명서
        
        ![이미지](https://github.com/ragu6963/TIL/assets/32388270/71898c0f-abee-4946-9b19-9083d0d8c4e7)
        

### 함수의 정의와 호출 3

- 함수 반환 값
    - 함수는 필요한 경우 결과를 반환할 수 있음
    - `return` 키워드 이후에 **반환할 값을 명시**
    - `return` 문은 함수의 실행을 종료하고, 결과를 호출 부분으로 반환
    - `return` 밑에 코드를 쓰면, 작동되지 않음
    - `return` 을 쓰지 않으면 **파이썬이 알아서 None을 반환**해 정상 종료할 수 있도록 함
        
        ![이미지](https://github.com/ragu6963/TIL/assets/32388270/9b0cadc1-aeb7-4bf9-a9fe-e8d13f06717f)
        

### 리턴과 출력

- 출력과 리턴은 다름
- 리턴은 반환되는 값이 있고, **할당할 수 있음**
- 출력은 반환되는 값이 없고 그저 출력할 뿐임.

```python
def my_func():
    print('hello world')

result_2 = my_func()
print(result_2)
# hello world
# None
# 두 줄이 출력됨. 

# print 함수는 return이 없다.
# 함수 내에서 출력이 일어났지만, 반환된 값은 없기 때문
```

### 함수의 정의와 호출 4

- 함수 호출
    - 함수를 사용하기 위해서는 호출이 필요
    - 함수의 이름과 소괄호를 활용해 호출
    - 필요한 경우 **인자(argument)를 전달**해야 함
    - 호출 부분에서 **전달된 인자는 함수 정의 시 작성한 매개변수에 대입**됨
        
        ![이미지](https://github.com/ragu6963/TIL/assets/32388270/01253ed5-3ab6-40c5-bfd8-04ca0c2ae01d)
        

**실행해보기**

```python
# 실행 해보기 1
def greet(name):
    message = 'Hello, ' + name
    return message

result = greet('Alice')
print(result)
```

### 함수 호출 (function call)

- 함수를 실행하기 위해 함수의 이름을 사용하여 해당 함수의 코드 블록을 실행하는 것

```python
function_name(arguments)
```

## 매개변수와 인자

### 매개변수와 인자

### 매개변수 `parameter`

- 함수를 **정의**할 때, **함수가 받을 값**을 나타내는 변수
    - 위치에 대한 기능을 할 뿐이지, 특별한 기능을 수행하지는 않음.

### 인자 `argument`

- 함수를 **호출**할 때, **실제로 전달되는 값**

### 매개변수와 인자 예시

```python
def add_numbers(x, y): # **x와 y는 매개변수(parameter)**
    result = x + y
    return result

a = 2
b = 3
sum_result = add_numbers(a, b) **# a와 b는 인자(argument)**
print(sum_result)
```

**실행 해보기**

```python
# 실행 해보기 1
def add_numbers(x, y):
	result = x + y
	return result

a = 2
b = 3
sum_result = add_numbers(a, b)
print(sum_result)
```

**다양한 인자 종류**
1. 위치 인자  
2. 기본 인자 값
3. 키워드 인자
4. 임의의 인자 목록
5. 임의의 키워드 인자 목록

### Positional Arguments (위치 인자)

- 함수 **호출 시 인자의 위치에 따라 전달되는 인자**
- **위치 인자는 함수 호출 시 반드시 값을 전달해야 함 (누락되면 안 됨)**
    
    ```python
    def greet(name, age):
        print(f'안녕하세요, {name}님! {age}살이시군요.')
    
    greet('Alice', 25) # 안녕하세요, Alice님! 25살이시군요
    ```
    

### Default Argument Values (기본 인자 값)

- 함수 정의에서 **매개변수에 기본 값을 할당**하는 것
- 함수 호출 시 **인자를 전달하지 않으면, 기본값이 매개변수에 할당**됨
    - 위치 인자에서 값이 누락되면 오류가 발생하는 것을 보완
    
    ```python
    def greet(name, age=30):
        print(f'안녕하세요, {name}님! {age}살이시군요.')
    
    greet('Bob') # 안녕하세요, Bob님! 30살이시군요.
    greet('Charlie', 40) # 안녕하세요, Charlie님! 40살이시군요.
    ```
    

### Keyword Arguments (키워드 인자)

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
    

### Arbitrary Argument Lists (임의의 인자 목록)

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
    

### Arbitrary Keyword Argument Lists (임의의 키워드 인자 목록)

- **정해지지 않은 개수의 키워드 인자를 처리**하는 인자
- 함수 정의 시 매개변수 앞에 `‘**’`를 붙여 사용하며,
    
    여러 개의 인자를 **dictionary로 묶어 처리**
    
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
        # 위치1, 위치2, 기본, 가변, 가변 키워드
        # ...
    ```
    

### 인자의 모든 종류를 적용한 예시

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

**실행 해보기**

```python
# 실행 해보기 1
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')

greet('Alice', 25)
```

```python
# 실행 해보기 2
def greet(name, age=30):
    print(f'안녕하세요, {name}님! {age}살이시군요.')

greet('Bob')
greet('Charlie', 40)
```

```python
# 실행 해보기 3
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')

greet(name='Dave', age=35)
```

```python
# 실행 해보기 4
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')

greet(age=35, 'Dave')
```

```python
# 실행 해보기 5
"""
아래 오류 발생 시 sum 변수 객체 삭제를 위해
del sum 코드 한 번 실행
TypeError: 'int' object is not callable
"""
# del sum

def calculate_sum(*args):
    print(args)
    total = sum(args)
    print(f'합계: {total}')

calculate_sum(1, 2, 3)
```

```python
# 실행 해보기 6
def print_info(**kwargs):
    print(kwargs)

print_info(name='Eve', age=30)
```

## 재귀 함수

### 재귀 함수

- **함수 내부에서 자기 자신을 호출**하는 함수

### 재귀 함수 예시 (팩토리얼)

```python
**𝑛!**
𝑛 ∗ (𝑛−1)!
𝑛 ∗ (𝑛−1) ∗ (𝑛−2)!
…
```

- factorial 함수는 **자기 자신을 재귀적으로 호출**하여 입력된 숫자 n의 팩토리얼을 계산
- 재귀 호출은 **n이 0이 될 때까지 반복**되며, **종료 조건을 설정**하여 **재귀 호출이 멈추도록** 함
- 재귀 호출의 결과를 이용하여 **문제를 작은 단위의 문제로 분할하고**, **분할된 문제들의 결과를 조합하여 최종 결과를 도출**

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
**# 종료 조건을 명확히 하고, 종료 조건을 향해 나아갈 수 있도록!**
```

---

### 재귀 함수 특징

- **특정 알고리즘 식을 표현**할 때 **변수의 사용이 줄어들며, 코드의 가독성이 높아짐 (항상 X)**
- 1개 이상의 **base case(**종료되는 상황)가 존재하고, **수렴하도록 작성**

### 재귀 함수를 사용하는 이유

- 문제의 **자연스러운 표현**
    - 복잡한 문제를 **간결하고 직관적으로 표현** 가능
- 코드 **간결성**
    - **상황에 따라** 반복문보다 알고리즘 코드가 **더 간결하고 명확해질 수 있음**
- **수학적 문제 해결**
    - 수학적 정의가 재귀적으로 표현되는 경우, 직접적인 구현 가능

### 재귀 함수 활용 시 기억해야 할 것

1. **종료 조건을 명확히**
2. **반복되는 호출이 종료 조건을 향하도록**

## 내장 함수

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

### 유용한 내장 함수 map & zip

### `map(function(함수), iterable(반복 가능한 객체))`

- 순회 가능한 **데이터구조(iterable)**의 **모든 요소에 함수를 적용**하고, 그 **결과를 map object로 반환**
- **요소 하나하나에 함수를 적용하기에, 반복(순회) 가능한 객체를 대입해야 함**
- **확장성:** 함수 자리에 내가 만든 함수도 적용이 가능함

```python
numbers = [1, 2, 3]
result = map(str, numbers)

print(result)  # <map object at 0x00000239C915D760> map 덩어리로 반환
print(list(result))  # ['1', '2', '3']
```

### `map()` 활용

- SWEA 문제의 input 처럼 문자열 `'1 2 3'`이 입력 되었을 때 활용 예시

```python
numbers1 = input().split() # split을 통해서 공백 단위로 데이터를 끊어 리스트로 변환
print(numbers1)  # ['1', '2', '3']

numbers2 = list(map(int, input().split())) # .map을 통해서 리스트 내부 요소들에 함수 적용
print(numbers2)  # [1, 2, 3]
```

### `zip(*iterable)`

- **임의의 iterable(반복이 가능한 것)을 모아 튜플을 원소로 하는 zip object를 반환**
    
    ```python
    girls = ['jane', 'ashley']
    boys = ['peter', 'jay']
    
    pair = zip(girls, boys)
    
    print(pair)  # <zip object at 0x000001C76DE58700> zip object로 반환
    print(list(pair))  # [('jane', 'peter'), ('ashley', 'jay')]
    ```
    

### `zip()` 활용

- 여러 개의 리스트를 동시에 조회할 때
    
    ```python
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
    
- 2차원 리스트의 같은 컬럼(열) 요소를 동시에 조회할 때
    
    ```python
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
    

## 함수와 Scope

### Python의 범위(Scope)

- **함수는 코드 내부에 `local scope`**를 생성하며, **그 외의 공간인 `global scope`**로 구분

### 범위와 변수 관계

- scope
    - **global scope (전역)**  : **코드 어디에서든 참조**할 수 있는 공간
    - **local scope (지역**) : 함수가 만든 scope (**함수 내부에서만 참조 가능**)
- variable
    - **global variable** : global scope에 정의된 변수
    - **local variable** : local scope에 정의된 변수

### Scope 예시

- **`num`은 local scope에 존재하기 때문에 global에서 사용할 수 없음**
- 이는 **변수의** **`수명주기`와 연관**이 있음
    
    ```python
    def func():
        num = 20
        print('local', num)  # local 20
    
    func()
    
    print('global', num)  # NameError: name 'num' is not defined
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

![이미지](https://github.com/ragu6963/TIL/assets/32388270/15b4f0c6-7f21-4986-8349-fd8740e49573)

### LEGB Rule 예시 1

- sum이라는 이름을 global scope에서 사용하게 되면서
    
    기존에 built-in scope에 있던 내장함수 sum을 사용하지 못하게 됨
    
- sum을 참조 시 LEGB Rule에 따라 global에서 먼저 찾기 때문
    
    ```python
    print(sum) # <built-in function sum>
    print(sum(range(3))) # 3
    
    sum = 5 **# sum이라는 이름을 global scope에서 사용**
    
    print(sum) # 5
    print(sum(range(3))) # TypeError: 'int' object is not callable
    **# built-in scope에 있던 내장함수 sum을 사용하지 못하게 됨**
    ```
    

**LEGB Rule 퀴즈**

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

**# 지역 영역에서부터 요소가 없을 때마다 확장해 나가면서 해답을 찾기: 매개변수 헷갈리지 말기
# 글로벌과 같은 바깥 영역에서는 안쪽 지역변수에서 값을 찾을 필요 없음**
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
    

### ‘global’ 키워드 주의사항 (1/2)

- global 키워드 선언 전에 참조 불가
    
    ```python
    num = 0
    
    def increment():
        # SyntaxError: name 'num' is used prior to global declaration
        print(num) **# global 선언 전에 참조 X**
        global num
        num += 1
    
    ```
    

### ‘global’ 키워드 주의사항 (2/2)

- 매개변수에는 global 키워드 사용 불가
    
    ```python
    num = 0
    
    def increment(num): **# 매개변수 X**
        # "num" is assigned before global declaration
        global num
        num += 1
    
    ```
    

**실행 해보기**

```python
# 실행 해보기 1
def func():
    num = 20
    print('local', num)

func()

print('global', num)
```

```python
# 실행 해보기 2
print(sum)
print(sum(range(3)))

sum = 5

print(sum) # 5
print(sum(range(3)))
```

```python
# 실행 해보기 3
a = 1
b = 2

def enclosed():
    a = 10
    c = 3

    def local(c):
        print(a, b, c)

    local(500)
    print(a, b, c)

enclosed()
print(a, b)
```

```python
# 실행 해보기 4
num = 0

def increment():
    global num
    num += 1

print(num)
increment()
print(num)
```

```python
# 실행 해보기 5
num = 0

def increment():
    print(num)
    global num
    num += 1
```

```python
# 실행 해보기 6
num = 0

def increment(num):
    global num
    num += 1
```

## 참고

### 람다 표현식 (Lambda expressions)

- 익명 함수를 만드는 데 사용되는 표현식
- 한 줄로 간단한 함수를 정의

### lambda 함수 구조

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

### 람다 표현식 예시

- 간단한 연산이나 함수를 한 줄로 표현할 때 사용
- 함수를 매개변수로 전달하는 경우에도 유용하게 활용
    
    ```python
    # 람다 함수 미적용 코드
    def addition(x, y):
        return x + y
    
    result = addition(3, 5)
    print(result) # 8
    ```
    
    ```python
    # 람다 함수 적용 코드
    addition = lambda x, y: x + y
    
    result = addition(3, 5)
    print(result) # 8
    ```
    

**람다 표현식 활용 (with map 함수)**

```python
numbers = [1, 2, 3, 4, 5]  
def square(x):  
    return x**2
```
# lambda 미사용
```python
squared1 = list(map(square, numbers))  
print(squared1)  # [1, 4, 9, 16, 25]
```
# lambda 사용
```python
squared2 = list(map(lambda x: x**2, numbers))   
print(squared2)  # [1, 4, 9, 16, 25]`
```
**실행 해보기**

```python
# 실행 해보기 1
def addition(x, y):
    return x + y

result = addition(3, 5)
print(result)
```

```python
# 실행 해보기 2
addition = lambda x, y: x + y

result = addition(3, 5)
print(result)
```
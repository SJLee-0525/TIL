# Control of flow

## 제어문

### 제어문 `Control Statement`

- 코드의 **실행 흐름을 제어**하는 데 사용되는 구문
- **조건에 따라 코드 블록을 실행**하거나 **반복적으로 코드를 실행**

### 제어문 종류

- **조건문**
    - `if`, `elif`, `else`
- **반복문**
    - `for`, `while`
- **반복문 제어**
    - `break`, `continue`, `pass`

## 조건문

### 개요

### 조건문 `Conditional Statement`

- 주어진 조건식을 평가하여 **해당 조건이 참(True)인 경우에만** 코드 블록을 실행하거나 건너뜀

### 파이썬 조건문에 사용되는 키워드

- `if` / `elif` / `else`

### `‘if’` statement

- if statement의 기본 구조
    
    ```python
    if 표현식:
        코드 블록
    elif 표현식:
        코드 블록
    else:
        코드 블록
    ```
    

### 조건문 예시 (1/2)

```python
a = 5

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)

# 3 초과
# 5
```

![이미지](https://github.com/ragu6963/TIL/assets/32388270/3e0e596c-202e-45bb-859c-6e8a2797548a)

### 조건문 예시 (2/2)

```python
a = 3

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)

# 3 이하
# 3
```

![이미지](https://github.com/ragu6963/TIL/assets/32388270/ea3beaf3-b5ae-4082-a38b-33fb26e8af91)

### 복수 조건문

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

**실행 해보기**

```
# 실행 해보기 1
a = 5

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)
```

```
# 실행 해보기 2
a = 3

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)
```

```
# 실행 해보기 3
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

```
# 실행 해보기 4
dust = 480

if dust > 150:
    print('매우 나쁨')
    if dust > 300:
        print('위험해요! 나가지 마세요!')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```

## 반복문

### 개요

### 반복문 `Loop Statement`

- **주어진 코드 블록을 여러 번 반복해서 실행**하는 구문
1. 특정 작업을 **반복적**으로 수행
2. 주어진 조건이 **참인 동안 반복해서 실행**

### 파이썬 반복문에 사용되는 키워드

- **`for`**
    - **특정 작업을 반복적으로 수행**
        - 종료 조건이 명확함
- **`while`**
    - 주어진 **조건이 참인 동안 반복해서 실행**
        - 종료 조건이 없다면 무한히 돌아감

### `‘for’` statement

- 임의의 시퀀스의 항목들을 그 시퀀스에 들어있는 순서대로 반복
- for statement의 기본 구조
    
    ```python
    **for 변수 in 반복 가능한 객체:
        코드 블록**
    
    # for문의 변수는 임시 변수
    # fot문 내부에서 임시 변수를 활용할 수 있음
    ```
    

### 반복 가능한 객체 `iterable`

- **반복문에서 순회할 수 있는 객체** (**sequence** 객체 뿐만 아니라 **dict, set** 등도 포함)

### for 문 원리

- 리스트 내 첫 항목이 반복 변수에 할당되고 코드 블록이 실행
- 다음으로 반복 변수에 리스트의 2번째 항목이 할당되고 코드 블록이 다시 실행
- ... 마지막으로 반복 변수에 리스트의 마지막 요소가 할당되고 코드 블록이 실행
    
    ```python
    items = ['apple', 'banana', 'coconut'] # 복수형
    
    **for item in items: # 반복 가능한 객체의 길이만큼**
        **print(item) # 단수형**
    
    """
    apple
    banana
    coconut
    """
    
    # Guide: 순회하는 객체와 임시 변수는 구분하기 쉽게 복수형 / 단수형으로 구분할 수 있도록 하자
    ```
    

**문자열 순회**

- 문자열도 sequence 데이터임

```python
country = 'Korea'

**for char in country:
    print(char)**

"""
K
o
r
e
a
"""
```

**range 순회**

- 굳이 list(range(i))로 **변환하지 않아도,** 반복 가능한 객체로 출력

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

**dict 순회**

- 기본적으로 dict는 for문 사용시 **key를 뱉어냄**
    - key를 활용해서 value를 출력하자!

```python
my_dict = {
    'x': 10,
    'y': 20,
    'z': 30,
}

**for key in my_dict:
    print(key)
    print(my_dict[key])**
    
"""
x
10
y
20
z
30
"""
```

### 인덱스로 리스트 순회

- 리스트의 요소가 아닌 **인덱스로 접근**하여 해당 요소들을 변경하기
    
    ```python
    numbers = [4, 6, 10, -8, 5]
    
    **for i in range(len(numbers)):**
        numbers[i] = numbers[i] * 2
    
    print(numbers) # [8, 12, 20, -16, 10]
    ```
    

### 중첩된 반복문

- **안쪽 반복문은 outers 리스트의 각 항목에 대해 한 번씩 실행됨**
- print가 호출되는 횟수 => **`len(outers) * len(inners)`**
    
    ```python
    outers = ['A', 'B']
    inners = ['c', 'd']
    
    **for outer in outers:
        for inner in inners:
            print(outer, inner)**
    
    """
    A c
    A d
    B c
    B d
    """
    ```
    

### 중첩 리스트 순회

- 안쪽 리스트 요소에 접근하려면 바깥 리스트를 순회하면서 중첩 반복을 사용해 각 안쪽 반복을 순회
    
    ```python
    elements = [['A', 'B'], ['c', 'd']]
    
    for elem in elements:
        print(elem)
    
    """
    ['A', 'B']
    ['c', 'd']
    """
    ```
    
    ```python
    elements = [['A', 'B'], ['c', 'd']]
    
    for elem in elements:
        for item in elem:
            print(item)
    
    """
    A
    B
    c
    d
    """
    ```
    

**실행해보기**

```
# 실행 해보기 1
items = ['apple', 'banana', 'coconut']

for item in items:
    print(item)
```

```
# 실행 해보기 2
country = 'Korea'

for char in country:
    print(char)
```

```
# 실행 해보기 3
for i in range(5):
    print(i)
```

```
# 실행 해보기 4
numbers = [4, 6, 10, -8, 5]

for i in range(len(numbers)):
    numbers[i] = numbers[i] * 2

print(numbers)
```

```
# 실행 해보기 5
outers = ['A', 'B']
inners = ['c', 'd']

for outer in outers:
    for inner in inners:
        print(outer, inner)
```

```
# 실행 해보기 6
elements = [['A', 'B'], ['c', 'd']]
for elem in elements:
    print(elem)
```

```
# 실행 해보기 7
elements = [['A', 'B'], ['c', 'd']]
for elem in elements:
    for item in elem:
        print(item)
```

### ‘while’ statement

- 주어진 **조건식이 참(True)인 동안** 코드를 반복해서 실행
    - **조건식이 거짓(False)가 될 때 까지 반복**
- while statement의 기본 구조
    
    ```python
    while 조건식:
        코드 블록
    ```
    

**while 반복문 예시**

```python
a = 0

**while a < 3:
    print(a)
    a += 1**

print('끝')

"""
0
1 
2 
끝
"""
```

### 사용자 입력에 따른 반복

- while문을 사용한 특정 입력 값에 대한 종료 조건 활용하기
    
    ```python
    number = int(input('양의 정수를 입력해주세요.: '))
    
    while number <= 0:
        if number < 0:
            print('음수를 입력했습니다.')
        else:
            print('0은 양의 정수가 아닙니다.')
        number = int(input('양의 정수를 입력해주세요.: '))
    
    print('잘했습니다!')
    """
    양의 정수를 입력해주세요.: 0
    0은 양의 정수가 아닙니다.
    양의 정수를 입력해주세요.: -1
    음수를 입력했습니다.
    양의 정수를 입력해주세요.: 1
    잘했습니다!
    """
    ```
    

**while 문은 반드시 `종료 조건`이 필요**

- 주어진 조건식이 참인 동안 : 거짓이 될 때 까지 작동

### 적절한 반복문 활용하기

- **`for`**
    - **반복 횟수가 명확하게 정해져 있는 경우에 유용**
    - 예를 들어 **리스트, 튜플, 문자열 등과 같은 시퀀스 형식의 데이터**를 처리할 때
- **`while`**
    - **반복 횟수가 불명확하거나 조건에 따라 반복을 종료해야 할 때** 유용
    - 예를 들어 **사용자의 입력을 받아서 특정 조건이 충족될 때까지 반복하는 경우**

**실행 해보기**

```
# 실행 해보기 1
a = 0

while a < 3:
    print(a)
    a += 1

print('끝')
```

```
# 실행 해보기 2
number = int(input('양의 정수를 입력해주세요.: '))
while number <= 0:
    if number < 0:
        print('음수를 입력했습니다.')
    else:
        print('0은 양의 정수가 아닙니다.')
    number = int(input('양의 정수를 입력해주세요.: '))
print('잘했습니다!')
```

### 반복 제어

- for문과 while은 매 반복마다 본문 내 모든 코드를 실행하지만
때때로 일부만 실행하는 것이 필요할 때가 있음

### 반복문 제어 키워드

- **`break`**
    - 반복을 **즉시 중지**
- **`continue`**
    - **다음 반복으로 건너뜀**
- **`pass`**
    - 아무런 동작도 **수행하지 않고 넘어감**

**반복문 제어 예시**

```python
# break

for i in range(10):
    if i == 5:
        **break # 중지**
    print(i)  # 0 1 2 3 4
```

```python
# continue

for i in range(10):
    if i % 2 == 0:
        **continue # 다음 반복으로** 
    print(i)  # 1 3 5 7 9
```

```python
# pass

for i in range(10):
    **pass**  **# 아무 작업도 안함 (에러 방지 등)**
```

### break 예시 (1/2)

- 프로그램 종료 조건 만들기
    
    ```python
    number = int(input('양의 정수를 입력해주세요.: '))
    
    while number <= 0:
        """
        종료 조건과 break
        """
        if number == -9999:
            print('프로그램을 종료합니다.')
            break
    
        if number < 0:
            print('음수를 입력했습니다.')
        else:
            print('0은 양의 정수가 아닙니다.')
    
        number = int(input('양의 정수를 입력해주세요.: '))
    
    print('잘했습니다!')
    
    """
    양의 정수를 입력해주세요.: -9999
    프로그램을 종료합니다.
    잘했습니다!
    """
    ```
    

### break 예시 (2/2)

- 리스트에서 첫번째 짝수만 찾은 후 반복 종료하기
    
    ```python
    numbers = [1, 3, 5, 6, 7, 9, 10, 11]
    found_even = False
    
    for num in numbers:
        if num % 2 == 0:
            print('첫 번째 짝수를 찾았습니다:', num)
            found_even = True
            break
    
    if not found_even:
        print('짝수를 찾지 못했습니다')
    
    """
    첫 번째 짝수를 찾았습니다: 6
    """
    ```
    

### continue 예시

- 리스트에서 홀수만 출력하기
- `현재 반복문의 남은 코드를 건너뛰고 다음 반복으로 넘어감`
    
    ```python
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
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
    

**pass 예시**

1. **코드 작성 중** **미완성 부분**
    ◦ 구현해야 할 부분이 나중에 추가될 수 있고, 코드를 컴파일하는 동안 오류가 발생하지 않음

```python
def my_function():
    pass  
```

**2. 조건문에서 아무런 동작을 수행하지 않아야 할 때**

```python
if condition:
    pass  # 아무런 동작도 수행하지 않음
else:
    # 다른 동작 수행
```

**3. 무한 루프에서 조건이 충족되지 않을 때 pass를 사용하여 루프를 계속 진행하는 방법**

```python
while True:
    if condition:
        break
    elif condition:
        pass  # 루프 계속 진행
    else:
        print('..')
```

**실행 해보기**

```
# 실행 해보기 1
number = int(input('양의 정수를 입력해주세요.: '))
while number <= 0:
    if number == -9999:
        print('프로그램을 종료합니다.')
        break
    if number < 0:
        print('음수를 입력했습니다.')
    else:
        print('0은 양의 정수가 아닙니다.')
    number = int(input('양의 정수를 입력해주세요.: '))
print('잘했습니다!')
```

```
# 실행 해보기 2
numbers = [1, 3, 5, 6, 7, 9, 10, 11]
found_even = False
for num in numbers:
    if num % 2 == 0:
        print('첫 번째 짝수를 찾았습니다:', num)
        found_even = True
        break
if not found_even:
    print('짝수를 찾지 못했습니다')
```

```
# 실행 해보기 3
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for num in numbers:
    if num % 2 == 0:
        continue
    print(num)
```

```
# 실행 해보기 4
for number in range(1, 5):
    if number != 3:
        print(number)
```

### List Comprehension

- 간결하고 효율적인 리스트 생성 방법

**List Comprehension 구조**

```python
[expression for 변수 in iterable]
list(expression for 변수 in iterable)

**# expression: 변수에 할당할 수식**
```

```python
[expression for 변수 in iterable if 조건식]
list(expression for 변수 in iterable if 조건식)
```

### List Comprehension 사용 전/후 비교

- 사용 전
    
    ```python
    numbers = [1, 2, 3, 4, 5]
    squared_numbers = []
    
    for num in numbers:
        squared_numbers.append(num**2)
    
    print(squared_numbers)  # [1, 4, 9, 16, 25]
    ```
    
- 사용 후
    
    ```python
    numbers = [1, 2, 3, 4, 5]
    squared_numbers = [num**2 for num in numbers]
    
    print(squared_numbers)  # [1, 4, 9, 16, 25]
    ```
    
- if문 포함

```python
	# if문 포함
squared_numbers_3 = [num ** 2 for num in numbers if num % 2 == 1]
print(squared_numbers_3)
```

### List Comprehension 활용 예시

- 2차원 배열 생성 시 (인접행렬 생성 시)

```python
data1 = [[0] * (5) for _ in range(5)]

# 또는
data2 = [[0 for _ in range(5)] for _ in range(5)]

"""
[[0, 0, 0, 0, 0],
 [0, 0, 0, 0, 0],
 [0, 0, 0, 0, 0],
 [0, 0, 0, 0, 0],
 [0, 0, 0, 0, 0]]
"""

```

### 가독성 비교

- **Comprehension 사용**
    
    ```python
    result = [i for i in range(10) if i % 2 == 1]
    ```
    
- **Comprehension 미사용**
    
    ```python
    result = []
    for i in range(10):
        if i % 2 == 1:
            result.append(i)
    ```
    
- **Comprehension을 남용하지 말자**
    - **Comprehension은 리스트를 생성하는 목적:** for문 단축이 목적이 아님

**실행 해보기**

```
# 실행 해보기 1
numbers = [1, 2, 3, 4, 5]
squared_numbers = []
for num in numbers:
    squared_numbers.append(num**2)
print(squared_numbers)
```

```
# 실행 해보기 2
numbers = [1, 2, 3, 4, 5]
squared_numbers = [num**2 for num in numbers]
print(squared_numbers)
```

```
# 실행 해보기 3
result = [i for i in range(10) if i % 2 == 1]
print(result)
```

```
# 실행 해보기 4
result = []
for i in range(10):
    if i % 2 == 1:
        result.append(i)
print(result)

```

**참고
enumerate**

### `enumerate(iterable, start=0)`

- iterable 객체의 각 요소에 대해 인덱스와 함께 반환하는 내장함수

**enumerate 예시**

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
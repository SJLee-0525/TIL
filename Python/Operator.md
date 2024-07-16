# Operator

## 연산자

### 산술 연산자

| 기호 | 연산자 |
| --- | --- |
| - | 음수   부호 |
| + | 덧셈 |
| - | 뺄셈 |
| * | 곱셈 |
| / | 나눗셈 |
| // | 정수   나눗셈 (몫) |
| % | 나머지 |
| ** | 지수   (거듭제곱) |

### 복합 연산자

- 연산과 할당이 함께 이뤄짐

| 기호 | 예시 | 의미 |
| --- | --- | --- |
| += | a   += b | a   = a + b |
| -= | a   -= b | a   = a - b |
| *= | a   *= b | a   = a * b |
| /= | a   /= b | a   = a / b |
| //= | a   //= b | a   = a // b |
| %= | a   %= b | a   = a % b |
| **= | a   **= b | a   = a ** b |

### 복합 연산자 예시

```python
y = 10
y -= 4
print(y) # 6

z = 7
z *= 2
print(z) # 14

w = 15
w /= 4
print(w) # 3.75

q = 20
q //= 3
print(q) # 6
```

### 실행 해보기

y = 10  
y -= 4  
print(y)  

z = 7  
z *= 2  
print(z)  

w = 15  
w /= 4  
print(w)

q = 20  
q //= 3  
print(q)

### 비교 연산자

| 기호 | 내용 |
| --- | --- |
| < | 미만 |
| <= | 이하 |
| > | 초과 |
| >= | 이상 |
| == | 같음 |
| != | 같지   않음 |
| is | 같음 |
| is   not | 같지   않음 |

### is 비교 연산자

- 매모리 내에서 같은 객체를 참조하는지 확인
- `==` 는 동등성(equality): **값이 같은지만 확인**
- `is` 는 식별성(identity): **값 뿐만 아니라 주소까지 같은지 확인**
- 값을 비교하는 `==` 와 다름
- 주로 None, Bool 구분할 때 사용

| 기호 | 내용 |
| --- | --- |
| is | 같음 |
| is not | 같지 않음 |

### 비교 연산자 예시

```python
print(3 > 6)  # False
**print(2.0 == 2)  # True**
print(2 != 2)  # False
print('HI' == 'hi')  # False
**print(1 == True)  # True**

# SyntaxWarning: "is" with a literal. Did you mean "=="?
# ==은 값(데이터)을 비교하는 것이지만 is는 레퍼런스(주소)를 비교하기 때문
# 아래 조건은 항상 False이기 때문에 is 대신 ==를 사용해야 한다는 것을 알림
**print(1 is True)  # False
print(1 == True)  # True

print(2 is 2.0)  # False**
**print(2.0 == 2)  # True**
```

### 실행 해보기

# 실행 해보기 1

print(3 > 6) `# False`  
print(2.0 == 2) `# True`  
print(2 != 2) `# False`  
print('HI' == 'hi') `# False`  
print(1 == True) `# True`  

# SyntaxWarning: "is" with a literal. Did you mean "=="?

# ==은 값(데이터)을 비교하는 것이지만 is는 레퍼런스(주소)를 비교하기 때문

# 아래 조건은 항상 False이기 때문에 is 대신 ==를 사용해야 한다는 것을 알림

print(1 is True) `# False`  
print(2 is 2.0)  `# False`  

### 논리 연산자

| 기호 | 연산자 | 내용 |
| --- | --- | --- |
| and | 논리곱 | 두   피연산자 모두 True인   경우에만      전체   표현식을 True로   평가 |
| or | 논리합 | 두   피연산자 중 하나라도 True인   경우      전체   표현식을 True로   평가 |
| not | 논리부정 | 단일   피연산자를 부정 |

### 논리 연산자 예시 (1/2)

```python
print(True and False) # False

print(True or False) # True

print(not True) # False

print(not 0) # True
```

### 논리 연산자 예시 (2/2)

- 비교 연산자와 함께 사용 가능
    
    ```python
    num = 15
    result = (num > 10) and (num % 2 == 0)
    print(result) # False
    
    name = 'Alice'
    age = 25
    result = (name == 'Alice') or (age == 30)
    print(result) # True
    ```
    

### 단축평가

- 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작

### 단축평가 예시 문제

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

### 단축평가 동작

- and
    - 첫 번째 피연산자가 False인 경우, 전체 표현식은 False로 결정.
        - 두 번째 피연산자는 평가되지 않고 그 값이 무시
    - 첫 번째 피연산자가 True인 경우, 전체 표현식의 결과는 두 번째 피연산자에 의해 결정.
        - 두 번째 피연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환
- or
    - 첫 번째 피연산자가 True인 경우, 전체 표현식은 True로 결정.
        - 두 번째 피연산자는 평가되지 않고 그 값이 무시
    - 첫 번째 피연산자가 False인 경우, 전체 표현식의 결과는 두 번째 피연산자에 의해 결정.
        - 두 번째 피연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환

### 단축평가 이유

- **코드 실행을 최적화하고, 불필요한 연산을 피할 수 있도록 함**

### 멤버십 연산자

- 특정 값이 시퀀스나 다른 컬렉션에 속하는지 여부를 확인

| 기호 | 내용 |
| --- | --- |
| in | 왼쪽   피연산자가 오른쪽 피연산자의 시퀀스에 속하는지를 확인 |
| not   in | 왼쪽   피연산자가 오른쪽 피연산자의 시퀀스에 속하지 않는지를 확인 |

### 멤버십 연산자 예시

```python
word = 'hello'
numbers = [1, 2, 3, 4, 5]

print('h' in word)  # True
print('z' in word)  # False

print(4 not in numbers)  # False
print(6 not in numbers)  # True
```

### 시퀀스형 연산자

- `+` 와 `` 는 시퀀스 (str, list, tuple ..) 간 연산에서 산술 연산자일 때와 다른 역할을 가짐

| 연산자 | 내용 |
| --- | --- |
| + | 결합   연산자 |
| * | 반복   연산자 |

### 시퀀스형 연산자 예시

```python
# Gildong Hong
print('Gildong' + ' Hong')

# hihihihihi
print('hi' * 5)

# [1, 2, 'a', 'b']
print([1, 2] + ['a', 'b'])

# [1, 2, 1, 2]
print([1, 2] * 2)
```

### 연산자 우선순위

| 우선순위 | 연산자 | 내용 |
| --- | --- | --- |
| 높음 | () | 소괄호   grouping |
|  | [] | 인덱싱,   슬라이싱 |
|  | ** | 거듭제곱 |
|  | +,   - | 단항   연산자 양수/음수 |
|  | *,   /, //, % | 산술   연산자 |
|  | +,   - | 산술   연산자 |
|  | <,   <=, >, >=, ==, != | 비교   연산자 |
|  | is,   is not | 객체   비교 |
|  | in,   not in | 멤버십   연산자 |
|  | not | 논리   부정 |
|  | and | 논리   AND |
| 낮음 | or | 논리   OR |
# 06 Packing & Unpacking

# Packing & Unpacking

## Packing & Unpacking

### Packing `패킹`

- 여러 개의 값을 하나의 변수에 묶어서 담는 것

### 패킹 예시

- 변수에 담긴 값들은 **튜플(tuple**) 형태로 묶임
    
    ```python
    packed_values = 1, 2, 3, 4, 5
    **# 1개의 변수에 여러개의 값을 지정: 1개의 튜플로 묶어서 할당**
    
    print(packed_values)  # (1, 2, 3, 4, 5)
    ```
    

### `‘*’`을 활용한 패킹

- `b`는 **남은 요소들을 리스트로 패킹하여 할당**
    
    ```python
    numbers = [1, 2, 3, 4, 5]
    a, *b, c = numbers
    
    print(a) # 1
    print(b) # [2, 3, 4] **# 남은 요소들은 리스트로 할당됨**
    print(c) # 5
    ```
    
- print 함수에 임의의 가변 인자를 작성할 수 있었던 이유
    
    ```python
    print('hello') # hello
    print('you', 'need', 'python') # you need python
    
    ```
    
    ![이미지](https://github.com/ragu6963/TIL/assets/32388270/05db04bd-d01c-4f4c-a193-854e59385d67)
    

**실행 해보기**

```python
# 실행 해보기 1
packed_values = 1, 2, 3, 4, 5
print(packed_values)
```

```python
# 실행 해보기 2
numbers = [1, 2, 3, 4, 5]
a, *b, c = numbers

print(a)
print(b)
print(c)
```

```python
# 실행 해보기 3
print('hello')
print('you', 'need', 'python')
```

### Unpacking `언패킹`

- 패킹된 변수의 값을 개별적인 변수로 분리하여 할당하는 것

### 언패킹 예시

- 튜플이나 리스트 등의 객체의 요소들을 개별 변수에 할당
    
    ```python
    packed_values = 1, 2, 3, 4, 5
    
    a, b, c, d, e = packed_values
    print(a, b, c, d, e)  # 1 2 3 4 5
    
    **# 개수 안 맞으면: a, b, c, d, e, f = packed_values**
    ```
    

### `‘*’`을 활용한 언패킹

- **`*`** 는 리스트의 요소를 언패킹하여 인자로 전달
    
    ```python
    def my_function(x, y, z):
        print(x, y, z)
    
    names = ['alice', 'jane', 'peter']
    my_function(*names) # alice jane peter
    **# 인자로 넣을 때 '*'는 언패킹의 의미를 가짐**
    ```
    

### `‘**’`을 활용한 언패킹

- **`**`** 는 딕셔너리의 키-값 쌍을 함수의 키워드 인자로 언패킹
    
    ```python
    def my_function(x, y, z):
        print(x, y, z)
    
    my_dict = {'x': 1, 'y': 2, 'z': 3}
    my_function(**my_dict)  # 1 2 3
    
    **# 인자로 넣을 때 '**'는 언패킹의 의미를 가짐**
    **# 딕셔너리로 할 때는, 매개 변수와 key가 같아야 함** 
    ```
    

### ``, `*` 패킹 / 언패킹 연산자 정리

- `‘*’`
    - **패킹 연산자**로 사용될 때, **여러 개의 인자를 하나의 튜플로 묶음**
    - **언패킹 연산자**로 사용될 때, **시퀀스나 반복 가능한 객체를 각각의 요소로 언패킹하여 함수의 인자로 전달**
- `‘**’`
    - **언패킹 연산자**로 사용될 때, **딕셔너리의 키-값 쌍을 언패킹하여 함수의 키워드 인자로 전달**

**실행 해보기**

```python
# 실행 해보기 1
packed_values = 1, 2, 3, 4, 5
a, b, c, d, e = packed_values
print(a, b, c, d, e)
```

```python
# 실행 해보기 2
names = ['alice', 'jane', 'peter']
print(*names)
```

```python
# 실행 해보기 3
def my_function(x, y, z):
    print(x, y, z)

my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict)
```

### 람다 표현식 (Lambda expression)

**익명 함수를 만드는 데 사용되는 표현식**

→ **한 줄**로 간단한 함수를 정의

lambda 매개변수: 표현식

lambda 키워드: 람다 함수를 선언하기 위해 사용되는 키워드

매개 변수:

함수에 전달되는 매개변수들

여러개의 매개변수가 있을 경우 쉼표로 구분
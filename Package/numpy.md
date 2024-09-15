## NUMPY

```python
# pip install numpy
# pip install pandas

import csv
import numpy as np
import pandas as pd
```

## 2. Numpy 기본 사용법

### 2.1. 기존 배열을 numpy array 로 변형

- `np.array()` 함수 사용

```python
arr = [1, 2, 3, 4, 5]
np_arr = np.array(arr)

print(np_arr) # arr = [1, 2, 3, 4, 5]
```

- `type()` 함수를 통한 타입 확인

```python
print(type(arr)) # <class 'list'>
print(type(np_arr)) # print(type(np_arr))
```

---

### 2.2. Numpy 배열 생성

### 2.2.1. 기본 배열 생성

- `np.arange()` 함수 사용

```python
arr = np.arange(15)

print(arr) # [ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14]
print(type(arr)) # <class 'numpy.ndarray'>
```

- python 의 range 함수와 비슷하게도 사용 가능하다

```python
arr = np.arange(10, 30, 5)

print(arr) # [10 15 20 25]
print(type(arr)) # <class 'numpy.ndarray'>
```

---

### 2.2.2. Numpy 2차원 배열 생성

- `np.arange()` 함수로 배열 생성 후 `reshape()` 를 통해 2차원 배열로 변형
- **주의사항**: reshape 의 x, y 축 곱이 배열의 개수와 맞지 않으면 에러가 발생함

```python
# reshape(x축 개수, y축 개수)
arr = np.arange(15).reshape(3, 5)
print(arr) 

'''
[[ 0  1  2  3  4]
[ 5  6  7  8  9]
[10 11 12 13 14]]
'''
```

- 에러 발생 코드

```python
arr0 = np.arange(1, 21).reshape(5, 4)
print(arr0)
'''
[[ 1  2  3  4]
 [ 5  6  7  8]
 [ 9 10 11 12]
 [13 14 15 16]
 [17 18 19 20]]
 '''
 
arr = np.arange(20).reshape(3, 5)
print(arr)
# ValueError: cannot reshape array of size 20 into shape (3,5)
```

## 

### 2.2.3. 0으로만 이루어진 배열 생성

- `np.ones()` 사용

```python
# np.zeros((x축 개수, y축 개수), dtype=데이터 타입)

arr = np.zeros((3, 4), dtype=np.int64)
print(arr)
'''
[[0 0 0 0]
 [0 0 0 0]
 [0 0 0 0]]
 '''
```

위의 (행, 축) 표현처럼 **numpy 는 항상 `(행, 축)` 의 형태로 사용한다.**

---

### 2.2.4. 1로만 이루어진 배열 생성

```python
# np.ones((x축 개수, y축 개수), dtype=데이터 타입)

arr = np.ones((3, 4), dtype=np.int64)
print(arr)
'''
[[1 1 1 1]
 [1 1 1 1]
 [1 1 1 1]]
 '''
```

### 2.2.5. 특정 수로 이루어진 배열 생성

```python
# np.full((x축 개수, y축 개수), 값)

arr = np.full((3, 4), 0.11)
print(arr)
'''
# np.ones((x축 개수, y축 개수), dtype=데이터 타입)
arr = np.ones((3, 4), dtype=np.int64)
print(arr)
'''
```

### 2.2.6. 균일한 간격의 숫자 생성

- `np.linspace()` 활용
- 그래프의 x 축을 그릴 때 많이 사용합니다.
- `lin` 은 선형 간격 값을 생성하는 것은 나타내며, 이는 로그 간격 값을 생성하는 `logspace` 와 대조됩니다.

```python
# np,linspace(구간 시작점, 구간 끝점, 구간 내 숫자 개수)
# == -5부터 5 사이에 총 10개의 지점을 생성해라
arr = np.linspace(-5, 5, 10)
print(arr)
'''
# np.ones((x축 개수, y축 개수), dtype=데이터 타입)
arr = np.ones((3, 4), dtype=np.int64)
print(arr)
'''
```

---

### 2.2.7. 랜덤한 값 생성

- `np.random.rand()` 활용

```python
# np.random.rand(개수)

arr = np.random.rand(5)
print(arr)
# [0.84354928 0.61814076 0.81550152 0.15739787 0.4511692 ]
```

- 2차원 배열로 생성

```python
# np.random.rand(x축 개수, y축 개수)

arr = np.random.rand(2, 3)
print(arr)
'''
[[0.69287007 0.91360366 0.24896903]
 [0.24731099 0.46892157 0.72723477]]
 '''
```

- 원하는 범위 내의 정수 값을 원하는 개수로 생성하기

```python
# np.random.randint(범위, size=개수)

arr = np.random.randint(5, size=10)
print(arr)
# [1 4 0 2 3 2 1 4 1 2]
```

---

### 3. 기본 함수

```python
arr = np.arange(15).reshape(3, 5)
print(arr)
'''
# np.random.randint(범위, size=개수)
arr = np.random.randint(5, size=10)
print(arr)
'''
```

```python
# 배열 각 축(axis) 의 크기

arr.shape
# (3, 5)
```

```python
# 축의 개수(차원, Dimension)

arr.ndim
# 2
```

```python
# 각 요소(Element) 의 타입

arr.dtype
# dtype('int64')
```

```python
# 각 요소(Element)의 타입의 bytes 의 크기

arr.itemsize
# 8
```

```python
# 전체 요소(Element) 의 개수

arr.size
# 15
```

---

### 4. Indexing & Slicing

- 파이썬 기본 slice 와 비슷하지만, 다차원 배열에서의 사용이 조금 더 편리하다

### 4.1 Indexing

```python
arr = np.arange(25).reshape(5, 5)
print(arr)
'''
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
 '''
```

**Python 기본 Indexing 과 동일하다**

```python
print(arr[1][2])
# 7

```

**ndarray 에서 차이점은 [1, 2] 로 접근이 가능하다.**

```python
print(arr[1, 2])
# 7
```

---

### 4.2 Slicing

```python
# Python List 에서의 2차원 배열 slicing

# 2행부터 / 3열까지

arr = [[0, 1, 2, 3, 4], [5, 6, 7, 8, 9], [10, 11, 12, 13, 14], [15, 16, 17, 18, 19], [20, 21, 22, 23, 24]]
print([arr[:3] for arr in arr[2:]])
# [[10, 11, 12], [15, 16, 17], [20, 21, 22]]
```

```python
arr = np.arange(25).reshape(5, 5)
print(arr)
'''
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
 '''
```

```python
# 1번행 이상 / 3번행 미만, 2번 열 미만 출력
print(arr[1:3, :2])
'''
[[ 5  6]
 [10 11]]
 '''
```

```python
# 모든 행, 2번 열 이후 출력

print(arr[:, 2:])
'''
[[ 2  3  4]
 [ 7  8  9]
 [12 13 14]
 [17 18 19]
 [22 23 24]]
 '''
```

```python
# 모든 행 / 모든 열을 2칸씩 띄워서 출력

print(arr[:, ::2])
'''
[[ 0  2  4]
 [ 5  7  9]
 [10 12 14]
 [15 17 19]
 [20 22 24]]
 '''
```

```python
# 1번 행부터 끝까지, 2칸씩 띄워서 / 0번 열부터 4번 미만 열까지, 3열씩 띄워서 출력

## print(arr[1::2, 0:4:3])
'''
[[ 5  8]
 [15 18]]
'''
```

---

### 5. 배열 값 수정 & 복사하기

- Index 접근 후 수정은 기본 배열과 동일하게 하면 된다.
- Numpy 도 마찬가지로 python 기반이기 때문에 얕은 복사(Shallow Copy)가 발생한다.
    - 깊은 복사: '실제 값'을 새로운 메모리 공간에 복사하는 것
    - 얕은 복사: '주소 값'을 복사
- 원본 배열을 수정하지 않으려면 `np.copy()` 함수를 사용하면 된다.

```python
arr = np.arange(15).reshape(3, 5)
print(arr)
'''
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]]
 '''
```

```python
# 값이 변경된다.
arr2 = arr
arr2[0][0] = 15
print(arr)
'''
[[15  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]]
'''
```

```python
arr = np.arange(15).reshape(3, 5)
arr2 = arr.copy()
arr2[0][0] = 15
print(arr)
'''
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]]
 '''
print(arr2)
'''
[[15  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]]
 '''
```
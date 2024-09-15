# 에러와 예외

## 디버깅

### 버그 `bug`

- 소프트웨어에서 발생하는 오류 또는 결함
- 프로그램의 예상된 동작과 실제 동작 사이의 불일치

버그의 기원

- 'Bug'라는 용어는 **소프트웨어 이전부터 공학 분야에서 사용**되었음
- 컴퓨터 분야에서의 첫 사용은 1947년 프로그래밍 언어의 일종인 코볼 발명자 그레이스 호퍼와 그녀의 팀이 컴퓨터의 릴레이에서 **실제 나방을 발견한 것이 시초**로 알려짐
- **하버드 Mark Ⅱ 컴퓨터 회로**에 실제 나방이 들어가 합선을 일으켜 비정상적으로 동작한 것을 기록한 것
- 발견된 나방은 컴퓨터 로그북에 테이프로 붙여서 보존되었고,
    
    "First actual case of bug being found" (실제 버그가 발견된 첫 사례)라는 메모가 남겨짐
    
- "버그"라는 용어는 이전부터 사용되어 왔지만 이 사건을 계기로 컴퓨터 시스템에서 발생하는 오류 또는 결함을 지칭하는 용어로 널리 사용되기 시작

실제 버그가 발견된 최초의 사례

![이미지](https://github.com/ragu6963/TIL/assets/32388270/ff6aa90f-a8e0-4ad4-b785-053f496b0864)

### Debugging

- 소프트웨어에서 **발생하는 버그를 찾아내고 수정하는 과정**
- 프로그램의 **오작동 원인을 식별하여 수정하는 작업**

디버깅 방법

1. **print 함수 활용**
    - 특정 함수 결과, 반복/조건 결과 등 나눠서 생각, 코드를 bisection으로 나눠서 생각
2. **개발 환경(text editor, IDE) 등에서 제공하는 기능 활용**
    - breakpoint, 변수 조회 등
3. **[Python tutor](https://pythontutor.com/) 활용** (단순 파이썬 코드인 경우)
4. **뇌 컴파일, 눈 디버깅 등**

## 에러

### 에러 `Error`

- 프로그램 실행 중에 발생하는 예외 상황

### 파이썬의 에러 유형

- **문법 에러 `Syntax Error`**
    - 프로그램의 구문이 올바르지 않은 경우 발생 (오타, 괄호 및 콜론 누락 등의 문법적 오류)
    - 프로그램 실행조차 되지 않음
- 예**외 `Exception`**
    - 프로그램 **실행 중에 감지**되는 에러

### 문법 에러 예시

- Invalid syntax (문법 오류)
    
    ```python
    while 
    # SyntaxError: invalid syntax
    ```
    
- assign to literal (잘못된 할당)
    
    ```python
    5=3 
    # SyntaxError: cannot assign to literal
    ```
    
- EOL (End of Line)
    
    ```python
    print('hello
    # SyntaxError: EOL while scanning string literal
    ```
    
- EOF (End of File)
    
    ```python
    print(
    # SyntaxError: unexpected EOF while parsing
    ```
    

## 예외

### 예외 `Exception`

- 프로그램 **실행 중에 감지되는 에러**

### 내장 예외 `Built-in Exceptions`

- 예외 상황을 나타내는 **예외 클래스들**
- 파이썬에서 이미 정의되어 있으며, 특정 예외 상황에 대한 처리를 위해 사용
    
    > 참고 문서 : https://docs.python.org/ko/3/library/exceptions.html#ValueError
    > 

### 내장 예외 예시

- `ZeroDivisionError`
    - 나누기 또는 모듈로 연산의 두 번째 인자가 0일 때 발생
        
        ```python
        10/0 
        # ZeroDivisionError: division by zero
        ```
        
- `NameError`
    - 지역 또는 전역 이름을 찾을 수 없을 때 발생
        
        ```python
        print(name_error) 
        # NameError: name 'name_error' is not defined
        ```
        
- `TypeError`
    - 타입 불일치
        
        ```python
        '2' + 2  
        # TypeError: can only concatenate str (not "int") to str
        ```
        
    - 인자 누락
        
        ```python
        sum()  
        # TypeError: sum() takes at least 1 positional argument (0 given)
        ```
        
    - 인자 초과
        
        ```python
        sum(1, 2, 3)  
        # TypeError: sum() takes at most 2 arguments (3 given)
        ```
        
    - 인자 타입 불일치
        
        ```python
        import random
        random.sample(1, 2)
        # TypeError: Population must be a sequence.  For dicts or sets, use sorted(d).
        ```
        
- `ValueError`
    - 연산이나 함수에 문제가 없지만 부적절한 값을 가진 인자를 받았고,
        
        상황이 IndexError 처럼 더 구체적인 예외로 설명되지 않는 경우 발생
        
        ```python
        int('1.5') 
        # ValueError: invalid literal for int() with base 10: '3.5'
        
        range(3).index(6) 
        # ValueError: 6 is not in range
        ```
        
- `IndexError`
    - 시퀀스 인덱스가 범위를 벗어날 때 발생
        
        ```python
        empty_list = []
        empty_list[2]
        # IndexError: list index out of range
        ```
        
- `KeyError`
    - 딕셔너리에 해당 키가 존재하지 않는 경우
        
        ```python
        person = {'name': 'Alice'}
        person['age']  
        # KeyError: 'age'
        ```
        
- `ModuleNotFoundError`
    - 모듈을 찾을 수 없을 때 발생
        
        ```python
        import hahaha  
        # ModuleNotFoundError: No module named 'hahaha'
        ```
        
- `ImportError`
    - 임포트 하려는 이름을 찾을 수 없을 때 발생
        
        ```python
        from random import hahaha
        # ImportError: cannot import name 'hahaha' from 'random'
        ```
        
- `KeyboardInterrupt`
    - 사용자가 Control-C 또는 Delete를 누를 때 발생
    - 무한루프 시 강제 종료
        
        ```python
        while True:
            continue
        
        '''
        Traceback (most recent call last):
          File "...", line 2, in <module>
            continue
        KeyboardInterrupt
        '''
        ```
        
- `IndentationError`
    - 잘못된 들여쓰기와 관련된 문법 오류
        
        ```python
        for i in range(10):
            print(i) 
        # IndentationError: expected an indented block
        ```
        

**실행 해보기**

```
# 실행 해보기 1
10/0
```

```
# 실행 해보기 2
print(name_error)
```

```
# 실행 해보기 3
'2' + 2
```

```
# 실행 해보기 4
sum()
```

```
# 실행 해보기 5
sum(1, 2, 3)
```

```
# 실행 해보기 6
import random
random.sample(1, 2)
```

```
# 실행 해보기 7
int('1.5')
```

```
# 실행 해보기 7
range(3).index(6)
```

```
# 실행 해보기 8
empty_list = []
empty_list[2]
```

```
# 실행 해보기 9
person = {'name': 'Alice'}
person['age']
```

```
# 실행 해보기 10
import hahaha

```

```
# 실행 해보기 11
from random import hahaha
```

```
# 실행 해보기 12
for i in range(10):
print(i)
```

## 예외 처리

- 예외가 발생했을 때 프로그램이 비정상적으로 종료되지 않고,
    
    적절하게 처리할 수 있도록 하는 방법
    

### 예외 처리 사용 구문

- **`try`**
    - 예외가 발생할 수 있는 코드 작성
- **`except`**
    - 예외가 발생했을 때 실행할 코드 작성
- **`else`**
    - 예외가 발생하지 않았을 때 실행할 코드 작성
- **`finally`**
    - 예외 발생 여부와 상관없이 항상 실행할 코드 작성
    
    ```python
    try:
        x = int(input('숫자를 입력하세요: '))
        y = 10 / x
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except ValueError:
        print('유효한 숫자가 아닙니다.')
    else:
        print(f'결과: {y}')
    finally:
        print('프로그램이 종료되었습니다.')
    ```
    

### try & except

- **try** 블록 안에는 **예외가 발생할 수 있는 코드를 작성**
- **except** 블록 안에는 **예외가 발생했을 때 처리할 코드를 작성**
- **예외가 발생하면** 프로그램 흐름은 try 블록을 빠져나와 **해당 예외에 대응하는 except 블록으로 이동**
- except 뒤에 **예외를 작성하지 않으면** **모든 예외 오류에 반응**
    
    ```python
    try:
        # 예외가 발생할 수 있는 코드
    
    except 예외:
        # 예외 처리 코드
    ```
    

**예외 처리 예시**

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
# 0으로 나눌 수 없습니다.

try:
    num = int(input('숫자입력 : '))
except ValueError:
    print('숫자가 아닙니다.')

"""
숫자입력 : a
숫자가 아닙니다.
"""
```

**복수 예외 처리**

### 복수 예외 처리 연습 (1/4)

- 100을 사용자가 입력한 값으로 나누고 출력하는 코드를 작성해보시오.
    - 먼저, 발생 가능한 에러가 무엇인지 예상해보기
        
        ```python
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
        ```
        

### 복수 예외 처리 연습 (2/4)

- 100을 사용자가 입력한 값으로 나누고 출력하는 코드를 작성해보시오.
    - 먼저, 발생 가능한 에러가 무엇인지 예상해보기
        
        ```python
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
        
        # int(’a’)
        # 100/int(’0’)
        ```
        

### 복수 예외 처리 연습 (3/4)

- 100을 사용자가 입력한 값으로 나누고 출력하는 코드를 작성해보시오.
    - 먼저, 발생 가능한 에러가 무엇인지 예상해보기
        
        ```python
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
        
        """
        int(’a’)
        문자열을 int로 형변환 : ValueError
        """
        
        """
        100 / 0
        0으로 숫자를 나눔 : ZeroDivisionError
        """
        ```
        

### 복수 예외 처리 연습 (4/4)

- 100을 사용자가 입력한 값으로 나누고 출력하는 코드를 작성해보시오.
    - 발생가능한 에러를 모두 명시하거나 & 별도로 작성하기
    - 모두 명시
        
        ```python
        try:
            num = int(input('100으로 나눌 값을 입력하시오 : '))
            print(100 / num)
        except (ValueError, ZeroDivisionError):
            print('제대로 입력해주세요.')
        ```
        
    - 별도 작성
        
        ```python
        try:
            num = int(input('100으로 나눌 값을 입력하시오 : '))
            print(100 / num)
        except ValueError:
            print('숫자를 넣어주세요.')
        except ZeroDivisionError:
            print('0으로 나눌 수 없습니다.')
        except:
            print('에러가 발생하였습니다.')
        ```
        

### else & finally

- `else`
    - 예외가 발생하지 않았을 때 추가 작업을 진행
- `finally`
    - 예외 발생 여부와 상관없이 항상 실행할 코드를 작성
    
    ```python
    try:
        x = int(input('숫자를 입력하세요: '))
        y = 10 / x
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except ValueError:
        print('유효한 숫자가 아닙니다.')
    else:
        print(f'결과: {y}')
    finally:
        print('프로그램이 종료되었습니다.')
    ```
    

**참고**

**예외 처리 주의사항**

### 내장 예외의 상속 계층구조 주의 (1/2)

- 아래와 같이 예외를 작성하면 코드는 2번째 except 절에 이후로 도달하지 못함
    
    ```python
    try:
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
    except BaseException:
        print('숫자를 넣어주세요.')
    # 하단 블록에 도달하지 못함
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except:
        print('에러가 발생하였습니다.')
    ```
    

### 내장 예외의 상속 계층구조 주의 (2/2)

- 내장 예외 클래스는 상속 계층구조를 가지기 때문에
    
    except 절로 분기 시 반드시 하위 클래스를 먼저 확인 할 수 있도록 작성해야 함
    
    ```python
    try:
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
    except BaseException: # 하위 예외 클래스 확인 필요
        print('숫자를 넣어주세요.')
    except ZeroDivisionError: # 하위 예외 클래스 확인 필요
        print('0으로 나눌 수 없습니다.')
    except:
        print('에러가 발생하였습니다.')
    ```
    
    ![이미지](https://github.com/ragu6963/TIL/assets/32388270/6ce033c9-6715-473f-a6c2-9e2288361a1a)
    

> 참고 문서 : https://docs.python.org/ko/3/library/exceptions.html#exception-hierarchy
> 

### 예외 객체 다루기

### `as` 키워드

- 예외객체
    - 예외가 발생했을 때 예외에 대한 정보를 담고 있는 객체
- `except` 블록에서 예외 객체를 받아 상세한 예외 정보를 활용 가능
    
    ```python
    my_list = []
    
    try:
        number = my_list[1]
    except IndexError as error:
        print(f'{error}가 발생했습니다.')
    
    # list index out of range가 발생했습니다.
    ```
    

### try-except와 if-else

- `try-except`와 `if-else`를 함께 사용할 수 있음
    
    ```python
    try:
        x = int(input('숫자를 입력하세요: '))
        if x < 0:
            print('음수는 허용되지 않습니다.')
        else:
            print('입력한 숫자:', x)
    except ValueError:
        print('오류 발생')
    ```
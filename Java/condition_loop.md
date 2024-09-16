# 조건문

## if 조건문

### if

`if`는 특정 조건이 참인지 확인하고, 그 조건이 `true`인 경우 특정 코드 블록을 실행함

```java
// 기본 구조

if (condition) {
    // 조건이 참일 때 실행되는 코드
}
```

### else

`else` 는 `if` 문에서 만족하는 조건이 없을 때 실행하는 코드를 제공

```java
// if - else 기본 구조

if (condition) {
    // 조건이 참일 때 실행되는 코드
} else {
    // if문에서 만족하는 조건이 없었을 경우 실행되는 코드
}
```

### else if

`else if` 문은 앞선 `if`문의 조건이 거짓일 때 다음 조건을 검사
만약 앞선 `if` 문이 참이라면 `else if`를 실행하지 않음

```java
// if - else if - else 기본 구조

if (condition1) {
    // 조건 1이 참일 때 실행되는 코드
} else if (condition2) {
    // 조건1이 거짓이고, 조건 2가 참일 때 실행되는 코드
} else if (condition3) {
    // 조건 1과 2가 거짓이고, 조건 3이 참일 때 실행되는 코드
} else {
    // 위 조건문에서 만족하는 조건이 없었을 경우 실행되는 코드
}
```

### 참고 : if문 중괄호 생략

- `if` 문 다음에 실행할 명령이 하나만 있을 경우에는 `{}` 를 생략할 수 있음.
- `else if` , `else` 도 마찬가지임
- 명령이 2개 이상이라면 사용 불가능함.
- 안 쓰는 게 좋다.

### 주의

- `if` 에 `else if` 를 함께 사용하는 것은 서로 연관된 조건일 때 사용해야 함
- 만약 관련이 없는 독립 조건이면 (각각의 조건에 대해 별도의 작업을 수행해야 할 경우)
`else if` 를 사용하지 않고 `if` 문을 각각 따로 사용해야 함

## Switch 조건문

- if문에 비해 간결한 코드를 작성 가능함
- `switch` 문의 조건에는 참 거짓의 결과가 아니라, 단순히 값만 넣을 수 있음.

### 일반적인 switch문

```java
package condition;

public class Switch1 {

    public static void main(String[] args) {
        // if문 사용
        // if문은 [참 / 거짓]의 결과가 나오는 조건식을 자유롭게 적을 수 있음
        /*
        int grade = 2;
        int coupon;
        if (grade == 1) {
            coupon = 1000;
        } else if (grade == 2) {
            coupon = 2000;
        } else if (grade == 3) {
            coupon = 3000;
        } else {
            coupon = 500;
        }
        System.out.println("발급받은 쿠폰: " + coupon + "원");
        */

        // switch문 사용
        // 단순한 if문과 같음: 하지만 값이 같은 경우에만 사용 가능함 (특정 case와 같은지만 체크할 수 있음)
        // case -> if / else if | default -> else
        // break가 없으면 다음 case를 그대로 수행하게 되니까 까먹지 말 것
        int grade = 3;
        int coupon;

        switch (grade) {
            case 1:
                coupon = 1000;
                break;
            case 2:
                coupon = 2000;
                break;
            case 3:
                coupon = 3000;
                break;
            default:
                coupon = 500;
        }
        System.out.println("발급받은 쿠폰: " + coupon + "원");
    }
}
```

### 새로운 switch문 (JAVA 14 이상)

- 기존 switch문보다 더 간결한 코드 작성이 가능함

**차이점**

- `->` 를 사용함
- 선택된 데이터를 반환할 수 있음

```java
package condition;

public class Switch2 {

    public static void main(String[] args) {
        // JAVA14에 등장한 새로운 switch문 사용
        // -> 사용
        // 선택된 데이터를 반환할 수 있음
        int grade = 0;

        int coupon = switch (grade) {
            case 1 -> 1000;
            case 2 -> 2000;
            case 3 -> 3000;
            default -> 500;
        };
        System.out.println("발급받은 쿠폰: " + coupon + "원");
    }
}
```

## 삼항 연산자

단순히 참 / 거짓 여부에 따라 특정 값을 구하는 경우에 사용 가능함

```
(조건) ? 참_표현식 : 거짓 표현식
[항이 3개] -> 삼항 연산자    
```

```java
package condition;
 
public class CondOp1 {
    // 삼항 연산자
    public static void main(String[] args) {
        // 아래 예제는 참과 거짓에 따라 status 변수 값이 달라짐
        // 이처럼 단순히 참과 거짓에 따라 특정 값이 정해지는 경우: 삼항 연산자 or 조건 연산자를 사용 가능함
        // ?:
        /*
        int age = 18;
        String status;
        if (age >= 18) {
            status = "성인";
        } else {
            status = "미성년자";
        }
        System.out.println("age = " + age + ", status = " + status);
        */

        // 삼항 연산자 사용
        // (조건), ?_참 표현식, :_거짓 표현식 <- 항이 3개
        // ? <- 조건이 참이면 | : <- 조건이 거짓이면
        int age = 18;
        String status = (age >= 18) ? "성인" : "미성년자";
        System.out.println("age = " + age + ", status = " + status);
    }
}
```

---

# 반복문

특정 코드를 반복해서 실행할 때 사용

## While 반복문

**반복문을 사용하지 않은 코드**

```java
package loop;

public class While1_1 {
    // 1을 한 번씩 더해서 총 3번 더하는 코드 만들기
    public static void main(String[] args) {
        int a = 1;
        System.out.println("현재 숫자는 " + a);
        a++;
        System.out.println("현재 숫자는 " + a);
        a++;
        System.out.println("현재 숫자는 " + a);
    }
}
```

**반복문을 사용한 코드**

```java
package loop;

public class While1_2 {
    // 반복문 While
    public static void main(String[] args) {
        int a = 0;

        while (a < 3) {
            a++;
            System.out.println("현재 숫자는: " + a);
        }
        System.out.println("While문 탈출!");
    }
}
```

**반복문 사용의 장점**

- 중복된 코드의 반복이 감소
- 유지 보수, 가독성 증가

### While 절차

```java
while (조건식) {
    // 코드
}
```

1. 조건식을 확인, 거짓이면 while문을 탈출함
2. 조건식이 참이면 코드 블럭을 실행하고 다시 조건식 검사로 돌아감

### while 예제 CODE

```java
package loop;

public class While2_1 {
    // 1부터 하나씩 증가하는 수를 3번 더하라
    public static void main(String[] args) {
        int sum = 0;
        int target = 0;
        int cnt = 0;
        int targetCnt = 100;

        while (cnt < targetCnt) {
            cnt++;
            target++;
            sum += target;
            System.out.println("target = " + target + " sum = " + sum);
        }
    }
}
```

## do-while 반복문

`do-while` 문은 `while` 문과 비슷하지만, 조건에 상관없이 무조건 한 번은 코드를 실행함

→ 최초 한 번은 코드 블럭을 실행해야 하는 경우 사용하면 됨

### do-while 절차

```java
do {
    // 코드
} while (조건식);
```

1. 최초로 `do {}` 안에 있는 코드 블럭을 실행
2. 이후 조건식을 검증. 참이면 `do {}` 블럭으로 되돌아가고, 거짓이면 `do-while`  탈출

### do-while 예제 CODE

```java
package loop;

public class DoWhile1 {

    public static void main(String[] args) {
        //do-while문은 while문과 유사하지만, 조건에 상관없이 무조건 한 번은 코드를 실행한다는 차이가 있다.
        int i = 10;
        while (i < 3) {
            System.out.println("while 현재 숫자는: " + i);
            i++;
        }

        int i2 = 10;
        do {
            System.out.println("do-while 현재 숫자는: " + i2);
            i2++;
        } while (i2 < 3);
        // do-while문의 경우는 우선 do문을 먼저 실행한 후 뒤에 있는 while 내의 조건문을 확인함
        // 만약 조건문이 참이면, do 블럭으로 되돌아가서 반복을 수행하고, 거짓이면 반복을 종료함
        // do-while문은 최초 한 번은 코드 블럭을 꼭 실행해야 하는 경우에 사용하면 된다
    }
}
```

## break, continue

`break` : 반복문을 즉시 종료하고 탈출

`continue` : 반복문의 나머지 부분을 건너뛰고, 다음 반복으로 넘어감

### break 예제 CODE

```java
package loop;

public class Break1 {

    public static void main(String[] args) {
        int sum = 0;
        int cnt = 1;

        while (true) {
            sum += cnt;
            if (sum > 10) {
                System.out.println("합이 10보다 크면 종료: sum = " + sum + " cnt = " + cnt);
                break;
            }
            cnt += 1;
        }
    }
}
```

### continue 예제 CODE

```java
package loop;

public class Continue1 {
    // 1부터 5까지의 숫자를 출력하는데, 숫자가 3일 때는 출력을 건너뛰어라
    public static void main(String[] args) {
        int num = 0;

        while (num < 5) {
            num++;
            if (num == 3) {
                continue;
            }
            System.out.println(num);
        }
    }
}
```

## for 반복문

`for` 도 `while` 과 같은 반복문임

`for` 는 주로 반복 횟수가 정해져 있을 때 사용함

### for문 구조 및 절차

```
for (1. 초기식; 2. 조건식; 4. 증감식) {
    // 3. 코드
} 
```

**절차**

1. **`초기식`**이 실행됨.
    1. 주로 반복 횟수와 관련된 변수를 선언하고 초기화 할 때 사용. (최초에 딱 한 번 사용됨)
2. **`조건식`**을 검증. 참이면 코드를 실행하고, 거짓이면 for문을 탈출함
3. 코드를 실행함
4. 코드가 종료되면 **`증감식`**을 실행함. 
    1. 주로 **`초기식`**에 넣은 반복 횟수와 관련된 변수의 값을 증가시킬 때 사용
5. 다시 2. **`조건식`**부터 시작

**구조**

- for문에서 **`초기식`, `조건식`, `증감식`**은 선택 요소
- 아래 코드와 같이 모두 생략해도 됨.
- 모두 생략할 경우 무한 반복하는 코드와 같음 `for ( ; ; ) {} == while (true) {}`

### for 예제 CODE

```java
package loop;

public class Continue1 {
    // 1부터 5까지의 숫자를 출력하는데, 숫자가 3일 때는 출력을 건너뛰어라
    public static void main(String[] args) {
        int num = 0;

        while (num < 5) {
            num++;
            if (num == 3) {
                continue;
            }
            System.out.println(num);
        }
    }
}
```

```java
package loop;

public class For2 {
    // i부터 하나씩 증가하는 수를 endNum(마지막 수)까지 더해라 (i ~ endNum 더하기)
    public static void main(String[] args) {
        int sum = 0;
        int endNum = 10;
        for (int i = 1; i <= endNum; i++) {
            sum += i;
            System.out.println("i=" + i + " sum=" + sum);
        }
    }
}
```

```java
package loop;

public class For3 {
    // for문에서 초기식, 조건식, 증감식은 선택이다. 다음과 같이 모두 생략해도 된다.
    // 단 생략해도 각 영역을 구분하는 세미 콜론(;)은 유지해야 함
    // for (; ; ) == while (true)
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; ; i++) {
            sum += i;
            if (sum > 10) {
                System.out.println("합이 10보다 크면 종료: i=" + i + " sum=" + sum);
                break;
            }
        }
    }
}

```

## for-each 반복문 (향상된 for문)

```java
// 향상된 for문, for-each문

for (int number : numbers) {
    System.out.println(number);
}
```

- 일반적인 for문과 동일하게 작동함
- 향상된 for문은 배열의 index를 활용하지 않고, 종료 조건을 주지 않아도 됨.
    
    → 단순히 해당 배열을 처음부터 끝까지 탐색함
    
- 조건 `( : )`
    - 왼쪽에는 반복할 때마다 찾은 값을 저장할 변수를 선언
    - 오른쪽에는 탐색할 배열을 선택

**배열의 index를 사용하지 않고도, 배열의 모든 요소를 순회할 수 있기 때문에 코드가 간결하고 가독성이 좋음**

### 향상된 for문을 사용하지 못하는 경우

- 향상된 for문에는 증가하는 index값이 감춰져 있음.
    - 이 index 값을 사용해야 하는 경우에는 사용할 수 없음.
- 모든 요소를 순회하기에 다 돌 때에는 쓸 필요 없음.

### 향상된 for문 예제 CODE

```java
package array;

public class EnhancedFor1 {
    // 향상된 for문 : 각각의 요소를 탐색한다는 의미에서 'for-each'문이라고도 부름
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        // 일반 for문
        for (int i = 0; i < numbers.length; i++) {
            System.out.print(numbers[i] + " ");
        }
        System.out.println();

        // 향상된 for문 [for-each문]
        // for (반복할 때마다 찾은 값을 저장할 변수 선언 : 탐색할 배열) {}
        // 단축키 : iter
        for (int number : numbers) {
            System.out.print(number + " ");
        }
        System.out.println();

        /*
        향상된 for문은 배열의 index를 사용하지 않고, 종료 조건을 주지 않아도 해당 배열의 처음부터 끝까지 탐색함
        for (반복할 때마다 찾은 값을 저장할 변수 선언 : 탐색할 배열) {}
        향상된 for문은 배열의 index를 사용하지 않고도 배열의 요소를 순회할 수 있기에 코드가 간결하고 가독성이 좋음
        다만 index 값을직접 사용해야하는 경우에는 for-each문을 사용할 수 없음.
         */
    }
}

```

## 중첩 반복문

반복문 내부에 또 반복문을 만들 수 있음

`for`, `while` 둘 다 가능함

```java
package loop;

public class Nested1 {
    // 중첩 반복문
    public static void main(String[] args) {
        for (int i = 0; i <= 2; i++) {
            System.out.println("외부 for 시작: i=" + i);
            for (int j = 0; j <= 2; j++) {
                System.out.println("-> i=" + i + ", j=" + j);
            }
            System.out.println(("외부 for 종료: i=" + i));
            System.out.println();
        }
    }
}

/*
외부 for 시작: i=0
-> i=0, j=0
-> i=0, j=1
-> i=0, j=2
외부 for 종료: i=0

외부 for 시작: i=1
-> i=1, j=0
-> i=1, j=1
-> i=1, j=2
외부 for 종료: i=1

외부 for 시작: i=2
-> i=2, j=0
-> i=2, j=1
-> i=2, j=2
외부 for 종료: i=2
*/
```
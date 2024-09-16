# 메서드

**아래 코드는 아래와 같은 문제점이 있음**

- 같은 연산을 두 번 수행
- 연산 1과 연산 2 부분이 거의 같음

```java
package method;

import java.util.Scanner;

public class Method1 {
    // 아래의 코드는 같은 연산을 반복함. 코드도 거의 같음.
    public static void main(String[] main) {
        Scanner scanner = new Scanner(System.in);

        int a = scanner.nextInt();
        int b = scanner.nextInt();

        System.out.println(a + " + " + b + " 연산 수행");
        System.out.println("연산 1: " + a + " + " + b + " = " + (a + b));

        int x = scanner.nextInt();
        int y = scanner.nextInt();

        System.out.println(x + " + " + y + " 연산 수행");
        System.out.println("연산 2: " + x + " + " + y + " = " + (x + y));
    }
}
```

**위와 같은 문제점을 해결하려면 아래와 같이 메서드를 사용하면 됨**

→ 중복이 제거되고 코드가 간결해짐

```java
package method;

import java.util.Scanner;

public class Method1Ref {
    // 간결하지 못한 [Method1]의 코드를 함수를 사용해서 수정하자
    // java에서는 함수를 매서드라고 부름. 매서드도 함수의 한 종류라고 보면 됨
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        for (int cnt = 1; cnt <= 2; cnt++) {
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            int rst = add(x, y);
            System.out.println("연산 " + cnt + ": " + x + " + " + y + " = " + (x + y));
        }
    }

    // add 매서드 만들기
    // 매서드 이름, 반환 타입, 매개변수 목록을 포함
    public static int add(int a, int b) {
        System.out.println(a + " + " + b + " 연산 수행");
        return (a + b);
    }

    /*
    제어자: public, static과 같은 부분
    public: 다른 클래스에서 호출할 수 있는 매서드라는 뜻
    static: 객체를 생성하지 않고 호출할 수 있는 정적 매서드라는 뜻

    반환 타입: 만약 반환하는 값이 없는 메서드의 경우 void를 사용
    int: 반환 타입을 정의 -> 실행 결과를 사용할 반환 타입 지정
    add: 매서드 이름 -> 이 이름으로 호출할 수 있음
    (int a, int b): 입력한 인자(인수)를 전달받아 입력 값 정의, 해당 매서드 안에서만 사용되는 변수이며, 파라미터, 매개변수라 함
     */
}
```

## 메서드 정의

**함수를 정의하는 것과 같이 메서드를 정의한다고 표현**

```java
public static int add(int a, int b) {
    System.out.println(a + " + " + b + " 연산 수행");
    return (a + b);
}
```

### 메서드 선언

```java
**public static int add(int a, int b) :** 
```

- **`public static`**
    - `public` : 다른 클래스에서 호출할 수 있는 메서드라는 뜻
    - `static` : 객체를 생성하지 않고 호출할 수 있는 정적 메서드라는 뜻

- **`int add(int a, int b)`**
    - `int` : 메서드의 실행 결과를 반환할 때 사용할 반환 타입을 지정
    - `add` : 메서드에 이름을 부여, 이 이름으로 메서드를 호출할 수 있음
    - `(int a, int b)` : 메서드를 호출할 때 전달하는 입력 값을 정의 (매개 변수 : parameter)

### 메서드 본문

```java
{    
    System.out.println(a + " + " + b + " 연산 수행");
    return (a + b);
}
```

- 메서드가 수행해야하는 코드 블록
- 메서드를 호출하면 메서드 본문이 순서대로 실행됨
- 메서드 본문은 블랙박스임 :
    - 메서드를 호출하는 곳에서는 메서드 선언은 알지만, 메서드 본문은 모름
- 메서드의 실행 결과를 반환하려면 return문을 사용해야 함.
    - return문 다음에 반환할 결과를 적어주면 됨

### 메서드 호출과 용어 정리

```java
int sum1 = add(5, 10);
int sum2 = add(10, 20);
```

- 메서드를 호출해서 실행하려면 메서드 이름에 인자(인수)를 입력하면 됨
- 메서드를 호출할 때는 넘기는 값과 매개변수의 타입이 맞아야 함. (순서와 개수도 포함)

```java
call("hello", 20)

public static int call(String str, int age) {
    return age;
}
```

**Argument `인수` , `인자`**

- 위 코드에서와 같이 `"hello"`, `20` 처럼 넘기는 값을 인자라고 함
- 들어가는 수라는 의미: 메서드 내부로 들어가는 값을 의미

**Parameter `매개변수`**

- 함수를 정의할 때 선언한 변수인 `String str`, `int age`를 매개변수라고 함
- 메서드를 호출할 때 인수를 넘기면, 그 인수가 매개변수에 대입됨
- 중간에서 전달하는 변수라는 의미를 가짐:
    - 메서드 호출부와 메서드 내부 사이에서 값을 전달하는 역할
    - 메서드 내부에서만 사용됨

### 메서드 구조 상세

```java
public static int add(int a, int b) {
    // 메서드 본문, 실행 코드
}

제어자 반환타입 메서드 이름(매개 변수 목록) {
    // 메서드 본문
}
```

- **제어자(Modifier)** :
    - `public` `static` 과 같은 부분
- **반환 타입(Return type) :**
    - 메서드가 실행된 후 반환하는 데이터의 타입을 지정
    - 반환 데이터가 없을 경우 `void` 사용
- **메서드 이름(Method Name):**
    - 메서드를 호출할 때 사용하는 이름
- **매개 변수(Parameter):**
    - 입력 값 → 메서드 내부에서 사용할 수 있는 변수
    - 매개 변수는 option : 입력 값이 필요 없는 메서드는 매개 변수를 지정하지 않아도 됨
- **메서드 본문(Method body) :**
    - `{}` 사이에 실제 메서드의 코드가 위치

### 매개 변수가 없거나 반환 타입이 없는 경우

```java
package method;

public class Method2 {

    public static void main(String[] args) {
        printHeader(1);
        System.out.println("= 프로그램이 동작합니다. =");
        printFooter(1);
    }

    // 반환 타입이 없는 함수
    public static void printHeader(int a) {
        System.out.println("= " + a + "번 프로그램을 시작합니다 =");
        return;
    }

    // 반환 타입 void의 경우에는 return을 생략해도 됨. (알아서 마지막에 java가 삽입해 줌)
    // 반환 타입이 있다면 return은 필수
    public static void printFooter(int a) {
        System.out.println("= " + a + "번 프로그램을 종료합니다 =");
    }
}
```

**매개변수가 없는 경우**

- **선언:** `public static void printHeader()` 와 같이 매개변수를 비워두고 정의하면 됨
- **호출:** `printHeader();` 와 같이 인수를 비워두고 호출하면 됨

**반환 타입이 없는 경우**

- **선언:** `public static void printHeader()` 와 같이 반환 타입을 `void`로 지정하면 됨
- **호출:** `printHeader();` 와 같이 메서드만 호출하고 반환 값을 받지 않으면 됨
    - `String str = printHeader();` ← 오류 발생
    - **단 반환 타입이 있는 메서드를 호출했는데, 반환 값이 필요 없다면 사용하지 않아도 됨**

## return

**반환 타입이 `void` 인 경우에는 `return;` 을 생략해도 됨**

→ Java가 `return` 을 마지막 줄에 넣어주는 것

**→ 반환 타입이 있으면 반드시 `return;` 을 사용해서 값을 반환해야 함**

```java
package method;

import java.util.Scanner;

public class MethodReturn1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int i = scanner.nextInt();
        boolean rst = odd(i);
        System.out.println("숫자 " + i + "는 홀수인가? " + rst);
    }

    public static boolean odd(int i) {
        return (i % 2 == 0) ? false : true;
    }
}
```

**return 문을 만나면 그 즉시 메서드를 탈출함**

```java
package method;

public class MethodReturn2 {

    public static void main(String[] args) {
        checkAge(12);
    }

    // ruturn을 만나면 그 즉시 매서드를 탈출함
    public static void checkAge (int age) {
        if (age < 18) {
            System.out.println(age + "세 미성년자는 출입이 불가능합니다");
            return;
        }
        System.out.println(age + "세, 입장하세요.");
    }
}
```

- 18세 미만인 경우, ‘미성년자는 출입이 불가능합니다’ 를 출력하고 return문이 수행됨
    
    → 다음 logic을 수행하지 않음
    
- 18세 이상의 경우 ‘입장하세요’를 출력하고 메서드가 종료됨
    - 반환 타입이 없는 `void` 형이기 대문에 return 생략 가능

## 메서드 호출과 값 전달

**JAVA는 항상 변수의 값을 복사해서 대입함**

→ 참조형도 동일: 참조형 변수에 있는 참조값을 복사해서 사용

```java
package method;

public class MethodValue2 {
    // 변수 이름이 같다면
    public static void main(String[] args) {
        int num = 5;
        System.out.println("1. changeNumber 호출 전, main num = " + num); // 5
        changeNumber(num);
        System.out.println("4. changeNumber 호출 후, main num = " + num); // 5
    }

    public static void changeNumber(int num) {
        System.out.println("2. changeNumber 변경 전, changeNumber num = " + num); // 5
        num = num * 2;
        System.out.println("3. changeNumber 변경 후, changeNumber num = " + num); // 10
    }
}

    /*
    1. changeNumber 호출 전, main num = 5
    2. changeNumber 변경 전, changeNumber num = 5
    3. changeNumber 변경 후, changeNumber num = 10
    4. changeNumber 호출 후, main num = 5
     */

    /*
    main()도 사실 매서드
    각각의 매서드 안에서 사용하는 변수는 서로 완전히 분리된 다른 변수: 이름이 같아도 다름
     */
```

**호출자의 변수 이름과 매개변수의 이름이 같아도 동일**

**→ `main()` 도 엄연히 메서드:** 

매개 변수의 이름이 같지만, 각각의 메서드 안에서 사용하는 변수는 완전히 분리된 다른 변수

```java
package method;

public class MethodValue2 {
    // 변수 이름이 같다면
    public static void main(String[] args) {
        int num = 5;
        System.out.println("1. changeNumber 호출 전, main num = " + num); // 5
        changeNumber(num);
        System.out.println("4. changeNumber 호출 후, main num = " + num); // 5
    }

    public static void changeNumber(int num) {
        System.out.println("2. changeNumber 변경 전, changeNumber num = " + num); // 5
        num = num * 2;
        System.out.println("3. changeNumber 변경 후, changeNumber num = " + num); // 10
    }
}

    /*
    1. changeNumber 호출 전, main num = 5
    2. changeNumber 변경 전, changeNumber num = 5
    3. changeNumber 변경 후, changeNumber num = 10
    4. changeNumber 호출 후, main num = 5
     */

    /*
    main()도 사실 매서드
    각각의 매서드 안에서 사용하는 변수는 서로 완전히 분리된 다른 변수: 이름이 같아도 다름
     */
```

**만약 메서드를 사용해서 값을 변경하려면?**

→ 메서드의 호출 결과를 반환 받아서 사용하면 됨

```java
package method;

public class MethodValue3 {
    // 매서드를 사용해서 값 변경하기
    public static void main(String[] args) {
        int num = 5;
        System.out.println("1. changeNumber 호출 전, main num = " + num); // 5
        num = changeNumber(num);
        System.out.println("4. changeNumber 호출 후, main num = " + num); // 10
    }

    public static int changeNumber(int num) {
        System.out.println("2. changeNumber 변경 전, changeNumber num = " + num); // 5
        num = num * 2;
        System.out.println("3. changeNumber 변경 후, changeNumber num = " + num); // 10
        return num;
    }
}

    /*
    1. changeNumber 호출 전, main num = 5
    2. changeNumber 변경 전, changeNumber num = 5
    3. changeNumber 변경 후, changeNumber num = 10
    4. changeNumber 호출 후, main num = 10
     */
```

## 메서드와 형변환

메서드를 호출할 때도 형변환이 적용됨

### 묵시적 형변환

- 메서드를 호출할 때 매개 변수에 값을 전달하는 것도 결국 변수에 값을 대입하는 것
    - **변수에서와 같이 자동 형변환이 적용됨**

```java
package method;

public class MethodCasting2 {
    // 매서드에서도 자동 형변환은 정상 작동함 (더 작은 범위에서 큰 범위로의 이동에서)
    public static void main(String[] args) {
        int number = 100;
        printDouble(number);
    }

    public static void printDouble(double d) {
        System.out.println("실수: " + d);
    }
}
```

### 명시적 형변환

- 메서드를 호출하는데 인자와 매개변수의 타입이 맞지 않다면?
    - 더 작은 범위로는 컴파일 오류 발생
    - 아래와 같이 명시적 형변환을 사용해서 호출해야 함

```java
package method;

public class MethodCasting1 {

    public static void main(String[] args) {
        double number = 1.5;
//        printNumber(number); >> double -> int는 묵시적 형변환 안 됨 (컴파일 오류)
        printNumber((int) number); // << 명시적 형변환 실시
    }

    public static void printNumber(int n) {
        System.out.println("숫자: " + n);
    }
}
```

## 메서드 오버로딩

**Java는 메서드의 이름 뿐만 아니라 매개 변수 정보를 함께 사용해서 메서드를 구분함**

**→ 이름이 같지만, 매개변수를 달리해서 다른 메서드를 정의할 수 있음**

### 오버로딩 규칙

- 메서드의 이름이 같아도 매개변수의 타입 및 순서가 다르면 오버로딩이 가능함
- 단 반환 타입이 다른 것은 인정하지 않음
- 메서드 시그니처(method signiture) = **`메서드 이름 + 매개변수 타입(순서)`**

**오버로딩 성공 예**

```java
add(int a, int b)         
add(int a, int b, int c) // 매개변수 개수가 다름
add(double a, double b)  // 매개변수 타입이 다름
```

**오버로딩 실패 예**

```java
// 반환 타입이 다른 것은 인정하지 않음 (메서드 시그니처가 같음)

int add(int a, int b)
double add(int a, int b)
```

### 메서드 오버로딩 예제 CODE

**매개 변수 개수가 다른 오버로딩**

```java
package method;

public class Overloading1 {
    // 매개변수 개수가 다른 오버로딩
    public static void main(String[] args) {
        System.out.println("1: " + add(1, 2));          // 1번 함수 호출
        System.out.println("2: " + add(1, 2, 3));    // 2번 함수 호출
        System.out.println("3: " + add(5, 2, 1));    // 2번 함수 호출
        System.out.println("4: " + add(5, 10));         // 1번 함수 호출
    }

    public static int add(int a, int b) {
        System.out.println("1번 함수 호출");
        return (a + b);
    }

    public static int add(int a, int b, int c) {
        System.out.println("2번 함수 호출");
        return (a + b + c);
    }
}

    /*
    java에서는 매서드를 구분할 때, 매서드 이름 뿐만 아니라 매개변수 정보까지 함께 사용해서 구분함
    따라서 매서드 이름이 같더라도 매개변수 타입의 구성이 다르다면 (순서, 타입) 다른 함수로 취급 가능하고 이럴 경우 오버로딩에 성공했다고 함
    하지만 반환 타입이 다르더라도 매서드 이름과 매개 변수 타입 구성이 같다면 오버로딩을 할 수 없으니 주의하자.
     */

    /*
    1번 함수 호출
    1: 3
    2번 함수 호출
    2: 6
    2번 함수 호출
    3: 8
    1번 함수 호출
    4: 15
     */
```

**매개변수의 타입이 다른 오버로딩**

```java
package method;

public class Overloading2 {
    // 매개변수의 타입이 다른 오버로딩
    public static void main(String[] args) {
        myMethod(1.2 , 1);  // 2번 함수 호출: 2.2
        myMethod(1, 1.5);   // 1번 함수 호출: 2.5
        myMethod(2, 2.5);   // 1번 함수 호출: 4.5
        myMethod(2.5, 0);   // 2번 함수 호출: 2.5
    }

    public static void myMethod(int a, double b) {
        System.out.println("1번 함수 호출: " + (a + b));
    }

    public static void myMethod(double a, int b) {
        System.out.println("2번 함수 호출: " + (a + b));
    }
}

```

```java
package method;

public class Overloading3 {
    // 본인의 타입에 최대한 맞는 매서드를 찾아서 실행한 후
    // 없다면, 형 변환 가능한 타입의 매서드를 찾아서 실행함
    public static void main(String[] args) {
        System.out.println("1: " + add(1, 2));      // 1번 호출 / 1: 3
                                                          // 만약 첫번째 add 매서드가 없다면: 자동 형변환 발생 후 2번 매서드 호출
                                                          // 2번 호출 / 1: 3.0

        System.out.println("2: " + add(1.2, 1.5));  // 2번 호출 / 2: 2.7
    }
    // 첫 번째 add 메서드: 두 정수를 받아서 합을 반환한다.
    public static int add(int a, int b) {
        System.out.println("1번 호출");
        return a + b;
    }
    // 두 번째 add 메서드: 두 실수를 받아서 합을 반환한다.
    // 첫 번째 메서드와 이름은 같지만, 매개변수의 유형이 다르다.
    public static double add(double a, double b) {
        System.out.println("2번 호출");
        return a + b;
    }
}
```
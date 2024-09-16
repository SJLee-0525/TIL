# 프로그램 실행

```java
 package javastart;
 
 public class HelloJava {
 
		 public static void main(String[] args) {
				 System.out.println("hello java");
	   }
 }
 
 // hello java
```

```java
package javastart;
```

- 패키지는 자바 파일을 구분하기 위한 폴더로 이해하면 됨
- `javastart` 이라는 패키지를 만들었다면, 
해당 패키지에 들어가는 JAVA파일 첫 줄에 `package javastart` 와 같이 소속된 패키지를 선언해줘야 함
- JAVA 파일이 위치하는 패키지와 `package javastart` 선언 위치가 같아야 함

```java
public class HelloJava
```

- `HelloJava`를 클래스라고 함.
- 단순하게는  [`HelloJava.java`](http://HelloJava.java) 라는 파일을 만들었다고 이핵하면 됨
- 파일명과 클래스 이름이 같아야 함.
- `{}` 블록을 사용해서 클래스의 시작과 끝을 나타냄

```java
public static void main(String[] args)
```

- `main` 매서드라고 함.
- JAVA는 `main(String[] args)` 매서드를 찾아서 프로그램을 시작함
- `main` 매서드는 프로그램의 시작점이라고 이해하면 됨
- `{}` 블록을 사용해서 클래스의 시작과 끝을 나타냄

---

# 주석

- 한 줄 주석
    - `//` 기호로 시작함. 이후의 모든 텍스트는 주석으로 처리됨
- 여러 줄 주석
    - `/*` 로 시작하고 `*/` 로 끝냄. 이 사이의 모든 텍스트는 주석으로 처리됨
    

---

# 변수

## 변수 선언과 초기화

```java
package variable;

public class Var3 {
    public static void main(String[] args) {
        int a;  // 변수 선언
        a = 10; // 변수  초기화 a(10)
        System.out.println(a);

        a = 50; // 변수 값 변경 a(10 -> 50)
        System.out.println(a);
    }
}
```

### 변수 선언

- 변수를 선언하면 컴퓨터의 메모리 공간을 확보해서 그곳에 데이터를 저장할 수 있음
- 변수의 이름을 통해서 해당 메모리 공간에 접근할 수 있음
- 데이터를 보관할 수 있는 공간을 만들고, 이름을 부여함
- 변수는 아래와 같이 하나씩 선언할 수도 있고, 여러 변수를 한 번에 선언할 수도 있음
    
    ```java
    package variable;
    
    public class Var5 {
        public static void main(String[] args) {
            int a;  // 변수 선언
            a = 1;  // 변수 초기화
            System.out.println(a);
    
            int b = 2;  // 변수 선언과 초기화 동시에 하기
            System.out.println(b);
    
            int c = 3, d = 4;   // 여러 변수 선언과 초기화를 한 번에 하기
            System.out.println(c);
            System.out.println(d);
        }
    }
    ```
    

### 변수 초기화

- 변수는 초기화 해야함
- 초기화 하지 않으면 아래와 같은 에러 발생
    
    ```java
    package variable;
    
    public class Var6 {
        public static void main (String[] args) {
            int a;
    //        System.out.println(a); // java: variable a might not have been initialized
    //        지역 변수는 반드시 초기화 해줘야 함
        }
    }
    ```
    
- 변수를 선언하면 메모리 상의 어떤 공간을 차지하고 사용.
- 그 공간에 어떤 값이 있었는지는 모르기 때문에 초기화를 하지 않으면 원치 않는 값이 출력될 수 있음
- 이를 방지하기 위해 JAVA에서는 변수를 초기화하도록 강제함

## 변수 타입

- 데이터를 다루는 종류에 따라 다양한 변수 형식이 존재함

```java
package variable;

public class Var7 {
    public static void main(String[] args) {
        int a = 100;        // 정수 literal
        double b = 10.5;    // 실수 literal
        boolean c = true;   // true, false 입력 가능 boolean literal
        char d = 'A';       // 문자 하나 literal
        String e = "Hello Java"; // 문자열을 다루기 위한 특별한 타입 : 문자열 literal

        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
        System.out.println(e);

//        int z = "백원"; // java: incompatible types: java.lang.String cannot be converted to int
//        int y = "100"; // java: incompatible types: java.lang.String cannot be converted to int
    }
}
```

### 숫자 타입

- **정수**
    - `byte` : `-128 ~ 127 (2^8)`
    - `short` : `-32,768 ~ 32,767 (2^16)`
    - **`int` :  `-2,147,483,648 ~ 2,147,483,647 (약 20억) (2^32) << 기본`**
    - **`long` : `9223372036854775807L; (2^64), L을 붙여야 함. 소문자도 가능하되 권장하지 않음`**
    
- **실수**
    - `float` :  `float은 뒤에 f를 적어줘야 함 (4byte, 2^32), 7자리 정밀도`
    - **`double` : `float보다 더 넓은 범위를 표현 가능함 (8byte, 2^64) 15자리 정밀도 << 기본`**

- **문자**
    - `char` : `문자 하나를 취급, ' 작은 따옴표 하나를 사용해서 감싸야 함`
    - **`String` : `문자열을 다룸, " 큰 따옴표를 사용해서 감싸야 함`**

- **기타**
    - **`boolean` : `true와 false를 취급`**

```java
package variable;

public class Var8 {
    public static void main(String[] args) {
        // 정수
        byte b = 127; // -128 ~ 127 (2^8)
        short s = 32767; // -32,768 ~ 32,767 (2^16)
        int i = 2147483647; // -2,147,483,648 ~ 2,147,483,647 (약 20억) (2^32) << 기본
        long l = 9223372036854775807L; // (2^64), L을 붙여야 함. 소문자도 가능하되 권장하지 않음

        // 실수
        float f = 10.0f; // float은 뒤에 f를 적어줘야 함 (4byte, 2^32), 7자리 정밀도
        double d = 10.1; // double이 float보다 더 넓은 범위를 표현 가능함 (8byte, 2^64) 15자리 정밀도 << 기본

        // 기타
        boolean bl = false; // (1byte)
        char c = 'A'; // 문자열 하나 << String 쓰자
        String str = "Hello"; // 문자열 << String으로도 문자열 하나 표현 가능
        String stra = "A";

        System.out.println("정수형");
        System.out.println(b);
        System.out.println(s);
        System.out.println(i);
        System.out.println(l);

        System.out.println("실수형");
        System.out.println(f);
        System.out.println(d);

        System.out.println("기타");
        System.out.println(bl);
        System.out.println(c);
        System.out.println(str);
        System.out.println(stra);
    }
}
```

### 변수명 규칙

- **규칙:** 필수
    - 변수 이름은 숫자로 시작할 수 없음 (숫자를 포함하는 것은 가능함)
    - 공백이 들어갈 수 없음
    - JAVA의 예약어를 변수 이름으로 사용할 수 없음 (ex : int, class, public 등)
    - 변수 이름에는 영문자와 숫자, $, _ 만 사용 가능함

- **관례:** 필수는 아니지만 사실상 규칙
    - **낙타 표기법**
        - 클래스는 대문자로 시작 `Person`, `OrderDetail`
        - 나머지는 소문자로 시작 `firstName`, `userAccount`
        - 예외 :
            - 상수는 모두 대문자를 사용하고 언더바로 구분 `USER_LIMIT`
            - 패키지는 모두 소문자 사용 `org.spring.boot`
    - 변수 이름은 의미 있고 용도를 명확하게 설명할 수 있게 지어야 함

---

# 연산자

**계산을 수행하는 기호**

## 연산자와 피연산자

```java
3 + 4
```

- 연산자: `+`
- 피연산자: `3` , `4`

## 산술 연산자

### 산술 연산자 종류

- `+` : 더하기
- `-` : 빼기
- `*` : 곱하기
- `/` : 나누기 (몫)
- `%` : 나누기 (나머지)

### 숫자 연산

```java
// 숫자형의 연산자 코드

package operator;

public class Operator1 {
    public static void main(String[] args) {
        int a = 5;
        int b = 2;

        // 덧셈
        int plus = a + b;
        System.out.println("a + b = " + plus);

        // 뺄셈
        int min = a - b;
        System.out.println("a - b = " + min);

        // 곱셈
        int mul = a * b;
        System.out.println("a * b = " + mul);

        // 나눗셈 (몫) : 자바에서 같은 int형끼리 계산하면 결과도 같은 int형으로 나옴.
        // int는 정수형이기 때문에 소수점 이하를 포함할 수 없음. 나중에 형변환에서 다룰 것
        // 주의) 0으로 나눌 수 없음
        int div = a / b;
        System.out.println("a / b = " + div);

        // 나눗셈 (나머지)
        int mod = a % b;
        System.out.println("a % b = " + mod);
    }
}
```

### 문자열 더하기

- JAVA는 문자열에도 `+` 연산자를 사용 가능함
- 문자열에 `+` 연산자를 사용하면 두 문자를 연결할 수 있음
- String 타입에 다른 타입을 더하는 경우: 대상 타입을 문자열로 변경함
    
    → 쉽게 이야기해서 문자열에 더하는 것은 다 문자열이 됨
    

```java
package operator;

public class Operator2 {
    public static void main(String[] args) {
        // 문자열과 문자열 더하기
        String result1 = "Hello " + "World";
        System.out.println(result1);

        // 문자열과 문자열 더하기 2
        String str1 = "Hello";
        String str2 = "World";
        System.out.println(str1 + str2);

        // 문자열과 숫자 더하기
        String result2 = "a + b = " + 3; // int형 3이 String으로 형변환돼서 더해지는 것
        System.out.println(result2);

        // 문자열과 숫자 더하기 2
        int num = 20;
        String str3 = "a + b = ";
        String result4 = str3 + num;
        System.out.println(result4);
        // 쉽게 이야기해서 문자열에 더하는 것은 다 문자열이 됨
    }
}
```

## 증감 연산자

### 증감 연산자 종류

- `++` : 대상의 값을 1 증가시킴
- `--` : 대상의 값을 1 감소시킴

```java
package operator;

public class OperatorAdd1 {
    public static void main(String[] args) {
        int a = 0;

        a = a + 1;
        System.out.println("a = " + a); // 1

        a = a + 1;
        System.out.println("a = " + a); // 2
        
        ++a; // a = a + 1
        System.out.println("a = " + a); // 3

        ++a;
        System.out.println("a = " + a); // 4

        --a; // a = a - 1
        System.out.println("a = " + a); // 3
    }
}
```

### 전위, 후위 증감 연산자

**증감 연산자는 피연산자 앞에 두거나 뒤에 둘 수 있음**

**연산자의 위치에 따라 연산이 수행되는 시점이 달라짐**

- `++a` : 전위 (Prefix) 증감 연산자
    - 증감 연산이 먼저 수행된 후 나머지 연산이 수행됨
- `a++` : 후위 (Postfix) 증감 연산자
    - 다른 연산이 먼저 수행된 후 증감 연산이 수행됨

```java
package operator;

public class OperatorAdd2 {
    public static void main(String[] args) {
        // 전위 증감 연산자
        int a = 1;
        int b = 0;

        b = ++a; // a의 값을 먼저 증가시키고 증가된 값을 b에 대입
        System.out.println("a = " + a + ", b = " + b);
        // a = 2, b = 2

        // 후위 증감 연산자
        a = 1; // a 값을 다시 1로 지정
        b = 0; // b 값을 다시 0으로 지정

        b = a++; // a의 현재 값을 b에 먼저 대입하고, 그 후 a의 값을 증가
        System.out.println("a = " + a + ", b = " + b);
        // a = 2, b = 1
    }
}
```

## 비교 연산자

두 값을 비교하는 데 사용

비교 연산자를 사용하면 `true` / `false` 결과가 나옴 

→ 조건문과 결합되는 경우가 많음

### 비교 연산자 종류

- `==` : 동등성
- `!=` : 불일치
- `>` : 크다
- `<` : 작다
- `>=` : 크거나 같다
- `<=` : 작거나 같다

```java
package operator;

public class Comp1 {
    public static void main(String[] args) {
        int a = 2;
        int b = 3;

        System.out.println(a == b); // false
        System.out.println(a != b); // true
        System.out.println(a > b);  // false
        System.out.println(a < b);  // true
        System.out.println(a >= b); // false
        System.out.println(a <= b); // true

        int c = 3;
        int d = 3;
        System.out.println(c == d); // true

        // 결과를 boolean 변수에 담을 수 있음
        boolean rst = c != d;
        System.out.println(rst);    // false
    }
}
```

### 문자열 비교

문자열이 같은지 비교할 때는 `==` 가 아닌 `.equals()` 매서드를 사용해야 함.

`==` 를 사용할 경우 실패할 때가 있음

```java
package operator;

public class Comp2 {

    public static void main(String[] args) {
        // 문자열 비교는 == 사용하는 게 아니라, .equals() 매서드를 사용해야 함
        // == 를 사용하면 성공할 때도 있지만, 실패할 때도 있음
        String str1 = "문자열1";
        String str2 = "문자열2";

        boolean rst1 = "hello".equals("hello");   // literal 비교
        System.out.println(rst1);                 // true

        boolean rst2 = str1.equals("문자열1");     // 문자열 변수와 literal 비교
        System.out.println(rst2);                 // true

        boolean rst3 = str1.equals(str2);         // 문자열 변수 비교
        System.out.println(rst3);                 // false

        // 아래와 같이 ==로 비교해도 결과는 나옴. 하지만 안 되는 조건이 있기에 문자열 비교에 사용하지 말자
        System.out.println("Hello" == "Hello");   // true
    }
}
```

## 논리 연산자

`boolean` 형인 `true` / `false` 를 비교하는데 사용

### 논리 연산자 종류

- `&&` : `AND` 두 피연산자가 모두 참이면 참을 반환
- `||` : `OR` 두 피연산자 중 하나라도 참이면 참을 반환
- `!` : `NOT` 피연산자의 논리적 부정을 반환 : 참이면 거짓을, 거짓이면 참을 반환

```java
package operator;

import java.sql.SQLOutput;

public class Logical1 {

    public static void main(String[] args) {
        System.out.println("&&: AND 연산");
        System.out.println(true && true);   // true
        System.out.println(true && false);  // false
        System.out.println(false && true);  // false
        System.out.println(false && false); // false

        System.out.println("||: OR 연산");
        System.out.println(true || true);   // true
        System.out.println(true || false);  // true
        System.out.println(false || true);  // true
        System.out.println(false || false); // false

        System.out.println("!: NOT 연산");
        System.out.println(!true);
        System.out.println(!false);

        boolean a = true;
        boolean b = false;
        System.out.println(a && b);  //false
        System.out.println(a || b);  // true
        System.out.println(!a);      // false
        System.out.println(!b);      // true
        System.out.println(a && !b); // true
        System.out.println(!a || b); // false
    }
}
```

### 논리 연산자 활용

```java
package operator;

public class Logical2 {

    public static void main(String[] args) {
        int a = 15;

        // a는 10보다 크거나 같고 20보다 작다
        boolean result = a >= 10 && a < 20;
        System.out.println(result); // true
    }
}
```

## 대입 연산자

대입 연산자 `=` 는 값을 변수에 할당하는 연산자

대입 연산자를 사용하면 변수에 값을 할당할 수 있음

### 축약 (복합) 대입 연산자 종류

- `+=`
- `-=`
- `*=`
- `/=`
- `%=`

```java
package operator;

public class Assign1 {
    // 대입 연산자
    public static void main(String[] args) {
        int a = 5;
        a += 3;                         // a = 5 + 3
        System.out.println("a += 3 = " + a); // a += 3 = 8
        
        a -= 2;                         // a = 8 - 2
        System.out.println("a -= 2 = " + a); // a -= 2 = 6

        a *= 4;                         // a = 6 * 4
        System.out.println("a *= 4 = " + a); // a *= 4 = 24

        a /= 3;                         // a = 24 / 3
        System.out.println("a /= 3 = " + a); // a /= 3 = 8

        a %= 5;                         // a = 8 % 5
        System.out.println("a %= 5 = " + a); // a %= 5 = 3
    }
}
```
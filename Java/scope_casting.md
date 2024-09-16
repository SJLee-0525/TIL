# 스코프 (Scope)

변수는 선언한 위치에 따라 아래와 같이 분류됨

- 지역 변수
- 멤버 변수 (클래스 변수, 인스턴스 변수)

## 지역 변수

- 특정 지역에서만 사용할 수 있는 변수:
    
    → 특정 지역을 벗어나면 사용할 수 없음 
    
    → 자신이 선언된 블록 안에서만 생존하고, 선언된 코드 블록을 벗어나면 제거되고 접근할 수 없음
    

* 특정 지역: 해당 변수가 선언된 코드 블록 `{}`

### 지역 변수 예제 CODE

```java
package scope;

public class Scope1 {

    public static void main(String[] args) {
        int m = 10; // m 생존 시작
        if (true) { // for문도 비슷
            int x = 20; // x 생존 시작
            System.out.println("if m = " + m); // m 생존: 블록 내부에서 블록 외부는 접근 가능
            System.out.println("if x = " + x); // x 생존
        } // x 소멸
        System.out.println("main m = " + m); // m 생존
        // System.out.println("main x = " + x); // 오류 발생: 변수 x에 접근 불가
    } // m 소멸
}

/*
if m = 10
if x = 20
main m = 10
*/
```

### Scope의 존재 이유

- 특정 구역에서만 필요한 변수가 모든 코드 내에서 존재한다면 메모리 사용에 있어서 비효율적임
    
    → 복잡성 증가, 유지보수성 악화, 가독성 감소
    

### 정리

- 변수는 꼭 필요한 범위로 한정해서 사용하는 것이 좋음
→ 메모리를 저 효율적으로 사용하고 더 유지보수하기 좋은 코드를 만들 수 있음
- **좋은 프로그램은 무한한 자유가 있는 프로그램이 아니라, 적절한 제약이 있는 프로그램임**

# 형변환

- 작은 범위에서 큰 범위로는 값을 넣을 수 있음
    
    예) `int` → `long` → `double`
    
- 큰 범위에서 작은 범위로 값을 넣는다면 아래와 같은 문제가 발생할 수 있음
    - 소수점 버림
    - Overflow

## 자동 형변환

- 위와 같은 이유 때문에 작은 범위에서 큰 범위로의 대입은 허용됨
- 이러한 경우 개발자가 직접 형변환을 하지 않아도 됨
    
    **→ 이런 과정이 자동으로 일어나기 때문에 `자동 형변환` 혹은 `묵시적 형변환` 이라고 함**
    

### 자동 형변환 CODE

```java
package scope;

public class Casting1 {
    // 형변환: 작은 범위에서 큰 범위로는 값을 넣을 수 있음
    public static void main(String[] args) {
        int intVal = 10;
        long longVal;
        double doubleVal;

        longVal = intVal;           // int -> long
        // longVal = (long) intVal;
        System.out.println("longVal = " + longVal);

        doubleVal = intVal;         // int -> double
        System.out.println("doubleVal = " + doubleVal);

        /*
        doubleValue = intValue
        doubleValue = (double) intValue // 형 맞추기
        doubleValue = (double) 10       // 변수 값 읽기
        doubleValue = 10.0              // 형변환

        앞에 (double) 과 같이 적어주면 int 형이 double 형으로 변함. <- 형변환
        위와 같이 작은 범위에서 큰 범위 숫자 타입으로의 대입은 직접 형변환 하지 않아도 됨 (자동 형변환, 묵시적 형변환)
         */
        
        double doubleVal2 = 20L;    // long => double
        System.out.println("doubleVal2 = " + doubleVal2);
    }
}
```

## 명시적 형변환

큰 범위에서 작은 범위 대입은 **`명시적 형변환`**이 필요함

### 가정

`double` 형 자료를 `int` 형으로 대입한다고 가정

- `int` 형은 `double` 형보다 숫자의 표현 범위가 작고, 실수를 표현할 수 없음
- `double` 형 자료를 `int` 에 대입한다면 숫자가 손실 되는 문제가 발생할 수 있음
    
    → 큰 버그 유발 가능성: 이 때문에 JAVA는 컴파일 오류를 발생 시킴
    
- 하지만 개발자가 이러한 위험을 감수하고도 값을 대입하고 싶다면 강제로 값을 변경 가능함
- `intValue = (int) doubleValue;` < `(int)` 와 같이 괄호를 사용해 명시적으로 표현하면 가능
- 개발자가 직접 형변환 코드를 입력한다고 해서 **`명시적 형변환`** 이라고 함

### 명시적 형변환 에제 CODE

```java
package scope;

public class Casting2 {
    // 명시적 형변환 : 큰 범위에서 작은 범위로의 대입은 명시적인 형변환이 필요함
    public static void main(String[] args) {
        double doubleVal = 1.5;
        int intVal;
        
        // intVal = doubleVal;      // 컴파일 오류 발생
        intVal = (int) doubleVal;   // 명시적 형변환 : 개발자가 직접 형변환 코드를 입력
        System.out.println("intVal = " + intVal); // 원본 값은 1.5였지만, 1로 변경되어 값이 대입됨 (실수 표현 불가)
        System.out.println("doubleVal = " + doubleVal); // 당연히 doubleVal의 형과 값은 유지됨

        System.out.println((int) 10.5);
    }
}
```

## OVERFLOW

형 변환을 할 때 숫자를 표현할 수 있는 범위를 넘어서면 발생하는 문제

- 기존 범위를 초과해서 표현하게 되면 전혀 다른 숫자가 표현 → 오버 플로우 발생
- OVERFLOW가 발생하면 마치 시계가 한 바퀴 돈 것처럼 다시 처음부터 시작함
- OVERFLOW가 발생했을 때 이를 해결하려고 시간을 낭비하기보다는
단순히 대입하는 변수의 타입을 더 큰 사이즈의 타입으로 바꿔서 해결해야 함

### OVERFLOW 예제 CODE

```java
package scope;

public class Casting3 {
    public static void main(String[] args) {
        long maxIntVal = 2147483647;    // int의 최대 값
        long maxIntOver = 2147483648L;  // int의 최대 값 + 1

        int intVal;
        intVal = (int) maxIntVal;       // int의 최대 값을 초과하지 않기 때문에 문제 발생 X
        System.out.println("intVal = " + intVal);           // intVal = 2147483647

        int intValOver;
        intValOver = (int) maxIntOver;  // int의 최대 값을 초과했기 때문에 문제 발생 O
        System.out.println("intValOver = " + intValOver);   // intValOver = -2147483648 (Overflow 발생)
        // 오버플로우가 발생하면, 시계가 한 바퀴 돈 것처럼 다시 처음부터 시작한다.
        // 오버플로우 발생하는 것 자체가 문제, 해결하려고 하지 말고, 그냥 (long)으로 바꿔서 다시 담자
    }
}
```

## 계산과 형변환

형 변환은 대입 뿐만 아니라 계산을 할 때에도 발생

### 계산과 형변환의 경우

1. **같은 타입끼리의 계산은 같은 타입의 결과를 냄:**
    - `int` + `int` = `int`
    - `double` + `double` = `double`
2. **서로 다른 타입의 계산은 큰 범위로 자동 형변환이 발생함**
    - `int` + `long` = `long` + `long` = `long`
    - `int` + `double` = `double` + `double` = `double`

### 계산과 형변환 예시 CODE

```java
package scope;

public class Casting4 {
    
    public static void main(String[] args) {
        /*
        Java에서의 계산은 다음 2가지만 기억하자.
        1. 같은 타입끼리의 계산은 같은 결과를 냄:
            - int + int = int를, double + double = double의 결과가 나옴

        2. 서로 다른 타입의 계산은 큰 범위로의 자동 형변환이 발생함:
            int + long = long + long으로 자동 형변환이 발생
            int + double = double + double로 자동 형변환이 발생
         */

        int div1 = 3 / 2;       // 답은 1.5이지만 (int)형끼리의 계산이기 때문에 (int)형인 1이 나옴
        System.out.println("div1 = " + div1); // div1 = 1
        
        double div2 = 3 / 2;    // (int)형끼리의 연산을 마친 후: 1을 (double)에 대입하기에 1.0이 나옴
        System.out.println("div2 = " + div2); // div2 = 1.0
        
        double div3 = 3.0 / 2;  // 3.0은 (double)형임. (double) / (double)의 연산으로 자동 형변환 됨
        System.out.println("div3 = " + div3); // div3 = 1.5
        
        double div4 = (double) 3 / 2;
        System.out.println("div4 = " + div4); // div4 = 1.5

        int a = 3;
        int b = 2;
        double rst = (double) a / b; // == ((double) a) / b
        System.out.println("rst = " + rst);   // rst = 1.5
    }
}
```

## 형변환 정리

- 작은 범위에서 큰 범위로는 대입할 수 있음
    - 묵시적 형변환 / 자동 형변환
- 큰 범위에서 작은 범위로의 대입은 아래와 같은 문제 발생 가능함: 명시적 형변환을 사용
    - 소수점 버림
    - OVERFLOW
- 연산과 형변환
    - 같은 타입은 같은 결과를 냄
    - 서로 다른 타입은 큰 범위로의 자동 형변환이 발생
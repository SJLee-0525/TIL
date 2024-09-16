# Scanner

- **`System.out` 을 통해서 출력을 했듯이, [`System.in`](http://System.in) 을 통해 사용자의 입력을 받을 수 있음**
- **`System.in`을 이용해 사용자 입력을 받으려면 여러 과정을 거쳐야해서 복잡하고 어려움**
    
    **→ JAVA는 이러한 문제를 해결하기 위해 `Scanner` 라는 클래스를 제공 : `편리함`**
    

### 예시 CODE

```java
package scanner;

import java.sql.SQLOutput;
import java.util.Scanner;

public class Scanner1 {
    // 입력 받기
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("문자열을 입력하세요:");
        String str = scanner.nextLine();
        System.out.println("입력한 문자열: " + str);

        System.out.print("정수를 입력하세요:");
        int intVal = scanner.nextInt();
        System.out.println("입력한 정수: " + intVal);

        System.out.print("실수를 입력하세요:");
        double doubleVal = scanner.nextDouble();
        System.out.println("입력한 실수: " + doubleVal);
    }
}
```

- **`Scanner scanner = new Scanner(System.in);`**
    - 객체와 클래스를 배워야 정확히 이해 가능함
    - `Scanner`의 기능을 사용하기 위해 `new`를 이용해 `Scanner`를 만든다 정도로 이해
    - `Scanner`는 `System.in`을 사용해서 사용자의 입력을 편리하게 받도록 도와줌
- **`scanner.nextLine()`**
    - 엔터 `\n` 를 입력할 때까지 문자를 가져옴
- **`scanner.nextInt()`**
    - 입력을 `int` 형으로 가져옴. 정수 입력에 사용
- **`scanner.nextDouble()`**
    - 입력을 `double` 형으로 가져옴. 실수 입력에 사용

### 주의

- 다른 타입 입력시 오류 발생함.

### Scanner 예제 CODE

**두 수를 입력 받고 그 합을 출력**

```java
package scanner;

import java.util.Scanner;

public class Scanner2 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

//        System.out.print("첫번째 숫자를 입력하세요: ");
        int a = scanner.nextInt();
        int b = scanner.nextInt();
        System.out.println("입력한 두 수의 합: " + (a + b));
    }
}
```

**두 수를 입력 받고 더 큰 수를 출력**

```java
package scanner;

import java.util.Scanner;

public class Scanner3 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("숫자를 입력하세요.");
        int a = scanner.nextInt();
        int b = scanner.nextInt();

        if (a > b) {
            System.out.println("처음 입력한 " + a +"이(가) 더 큽니다.");
        } else if (a < b) {
            System.out.println("두번째에 입력한 " + b + "이(가) 더 큽니다.");
        } else {
            System.out.println("두 숫자 " + a + "와 " + b +"는 같습니다.");
        }
    }
}
```

# Scanner와 반복

**`Scanner` 와 `반복문` 을 함께 사용하면 사용자의 입력을 지속적으로 받아들일 수 있음.**

### Scanner와 반복 예제 CODE

```java
package scanner;

import java.util.Scanner;

public class ScannerWhile1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.print("문자열을 입력하세요: (exit: 종료)");
            String str = scanner.nextLine();
            if (str.equals("exit")) {
                System.out.println("프로그램을 종료합니다.");
                break;
            }
            System.out.println("입력한 문자열: " + str);
        }
    }
}
```

```java
package scanner;

import java.util.Scanner;

public class ScannerWhile2 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("두 숫자를 입력하세요. (0을 두 번 입력하면 종료됩니다.)");
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            if (a == 0 && b == 0) {
                System.out.println("프로그램을 종료합니다");
                break;
            }
            int rst = a + b;
            System.out.println("입력한 두 숫자의 합: " + rst);
        }

    }
}
```

```java
package scanner;

import java.util.Scanner;

public class ScannerWhile3 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int sum = 0;
        while (true) {
            System.out.println("숫자를 입력하세요. 0을 입력하면 종료됩니다.");
            int num = scanner.nextInt();
            if (num == 0) {
                System.out.println("프로그램을 종료합니다.");
                break;
            }
            sum += num;
            System.out.println("현재까지 입력한 수의 총합: " + sum);
        }
        System.out.println("입력한 모든 정수의 합: " + sum);
    }
}
```

**반복문 조건 안에 입력을 받을 수도 있음**

```java
package scanner.ex;

import java.util.Scanner;

public class ScannerWhileEx3 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int sum = 0;
        int cnt = 0;
        int input;

        System.out.println("숫자를 입력하세요. 입력을 중단하려면 -1을 입력하세요");
        while ((input = scanner.nextInt()) != -1) {
            sum += input;
            cnt++;
        }
        double average = (double) sum / cnt;
        System.out.println("입력한 숫자들의 합계: " + sum);
        System.out.println("입력한 숫자들의 평균: " + average);
    }
}
```
## 문자열 기본

```java
package ssafy.string;

public class String1 {
    // 문자열의 초기화 2가지 방법
    public static void main(String[] args) {

        // 문자열 상수 풀에 1개만 저장을 하고 이후부터는 같은 주소로 할당
        String lStr1 = "Hello";
        String lStr2 = "Hello";

        // 힙 공간에 다른 주소를 가진 스트링을 생성
        String str1 = new String("Hello");
        String str2 = new String("Hello");

        // == 은 주소값을 비교하는 연산자
        System.out.println(lStr1 == lStr2); // true
        System.out.println(str1 == str2);   // false

        // 값을 비교하는 메서드
        System.out.println(lStr1.equals(lStr2));
        System.out.println(str1.equals(str2));

        //length(), replace(), split(), substring()
    }
}
```

## 문자열 비교하기

```java
package ssafy.string;

public class Equals {

    public static void main(String[] args) {

        String str1 = "Hi";
        String str2 = "Hello";

        if (str1.equals((str2))) {
            System.out.println("Equals");
        } else if (!str1.equals(str2)) {
            System.out.println("Not Equals");
        }
    }
}

```

## 문자열 정수로 변환

```java
package ssafy.string;

public class StringToInt {
    // Integer.parseInt()
    public static void main(String[] args) {

        String str1 = "12345";

        String str2 = str1 + 25;
        System.out.println(str2); // 1234525

        int int1 = Integer.parseInt(str1);
        System.out.println(int1); // 12345

        int sum = int1 + 15;
        System.out.println(sum);  // 12360
    }
}

```

## 문자열 뒤집기

```java
package ssafy.string;

import java.util.Arrays;

public class StringSwap1 {

    public static void main(String[] args) {

        String str = new String("Algorithm");

        char[] charArr = new char[str.length()];

        for (int i = 0; i < str.length(); i++) {
            charArr[i] = str.charAt(i);
        }
        System.out.println(Arrays.toString(charArr)); // [A, l, g, o, r, i, t, h, m]

        // 새로운 배열을 만들어서 뒤집기

        char[] nextArr = new char[charArr.length];

        for (int i = 0; i < nextArr.length; i++) {
            nextArr[i] = charArr[charArr.length - i - 1];
        }
        System.out.println(Arrays.toString(nextArr)); // [m, h, t, i, r, o, g, l, A]

        // 원본 배열에서 Swap : 배열을 새로 만들 필요도 없고, 반복도 절반만 수행하면 됨
        char[] nextArr2 = str.toCharArray(); // 스트링에서 바로 리스트로 뽑아오는 메서드
        System.out.println(Arrays.toString((nextArr2))); // [A, l, g, o, r, i, t, h, m]

        for (int i = 0; i < nextArr2.length / 2; i++) {
            char temp = nextArr2[i];
            nextArr2[i] = nextArr2[nextArr2.length - 1 - i];
            nextArr2[nextArr2.length - 1 - i] = temp;
        }
        System.out.println(Arrays.toString(nextArr2)); // [m, h, t, i, r, o, g, l, A]

        // 문자열 합치기
        String nextStr2 = "";
        for (int i = 0; i < nextArr2.length; i++) {
            nextStr2 += nextArr2[i];
        }
        System.out.println(nextStr2); // mhtiroglA
    }
}

```

## 문자열 비교하기 (BruteForce)

```java
package ssafy.string;

public class StringPattern {

    public static void main(String[] args) {
        String text = "This iss a book";
        String pattern = "iss";

        int result = bruteforce(text, pattern);
        System.out.println(result);
    }

    public static int bruteforce(String text, String pattern) {
        int ti = 0;
        int pi = 0;
        while (ti < text.length() && pi < pattern.length()) {
            if (text.charAt(ti) != pattern.charAt(pi)) {
                ti -= pi;
                pi = -1;
            }
            ti += 1;
            pi += 1;
        }
        if (pi == pattern.length()) {
            return (ti - pi);
        } else {
            return -1;
        }
    }
}
```

```java
strArr[i].matches("[-+]?\\d*\\.?\\d+")
```
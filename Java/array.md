# 기본형과 참조형

JAVA의 데이터 타입을 크게 보면 `기본형` 과 `참조형` 으로 나눌 수 있음

- **기본형**
    - 사용하는 값을 직접 넣을 수 있음
    - `int`, `long`, `double`, `boolean` 등
    - 사용할 값을 직접 저장: 더 빠르고 효율적인 메모리 처리 가능
    - 기본형은 모두 사이즈가 정해져 있음 : 선언과 동시에 크기가 정해짐 : 크기를 동적으로 바꿀 수 없음
        
        ```java
        int i;    // 4byte
        long l;   // 8byte
        double d; // 8byte
        ```
        
    
- **참조형**
    - 배열과 같이 데이터에 접근하기 위한 참조(주소)를 저장하는 데이터 타입
    - 참조형은 기본형과 달리 크기를 동적으로 할당할 수 있음 → `유연성` 제공
    - 메모리에 저장된 배열이나 객체의 참조를 저장: 더 복잡한 데이터 구조를 만들고 관리할 수 있음

# 배열

## 1차원 배열

### 배열이 필요한 이유

- 아래 코드의 경우 학생을 몇 명 추가해야 한다면 변수를 선언하고, 출력하는 부분까지 같이 수정해야 함
    
    → 비슷한 변수를 반복해서 선언하는 문제
    
- 변수의 이름 때문에 반복문도 사용 불가.

**같은 타입의 변수를 반복해서 선언하고, 사용하는 문제를 해결: `배열`**

```java
package array;

public class Array1 {

    public static void main(String[] args) {
        // 아래 코드의 경우, 학생 수가 변경될 경우 코드가 길어지거나, 많은 변수 선언 등의 문제가 발생할 수 있음
        int student1 = 90;
        int student2 = 80;
        int student3 = 70;
        int student4 = 60;
        int student5 = 50;

        System.out.println("학생1 점수: " + student1);
        System.out.println("학생2 점수: " + student2);
        System.out.println("학생3 점수: " + student3);
        System.out.println("학생4 점수: " + student4);
        System.out.println("학생5 점수: " + student5);
    }
}
```

### 배열의 선언과 생성

```java
package array;

public class Array1Ref2 {
    // 리팩토링 (Refactoring) : 코드의 기능은 유지하면서 내부 구조를 개선해 가독성을 높이고 유지보수를 용이하게 하는 과정
    public static void main(String[] args) {
        int student_cnt = 5;
        int[] students;
        students = new int[student_cnt];

        students[0] = 90;
        students[1] = 80;
        students[2] = 70;
        students[3] = 60;
        students[4] = 50;

        for (int i = 0; i < student_cnt; i++) {
            System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
        }
    }
}
```

```java
int[] students;        // 배열 변수 선언
students = new int[5]; // 배열 생성
```

1. **배열 변수 선언 `int[] = students;`**
    - 배열을 사용하려면 배열 변수를 선언해야 함
    - 일반적인 변수와 달리 타입 다음에 `[]` 가 들어감
    - 배열 변수를 선언한다고 해서, 아직 사용할 수 있는 배열이 만들어진 것은 아님!
        - `int a;` 에는 정수를 , `double b` 에는 실수를 담을 수 있음
        - `int[] students;` 와 같은 변수에는 배열을 담을 수 있음 (10 ,20과 같은 값을 담는 게 아님)

1. **배열 생성 `students = new int [5];`**
    - 배열을 사용하려면 배열을 생성해야 함
    - `new int[5]` 라고 입력하면 5개의 `int` 형 변수가 만들어짐
    - `new` 는 새로 생성한다는 뜻, `int[5]` 는 `int` 형 변수 5개라는 뜻

1. **배열 참조 값 보관**
    - `new int[5]` 로 배열을 생성하면 배열의 크기만큼 메모리를 확보함
        - `int` 형 5개를 사용하면 `4byte * 5 -> 20byte` 를 확보
    - 배열을 생성하고 나면 JAVA는 이 배열에 접근할 수 있는 참조 값(주소)을 반환
    - 앞서 선언한 배열 변수인 `int[] students` 에 생성된 배열의 참조값을 보관
        - 이 참조값을 통해 배열에 접근하고 사용할 수 있음
        - 참고로 배열을 생성하는 `new int[5]`에는 아무런 이름이 없음.
        

```java
package array;

public class Array2 {
    // 배열의 선언과 생성
    public static void main(String[] args) {
        int[] students;         // 배열 생성 (일반적인 타입 뒤에 [] 삽입) :
                                // 하지만 선언한다고 해서 아직 사용할 수 있는 배열이 만들어진 것은 아님
                                // int[] students와 같은 배열 변수에는 배열을 담을 수 있음 (10, 20과 같은 값이 아님)

        /*
        int[] students = new int[5]; //1. 배열 생성
        int[] students = x001; //2. new int[5]의 결과로 x001 참조 값 반환 <- 중요!
        students = x001 //3. 최종 결과
         */

        students = new int[5];  // int 그릇이 5개 있는 배열을 생성
                                // new는 새로 생성한다는 것, int[5]는 int형 변수 5개라는 뜻
                                // java는 배열을 생성할 때 내부 값을 자동으로 초기화함
                                // 숫자형은 0, boolean은 false, String은 null로 초기화

        /*
        배열을 생성하는 new int[5]에는 아무런 이름이 없고, 그저 int형 변수 5개를 연속으로 만드는 것
        int[] students 변수는 new int[5]로 생성한 배열의 참조 값을 가지고 있음
        이 참조 값을 통해서 배열에 접근할 수 있음
         */

        System.out.println(students); // [I@10f87f48 << 참조값

        // 변수 값 대입
        students[0] = 90; // index는 0부터 시작함
        students[1] = 80; // == x001의 [1]요소에 80을 대입
        students[2] = 70;
        students[3] = 60;
        students[4] = 50; // index의 마지막 요소는 입력한 n - 1

        // 변수 값 사용
        System.out.println("학생1 점수: " + students[0]);
        System.out.println("학생2 점수: " + students[1]);
        System.out.println("학생3 점수: " + students[2]);
        System.out.println("학생4 점수: " + students[3]);
        System.out.println("학생5 점수: " + students[4]);

        /*
        기본형 vs 참조형

        기본형: int, long, double, boolean처럼 변수에 사용할 값을 직접 넣을 수 있는 데이터 타입 (크기가 정해져있음)
        참조형: []과 같이 데이터에 접근하기 위해 참조(주소)를 저장하는 데이터 타입 (동적으로 크기 변경이 가능함)

        기본형은 사용할 값을 직접 저장하는 반면, 참조형은 메모리에 저장된 배열이나 참조를 저장.
        이로인해 참조형은 더 복잡한 데이터 구조를 만들고 관리할 수 있지만, 기본형에 비해 느리고 효율적인 메모리 사용이 어려움.
         */
    }
}

```

### 배열 사용

배열은 변수와 사용법이 유사함

`[]` 사이에 숫자 번호(index)를 넣어주면 됨

**배열은 0부터 시작함**

- `new int[5]` 로 배열을 만들었다면, 인덱스는 `0, 1, 2, 3, 4` 가 존재
- 접근 가능한 배열의 인덱스를 넘어가면 오류가 발생함

**배열에 값 대입 및 읽기**

- 일반적인 변수와 사용법은 같음
- `[]` 를 통해 인덱스만 넣어주면 됨

## 배열 Refactoring

### 배열 초기화

**배열은 `{}` 를 사용해서 생성과 동시에 초기화하는 기능을 제공**

```java
package array;

public class Array1Ref3 {
    //
    public static void main(String[] args) {

        int[] students = new int[]{90, 80, 70, 60, 50}; // 배열 변수의 선언, 배열 생성, 초기화를 동시에 진행 new int[]{요소}

        // 배열.length : 배열의 길이를 제공, 참조만 가능, 대입은 불가
        for (int i = 0; i < students.length; i++) {
            System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
        }
    }
}
```

- **`.length` :**
    - 배열의 길이를 제공
    - 이 값은 조회만 가능함: 대입은 불가
    

### 간단한 배열 생성

**배열은 `{}` 만 사용해서 생성과 동시에 초기화하는 기능을 제공**

- 단 이 때는 아래와 같이 배열 변수의 선언을 한 줄에 함께 사용할 때만 가능
- 내부적으로는 `new int[5]` 를 사용해서 배열을 생성 : JAVA가 제공하는 편의 기능

```java
package array;

public class Array1Ref4 {

    public static void main(String[] args) {
        int[] students = {90, 80, 70, 60, 50}; // new int[] 까지도 생략 가능함 (java가 추론함)
        // int[] students = new int[]{90, 80, 70, 60, 50}; // 실제로는 아래와 같이 동작함

        /*
        단 아래와 같이 라인을 나누면 new int[] 생략 못 함 (java가 int형 배열인 것을 인지하지 못 하기 때문)

        int[] students;
        students = {90, 80, 70, 60, 50};
         */

        // 배열.length : 배열의 길이를 제공, 참조만 가능, 대입은 불가
        for (int i = 0; i < students.length; i++) {
            System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
        }
    }
}
```

### 배열의 복사

- 배열은 생성하면 길이를 변경할 수 없기 때문에, 
더 많은 저장 공간이 필요하다면 이전 배열의 값을 복사해야함

```java
// 새로운 배열 = Arrays.copy(복사하고 싶은 배열, 새로운 배열의 크기)
System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length);
```

## 2차원 배열

**1차원 배열은 단순히 순서대로 나열되어 있었음**

**2차원 배열은 하나의 차원이 추가됨:**

- 행과 열로 구성

### 2차원 배열의 선언과 생성

**`int[][] arr = new arr[2][3]` 과 같이 선언하고 생성**

`[]` 가 하나 더 추가되는 것을 제외하고는 사용법은 1차원 배열과 같음

```java
package array;

public class ArrayDi0 {

    public static void main(String[] args) {
        // 2 * 3 2차원 배열 만들기
        int[][] arr = new int[2][3]; // 행 = 2, 열 = 3

        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[0][2] = 3;
        arr[1][0] = 4;
        arr[1][1] = 5;
        arr[1][2] = 6;

        // 0행 출력
        System.out.print(arr[0][0] + " ");
        System.out.print(arr[0][1] + " ");
        System.out.print(arr[0][2] + " ");
        System.out.println();

        // 1행 출력
        System.out.print(arr[1][0] + " ");
        System.out.print(arr[1][1] + " ");
        System.out.print(arr[1][2] + " ");
        System.out.println();
    }
}

/*
1 2 3 
4 5 6 
*/
```

**리팩토링**

```java
package array;

public class ArrayDi1 {

    public static void main(String[] args) {
        int[][] arr = new int[2][3];

        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[0][2] = 3;
        arr[1][0] = 4;
        arr[1][1] = 5;
        arr[1][2] = 6;

        for (int i = 0; i < 2; i++) {
            for (int j = 0; j < 3; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}

/*
1 2 3 
4 5 6 
*/
```

**값 입력에 따라 크기가 유동적으로 변하는 배열 만들기**

```java
package array;

public class ArrayDi3 {

    public static void main(String[] args) {
        int tarRow = 5;
        int tarCol = 3;

        int[][] arr = new int[tarRow][tarCol];

        int cnt = 1;
        for (int row = 0; row < arr.length; row++) {
            for (int col = 0; col < arr[row].length; col++) {
                arr[row][col] = cnt++;
            }
        }

        for (int row = 0; row < arr.length; row++) {
            for (int col = 0; col < arr[row].length; col++) {
                System.out.print(arr[row][col] + " ");
            }
            System.out.println();
        }
    }
}

/*
1 2 3 
4 5 6 
7 8 9 
10 11 12 
13 14 15 
*/
```

### 2차원 배열 Refactoring

**2차원 배열도 아래와 같이 1차원 배열처럼 편리하게 초기화 가능함**

```java
package array;

public class ArrayDi2 {

    public static void main(String[] args) {
        int[][] arr = {
                {1, 2, 3},
                {4, 5, 6}
        };

        for (int row = 0; row < arr.length; row++) {
            for (int col = 0; col < arr[row].length; col++) {
                System.out.print(arr[row][col] + " ");
            }
            System.out.println();
        }
    }
}

/*
1 2 3 
4 5 6 
*/
```
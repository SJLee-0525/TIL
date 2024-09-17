# 배열

- 동일한 자료형의 변수들을 하나의 변수에 담기 위한 자료구조
    - 여러 개의 데이터를 다뤄야 할 때 한 번의 선언을 통해서 여러 개의 데이터를 다룰 수 있어 효율적

```java
int[] nums;
nums = new int[6]; // 배열의 크기만 지정하기 {0, 0, 0, 0, 0, 0}
nums[0] = 1;
nums[1] = 2;
nums[2] = 3;
nums[3] = 4;
nums[4] = 5;
nums[5] = 6;

// 한 줄 쓰기도 가능
int[] nums = new int[]{1, 2, 3, 4, 5, 6};
int[] nums = {1, 2, 3, 4, 5, 6};
```

### 배열 순회

```java
package ssafy.array;

public class Array01 {

    public static void main(String[] args) {
        int[] arr = {3, 4, 5, 1, 2, 6};

        System.out.println("정방향 순회");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]);
            if (i < arr.length - 1) {
                System.out.print(", ");
            }
        }

        System.out.println();
        System.out.println("역방향 순회");
        for (int i = arr.length - 1; i >= 0; i--) {
            System.out.print(arr[i]);
            if (i != 0) {
                System.out.print(", ");
            }
        }
    }
}

		/*
		정방향 순회
		3, 4, 5, 1, 2, 6
		역방향 순회
		6, 2, 1, 5, 4, 3
		*/
```

## 검색

저장되어 있는 자료 중에서 원하는 것을 찾는 작업

### 순차 검색: 정렬되지 않은 경우

- Search by ISBN
- 첫 번째 원소부터 순서대로 검색 대상과 키 값이 같은 원소가 있는지 비교하면서 찾음
- 키 값이 동일한 원소를 찾으면 그 원소의 index를 반환
- 자료 구조의 마지막에 이를 때까지 검색 대상을 찾지 못하면 검색 실패

```java
package ssafy.array;

public class SequentialSearch1 {

    public static void main(String[] args) {
        int[] arr = {4, 9, 11, 23, 2, 19, 17};
        int targetKey = 19;

        int result = searchWhileNoSort(arr, targetKey);
        System.out.println(result);
    }

    // for문 사용
    public static int searchForNoSort(int[] inputArr, int key) {
        for (int i = 0; i < inputArr.length; i++) {
            if (inputArr[i] == key) {
                return i;   // 찾는 대상이 있을 경우 index를 리턴
            }
        }
        return -1;          // 찾는 대상이 없을 경우 -1 return;
    }

    // while문 사용
    public static int searchWhileNoSort(int[] inputArr, int key) {
        int i = 0;
        while(i < inputArr.length) {
            if (inputArr[i] == key) {
                return i;
            }
            i++;
        }
        return -1;
    }
}
```

### 순차 검색: 정렬된 경우

- 첫 번째 원소부터 순서대로 검색 대상과 키 값이 같은 원소가 있는지 비교하면서 찾음
- 키 값이 동일한 원소를 찾으면 그 원소의 index를 반환
- 찾고자 하는 원소의 값보다, index가 가리키는 값이 커지면 검색 실패

```java
package ssafy.array;

import java.util.Arrays;  // 잊지 말고 넣자

public class SequentialSearch2 {

    public static void main(String[] args) {
        int[] arr = {4, 9, 11, 23, 2, 19, 17};

        Arrays.sort(arr);   // 정렬하기
        System.out.println(Arrays.toString(arr)); // [2, 4, 9, 11, 17, 19, 23]
        int targetKey = 23;

        int result = searchWhileSort(arr, targetKey);
        System.out.println(result);
    }

    public static int searchForSort(int[] inputArr, int key) {
        for (int i = 0; i < inputArr.length; i++) {
            if (inputArr[i] == key) {
                return i;
            }
            if (inputArr[i] > key) {
                return -1;
            }
        }
        return -1;
    }

    public static int searchWhileSort(int[] inputArr, int key) {
        int i = 0;
        while (i < inputArr.length) {
            if (inputArr[i] == key) {
                return i;
            }
            if (inputArr[i] > key) {
                return -1;
            }
            i++;
        }
        return -1;
    }
}
```

### 이진 검색

- **자료가 정렬된 상태여야 사용 가능함**
- 자료의 가운데에 있는 항목의 키 값과 비교해 다음 검색의 위치를 결정 후 검색
- 가운데에 있는 값보다 작다면 왼쪽 영역을, 크다면 오른쪽 영역을 검색하는 식 (오름차순 기준)

```java
package ssafy.array;

import java.util.Arrays;

public class binarySearch1 {

    public static void main(String[] args) {
        int[] arr = {4, 9, 11, 23, 2, 19, 17};
        Arrays.sort(arr);
        // System.out.println(Arrays.toString(arr)); // [2, 4, 9, 11, 17, 19, 23]

        int targetKey = 2;

        int result = binarySearch(arr, targetKey);
        System.out.println(result);
    }

    public static int binarySearch(int[] inputArr, int key) {
        int start = 0;                  // 구간의 시작 index
        int end = inputArr.length - 1;  // 구간의 끝 index
        while (start <= end) {          // start와 end가 같아도 검색해야할 데이터는 하나가 남은 상태: 역전돼야 모든 데이터를 검사한 것
            int mid = (start + end) / 2;

            if (inputArr[mid] == key) {
                return mid;
            } else if (inputArr[mid] > key) {
                end = mid - 1;
            } else {                    // == (inputArr[mid] < key)
                start = mid + 1;
            }
        }
        return -1;
    }
}
```

## 정렬

```
관련 메서드

Arrays.sort()      -> Quick Sort
Collections.sort() -> Merge Sort 
Comparable
Comparator
```

### 버블 정렬

- 첫 번째 원소부터 인접한 원소와 비교하여 자리를 교환해가면서 마지막 자리로 이동
- 한 사이클이 끝나면 가장 큰 원소가 마지막 자리에 위치 (오름차순 기준)
- 교환하며 자리를 이동하는 모습이 마치 물 위에 올라오는 거품 모양과 같다고 하여 버블 정렬이라고 함

```java
package ssafy.array;

import java.util.Arrays;

public class BubbleSort1 {
    // 버블 정렬 (오름차순)
    public static void main(String[] args) {

        int[] arr = {55, 7, 78, 12, 42};
        
        for (int i = arr.length - 1; i >= 1; i--) {    // i: 각 사이클마다 최대 데이터가 정렬될 위치
            for (int j = 0; j < i; j++) {              // j: 인접한 데이터와 비교할 index
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
            System.out.println(Arrays.toString(arr));
        }
    }
}

/*
[7, 55, 12, 42, 78]
[7, 12, 42, 55, 78]
[7, 12, 42, 55, 78]
[7, 12, 42, 55, 78]
*/
```

### 선택 정렬

- 주어진 자료들 중 가장 작은 값의 원소부터 차례대로 선택해 위치를 교환하는 방식 (오름차순 기준)
    1. 주어진 리스트 중 최소 값을 찾음
    2. 그 값을 리스트의 맨 앞에 위치한 값과 교환
    3. 앞선 첫 위치를 제외한 나머지 리스트를 대상으로 위의 과정을 반복

```java
package ssafy.array;

import java.util.Arrays;

public class SelectionSort1 {

    public static void main(String[] args) {
        int[] arr = {10, 64, 25, 11, 28, 77, 34};

        int[] newArr = selectionSort(arr);
        System.out.println("결과: " + Arrays.toString(newArr));
    }

    public static int[] selectionSort(int[] inputArr) {
        // cycle 횟수: 배열 길이 - 1
        for (int i = 0; i < inputArr.length - 1; i++) {
            int minIndex = i;   // 최소 값의 인덱스를 저장할 변수

            // 최소 값을 찾는 반복문
            for (int j = i + 1; j < inputArr.length; j++) {
                if (inputArr[minIndex] > inputArr[j]) { // 만약 현재 최소 값보다 더 작은 값이 있다면
                    minIndex = j;                       // 최소 값 인덱스를 수정해줌
                }
            }
            // i와 minIndex의 위치 swap
            int temp = inputArr[i];
            inputArr[i] = inputArr[minIndex];
            inputArr[minIndex] = temp;

            System.out.println(Arrays.toString(inputArr));
        }
        return inputArr;
    }
}
```

### 카운팅 정렬

- 항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는 세는 작업을 해 
선형 시간에 정렬하는 효율적인 알고리즘
- 정수나, 정수로 표현할 수 있는 자료에 대해서만 적용 가능
- 집합 내에 가장 큰 정수를 알아야 함 (카운트를 위한 충분한 공간을 할당하기 위해)

```java
package ssafy.array;

import java.util.Arrays;

public class CountingSort1 {

    public static void main(String[] args) {
        int[] arr = {0, 4, 1, 3, 1, 2, 4, 1};
        int maxValue = findMaxValue(arr);                   // 4

        int[] countingArr = counting(arr, maxValue);        // [1, 4, 5, 6, 8]

        int[] resultArr = countingSort(arr, countingArr);
        System.out.println(Arrays.toString(resultArr));     // [0, 1, 1, 1, 2, 3, 4, 4]
    }

    public static int findMaxValue(int[] inputArr) {
        int maxVal = inputArr[0];
        for (int i = 1; i < inputArr.length; i++) {
            if (maxVal < inputArr[i]) {
                maxVal = inputArr[i];
            }
        }
        return maxVal;
    }

    public static int[] counting(int[] inputArr, int maxValue) {
        int[] countingArr = new int[maxValue + 1];   // [0, 0, 0, 0, 0]
        for (int i = 0; i < inputArr.length; i++) {
            countingArr[inputArr[i]] += 1;
        }
        // [1, 3, 1, 1, 2]

        for (int i = 1; i < countingArr.length; i++) {
            countingArr[i] += countingArr[i - 1];
        }
        return countingArr;
        // [1, 4, 5, 6, 8]
    }

    public static int[] countingSort(int[] inputArr, int[] countingArr) {
        int[] resultArr = new int[inputArr.length];     // [0, 0, 0, 0, 0, 0, 0, 0]

        for (int i = inputArr.length - 1; i >= 0; i--) {
            countingArr[inputArr[i]] -= 1;
            resultArr[countingArr[inputArr[i]]] = inputArr[i];

            System.out.println(Arrays.toString(resultArr));
        }
        return resultArr;
    }
}

    /*
    [0, 0, 0, 1, 0, 0, 0, 0]
    [0, 0, 0, 1, 0, 0, 0, 4]
    [0, 0, 0, 1, 2, 0, 0, 4]
    [0, 0, 1, 1, 2, 0, 0, 4]
    [0, 0, 1, 1, 2, 3, 0, 4]
    [0, 1, 1, 1, 2, 3, 0, 4]
    [0, 1, 1, 1, 2, 3, 4, 4]
    [0, 1, 1, 1, 2, 3, 4, 4]
     */
```
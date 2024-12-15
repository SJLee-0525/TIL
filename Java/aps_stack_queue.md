# Stack

### 직접 구현

```java
package ssafy.stack;

public class Stack2 {

    // 스택 배열 생성
    public static String[] stack = new String[100];

    // 마지막에 들어간 데이터의 index를 가리키는 top
    public static int top = -1;

    public static boolean isEmpty() {
        // return (top == -1) ? true : false;
        return top == -1;
    }

    public static boolean isFull() {
        return (top == stack.length - 1) ? true : false;
        // return top == stack.length - 1;
    }

    public static void pushItem(String item) {
        if (isFull()) {
            System.out.println("스택이 가득 찼습니다.");
            return;
        }
        stack[++top] = item;
    }

    public static String popItem() {
        if (isEmpty()) {
            System.out.println("스택이 비어있습니다.");
            return null; // 스트링을 리턴해줘야 하니까
        }
        String popItem = stack[top];
        stack[top--] = null; // pop한 위치를 빈 것으로 되돌림
        return popItem;
    }

    // pop과 달리 마지막 원소만 확인하는 것
    public static String peek() {
        if (isEmpty()) {
            System.out.println("스택이 비어있습니다.");
            return null;
        }
        return stack[top];
    }

    public static void main(String[] args) {
        pushItem("고양이");
        pushItem("토끼");
        pushItem("쥐");

        // 스택이 비어있지 않은 동안 pop 호출
        while (!isEmpty()) {
            System.out.println(popItem());
        }

        // 비어있는 상태에서 pop해보기
        System.out.println(popItem());

        // 100개 다 채워보기
        for (int i = 1; i <= 100; i++) {
            pushItem(i + "");
        }

        // 초과해서 push해보기
        pushItem("101");

        System.out.println(isFull());
    }
}

```

### 유틸리티 이용

```java
package ssafy.stack;

import java.util.Stack;

public class Stack1 {

    public static void main(String[] args) {
        Stack<String> stack = new Stack<> ();

        stack.push("고양이");
        stack.push("토끼");
        stack.push("쥐");

        for (int i = 0; i < 3; i++) {
            System.out.println(stack.pop());
        }
    }
}
// stack.peek() 조회
```

## DFS

### 1차원

```java
package ssafy.stack;

import java.util.Scanner;
import java.util.Stack;
import java.util.Arrays;
import java.util.ArrayList;

public class SweaFindRoute {

    public static int DFS(ArrayList<Integer>[] adjList) {
        int[] visited = new int[100];
        Stack<Integer> stack = new Stack<>();

        int now = 0;    // 출발점은 0
        visited[0] = 1; // 출발 표시
        while (true) {
            boolean flag = true;
            for (int w : adjList[now]) { // 해당 위치의 인접 정점 순회
                if (visited[w] == 0) {   // 방문 안 한 곳이 있다면
                    flag = false;        // flag 표시
                    stack.push(now);     // 현위치 스택에 push
                    now = w;             // 이동
                    visited[now] = 1;    // 방문 표시
                    if (now == 99) {     // 희망 도착점은 99
                        return 1;        // 희망 지점에 도착하면 1 반환
                    }
                    break;
                }
            }
            if (flag) {                 // for문 내에서 방문한 적이 없으면
                if (!stack.isEmpty()) { // 스택이 비어있지 않으면
                    now = stack.pop();  // 스택에서 뽑아서 사용
                } else {                // 비어있으면
                    return 0;           // 0 반환
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        // 출발점은 0, 도착점은 99, 정점 개수는 최대 100, 단방향 노드
        for (byte t = 1; t <= 10; t++) {
            int tc = scanner.nextInt();
            int E = scanner.nextInt();

            // 2차원 인접 리스트 만들기
            ArrayList<Integer>[] adjList = new ArrayList[100];
            for (int i = 0; i < 100; i++) {
                adjList[i] = new ArrayList<Integer>();
            }

            // 인접 리스트에 값 넣기
            for (int e = 0; e < E; e++) {
                int V1 = scanner.nextInt();
                int V2 = scanner.nextInt();
                adjList[V1].add(V2);
            }
            // System.out.println(Arrays.deepToString(adjList));

            // DFS 호출
            int result = DFS(adjList);
            System.out.println("#" + tc + " " + result);

        }
        scanner.close();
    }
}

```

### 2차원

```java
package ssafy.stack;

import java.util.Scanner;
import java.util.Arrays;
import java.util.Stack;

public class Swea4875 {

    // 델타 배열
    public static int[] di = {1, 0, -1, 0};
    public static int[] dj = {0, 1, 0, -1};

    // 시작지점 찾는 함수
    public static int[] findStart(int[][] maze, int N) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                if (maze[i][j] == 2) {
                    return new int[] {i, j};
                }
            }
        }
        return new int[] {-1, -1};
    }

    // DFS 탐색
    public static int DFS(int[][] maze, int N) {
        // 출발지 찾아서 반환받고 할당
        int[] start = findStart(maze, N);

        int i = start[0];
        int j = start[1];

        // 만약 출발 지점이 없으면 0 리턴
        if (i == -1 && j == -1) {
            return 0;
        }

        // DFS 사전 준비: Stack은 1차원 배열을 받도록 선언, visited는 2차원 배열로 선언
        Stack<int[]> stack = new Stack<>();
        int[][] visited = new int[N][N];
        visited[i][j] = 1; // 방문 표시

        // DFS
        while (true) {
            boolean flag = true;                    // 탐색 여부 확인용 flag
            for (int k = 0; k < 4; k++) {           // 델타 탐색
                int mi = i + di[k];                 // 임시로 이동 후
                int mj = j + dj[k];
                if (0 <= mi && mi < N               // 만약 인덱스 범위를 초과하지 않고
                    && 0 <= mj && mj < N
                    && maze[mi][mj] != 1            // 벽이 아니며
                    && visited[mi][mj] == 0) {      // 방문한 적이 없다면
                    flag = false;                   // 탐색했다고 표시 후
                    stack.push(new int[]{i, j});    // 스택에 현 위치 삽입
                    i = mi;                         // 이동
                    j = mj;
                    visited[i][j] = 1;              // 이동한 위치 방문 표시
                    if (maze[mi][mj] == 3) {        // 만약 도착지라면 1 리턴
                        return 1;
                    }
                    break;                          // for문 중단
                }
            }
            if (flag == true) {                     // 만약 for문 내에서 탐색한 적이 없었다면
                if (!stack.isEmpty()) {             // 만약 스택이 비어있지 않으면
                    int[] temp = stack.pop();       // 스택에서 pop해서 되돌아감
                    i = temp[0];
                    j = temp[1];
                } else {                            // 만약 비었다면
                    return 0;                       // 탐색할 수 있는 곳이 없으니 0 반환
                }
            }
        }
    }

    // MAIN
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int T = scanner.nextInt(); // 테케 개수
        for (int tc = 1; tc <= T; tc ++) {
            int N = scanner.nextInt();
            scanner.nextLine();

            // 미로 배열 선언 후 값 할당
            int[][] maze = new int[N][N];
            for (int i = 0; i < N; i++) {
                String inputStr = scanner.nextLine();
                for (int j = 0; j < N; j++) {
                    char inputChar = inputStr.charAt(j);
                    maze[i][j] = Character.getNumericValue(inputChar);
                }
            }
            // System.out.println(Arrays.deepToString(maze));

            // DFS 호출 후 결과 값 반환
            int result = DFS(maze, N);

            // 결과 출력
            System.out.println("#" + tc + " " + result);
        }
        scanner.close();
    }
}

```

# Queue

### 직접 구현

```java
package ssafy.queue;

import java.util.Arrays;
import java.util.Scanner;

public class Queue1 {

    // 배열 사이즈가 10이면 10번 삽입할 수 있음 (큐의 크기가 10이 아님)
    static String[] queue = new String[10];
    static int front = -1;
    static int rear = -1;

    // 공백상태 확인
    static boolean isEmpty() {
        return front == rear;
    }

    // 포화상태 확인
    static boolean isFull() {
        // rear가 배열의 마지막 index를 가리키면 포화 상태
        return rear == (queue.length - 1);
    }

    // 삽입
    static void enQueue(String item) {
        if (isFull()) {
            System.out.println("Queue가 가득 찼습니다.");
            return;
        }
        queue[++rear] = item;
        System.out.print("삽입 성공 ");
        System.out.println(Arrays.toString(queue));
    }

    // 삭제
    static String deQueue() {
        if (isEmpty()) {
            System.out.println("Queue가 비어있습니다.");
            return null;
        }
        System.out.println(Arrays.toString(queue));
        return queue[++front];
    }

    // 조회
    static String qPeek() {
        return queue[front + 1]; // 일시적으로 front를 1 늘려서 확인
    }

    // 큐에 들어있는 데이터 개수 조회
    static int qSize() {
        return rear - front;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // 원소 넣기
        while (true) {
            String item = scanner.nextLine();
            if (item.equals("0")) {
                break;
            }
            enQueue(item);
        }

        // 원소 뽑기
        while (!isEmpty()) {
            System.out.println(deQueue());
        }
    }

}

```

### 유틸리티 이용

```java
package ssafy.queue;

import java.util.Queue;
import java.util.LinkedList;

public class Queue2 {

    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();

        // 삽입
        queue.add(1);       // 원소를 추가할 수 없으면 예외 발생 (프로그램 중단)
        queue.offer(1);     // 추가에 성공하면 true, 실패하면 false 반환 (프로그램 유지)

        // 삭제
        queue.remove();     // 원소를 삭제하고 반환, 삭제할 수 없으면 예외 발생 (프로그램 중단)
        queue.poll();       // 원소를 삭제하고 반환, 삭제할 수 없으면 null 반환 (프로그램 유지)

        // 조회
        queue.element();    // 원소를 조회할 수 없으면 예외 발생 (프로그램 중단)
        queue.peek();       // 원소를 조회할 수 없으면 null 반환 (프로그램 유지)
    }
}
```

# Deque

**stack + queue**

```java
package ssafy.queue;

import java.util.Deque;
import java.util.LinkedList;

public class Deque1 {

    public static void main(String[] args) {
        Deque<Integer> deque = new LinkedList<>();

        // 앞쪽에 원소 추가
        deque.addFirst(1);      // Deque의 앞쪽에 데이터를 삽입, 용량 초과시 Exception
        deque.offerFirst(1);    // Deque의 앞쪽에 데이터를 삽입 후 true, 용량 초과시 false
        deque.push(1);          // addFirst()와 동일

        // 뒤쪽에 원소 추가
        deque.addLast(1);       // Deque의 뒤쪽에 데이터를 삽입, 용량 초과시 Exception
        deque.add(1);           // addLast()와 동일
        deque.offerLast(1);     // Deque의 뒤쪽에 데이터를 삽입 후 true, 용량 초과시 false
        deque.offer(1);         // offerLast()와 동일

        // 앞쪽의 원소 삭제
        deque.removeFirst();        // Deque의 앞에서 제거, 비어있으면 예외
        deque.remove();             // removeFirst()와 동일
        deque.pop();                // removeFirst()와 동일
        deque.poll();               // Deque의 앞에서 제거, 비어있으면 null 리턴
        deque.pollFirst();          // poll()과 동일

        // 뒤쪽의 원소 삭제
        deque.removeLast();         // Deque의 뒤에서 제거, 비어있으면 예외
        deque.pollLast();           // Deque의 뒤에서 제거, 비어있으면 null 리턴

        // 값 확인
        deque.getFirst();           // 첫 번째 엘리먼트를 확인, 비어있으면 예외
        deque.peekFirst();          // 첫 번째 엘리먼트를 확인, 비어있으면 null 리턴
        deque.peek();               // peekFirst()와 동일

        deque.getLast();            // 마지막 엘리먼트를 확인, 비어있으면 예외
        deque.peekLast();           // 마지막 엘리먼트를 확인, 비어있으면 null 리턴

        deque.size();               // Deque에 들어있는 엘리먼트의 개수
    }
}

```
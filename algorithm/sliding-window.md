# 슬라이딩 윈도우 (Sliding Window) 알고리즘

`슬라이딩 윈도우` 알고리즘은 배열이나 리스트에서 일정 범위의 값을 비교할 때 사용하면 유용하다. <br>
예를 들어 **"정수 배열에서 연속된 3개의 숫자의 합계 중 가장 큰 값은 무엇인가?"** 라는 문제에서 사용될 수 있다. <br>
**슬라이딩 윈도우 알고리즘은 중복된 요소를 버리지 않고 재사용하여 불필요한 계산을 줄이는 알고리즘!**

### 단순 for 루프로 구현

가장 단순한 방법으로는 for 루프로 모든 배열 요소를 특정 길이까지만 돌면서 합계를 구하고 최대값과 비교하면서 찾는 방법이 있다.<br>
**-> 모든 요소를 일일이 검사하기 때문에 비효율적이고 데이터의 양이 많아지면 시간이 오래걸리는 단점을 가진다.**

```java
private static int max() {
    int[] num = {2, 4, 7, 10, 8, 4};
    int k = 3;
    int max = 0;

    for (int i = 0; i < num.length - k + 1; i++) {
        int sum = 0;
        for (int j = i; j < num.length - k + i; j++) {
            sum += num[j];
        }
        max = Math.max(max, sum);
    }

    return max;
}
```

### 단순 for 루프로 구현시 문제점

반복마다 중복된 요소를 탐색하는 문제점을 가진다.
이런 중복되는 요소들을 재사용하는 방법이 슬라이딩 윈도우 알고리즘의 핵심이다.

<img width="424" alt="스크린샷 2021-10-29 오후 1 03 59" src="https://user-images.githubusercontent.com/61447654/139375610-299f56e8-b58a-4e84-99a8-51a66611986a.png">


### 슬라이딩 윈도우를 이용해서 구현

`end`가 k보다 작으면 숫자들을 더해주고 `end`가 k보다 커지면 `start`의 숫자를 차감하고 `start++`을 해준다. **(윈도우를 오른쪽으로 1칸 이동)**<br>
이렇게하면 매번 3개의 숫자의 합을 구해서 비교할 필요없이 한 번에 최대값을 구할 수 있다.

```java
private static int max() {
    int[] num = {2, 4, 7, 10, 8, 4};
    int k = 3;
    int window_start = 0; // 윈도우의 시작 인덱스
    int window_sum = 0; // 윈도우의 합계
    int max = 0;

    for (int end = 0; end < num.length; end++) {
        window_sum += num[end];

        if(end >= k - 1) {
            max = Math.max(max, window_sum);
            window_sum -= num[window_start];
            window_start++;
        }
    }
    return max;
}
```

### 슬라이딩 윈도우 코드 진행 방식

<img width="555" alt="스크린샷 2021-10-29 오후 1 20 16" src="https://user-images.githubusercontent.com/61447654/139375730-16bdf008-ef71-4a54-9fc7-159ea8f171b6.png">


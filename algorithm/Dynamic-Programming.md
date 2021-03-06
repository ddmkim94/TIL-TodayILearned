# 동적 계획법 (Dynamic Programming) 알고리즘
`다이나믹 프로그래밍`은 하나의 문제는 단 한 번만 풀도록 하는 알고리즘으로,
한 번 푼 것을 여러 번 다시 푸는 비효율적인 알고리즘을 개선하기 위한 방법입니다.<br>
분할 정복 알고리즘(재귀)을 개선하기 위한 알고리즘이기도 합니다.<br>
단순 분할 정복으로 풀게되면 심각한 비효율성을 낳는 대표적인 예로는 피보나치 수열이 있습니다.<br>
피보나치 수열은 특정 숫자를 구하기 위해 그 앞의 숫자와 두 칸 앞의 숫자를 더해야합니다.<br>
피보나치 수열의 점화식은 다음과 같습니다. `D[i] = D[i - 1] + D[i - 2]`

### 분할 정복 알고리즘의 단점
단순 분할 정복으로 피보나치 수열을 풀면 이미 해결한 문제를 반복해서 해결하기 때문에 비효율적입니다. (재귀함수)<br> 
n = 5일 때 같은 문제가 여러 번 반복되는 걸 확인할 수 있고, 만약 숫자가 더 커진다면 반복되는 문제의 개수는 엄청나게 늘어날 겁니다.<br> 
이런 경우 다이나믹 프로그래밍을 사용해서 문제를 해결해야 합니다.<br> 

<img width="668" alt="스크린샷 2021-10-29 오후 2 27 52" src="https://user-images.githubusercontent.com/61447654/139384065-af43d13f-7843-4d16-9fad-5b78201ff5ac.png">

다이나믹 프로그래밍은 두 가지 조건을 만족하는 경우에 사용할 수 있다.<br> 
1. 큰 문제를 작은 문제로 나눌 수 있다.<br> 
2. 작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서도 동일하게 적용된다.<br> 
즉, 다이나믹 프로그래밍은 큰 문제를 잘게 나누어 해결하고 나중에 큰 문제를 해결하는 방법입니다.<br> 
이때  `메모이제이션(Memoization)`이 사용된다는 점이 분할 정복과 다릅니다.<br> 
메모이제이션은 이미 계산된 결과를 배열에 저장해놓고 나중에 동일한 계산이 나오는 경우 저장된 값을 반환해주는 방법입니다. -> 동일한 계산을 1번만 하게됩니다. 

### 재귀함수로 피보나치 수열 구현
피보나치 수열은 재귀함수로 간단하게 구현할 수 있습니다.<br> 
n  = 10인 경우에는 55가 정상적으로 잘 출력됩니다. <br> 
하지만 n = 50인 경우에는 계산량이 엄청나게 늘어나기 때문에 실행되지 않습니다.<br> 
이런 문제를 해결하기 위해선 메모이제이션 기법을 사용해야 합니다.

```java
public static void main(String[] args) {
    int result = d(50);
    System.out.println("result = " + result);
}

private static int d(int n) {
    if(n == 1) return 1;
    if(n == 0) return 0;
    return d(n - 1) + d(n - 2);
}
```

### 메모이제이션 기법을 사용해서 피보나치 수열 구현
메모이제이션 기법을 사용하면 계산 결과가 배열에 저장되기 때문에 중복 계산이 일어나지 않습니다.<br> 
n = 50인 경우에도 정상적으로 피보나치 수열이 출력됩니다.

```java
static long[] dp = new long[101];

public static void main(String[] args) {
    long result = fibonacci(100);
    System.out.println("result = " + result);
}

private static long fibonacci(int n) {

    if(n <= 1) return n;
    else if (dp[n] != 0) {
        return dp[n];
    }else {
        return dp[n] = fibonacci(n - 1) + fibonacci(n - 2);
    }
}
```

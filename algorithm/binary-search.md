# 이분 탐색 (Binary Search)
## 개념
- **이분 탐색**은 정렬된 배열에서 범위를 반씩 줄여가며 원하는 값을 찾는 탐색 방법이다.
- 선형 탐색에 비해 최악의 경우에도 시간 복잡도가 더 좋기 때문에 자주 사용되는 탐색 방법이다.

## 구현
이분 탐색을 구현하기 위해서는 다음과 같은 과정이 필요합니다.
1. 배열을 정렬한다. **(매우 중요)**
2. 정렬된 배열에서 왼쪽 끝 인덱스 `left`와 오른쪽 끝 인덱스 `right`를 이용해서 중간 인덱스 `mid`를 찾는다.
3. `mid`와 찾고자 하는 값 `target`을 비교한다.
4. `mid` == `target`이 될 때까지 아래 과정을 반복한다.
	- `mid`보다 `target`이 크다면 `left`를 `mid + 1`로 이동시켜 오른쪽 구간에서 탐색한다.
	- `mid`보다 `target`이 작다면 `right`를 `mid - 1`로 이동시켜 왼쪽 구간에서 탐색한다.
5. `left`와 `right`가 같아질 때까지 일치하는 값이 없다면 -1을 리턴한다.


## 구현 코드
```java
public class BinarySearch {

    public static void main(String[] args) {
        int solution = search(new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9}, 6);
        System.out.println("solution = " + solution);
    }

    public static int search(int[] nums, int target) {

        int n = nums.length;
        int left = 0;
        int right = n - 1;

        while (left <= right) {
            int m = (left + right) / 2;

            if (nums[m] == target) {
                return m;
            } else if (nums[m] >= target) {
                right = m - 1;
            } else if (nums[m] <= target) {
                left = m + 1;
            }
        }

        return -1;
    }
}

```

## 매개변수탐색 (Parameter Search)
- 배열에 target과 정확히 일치하는 값이 없는 경우 사용하며 최적화 문제에 자주 사용되는 탐색 방법이다.
- 매개변수탐색 알고리즘은 내부적으로 이분 탐색 방법을 사용한다.

## 이분탐색 vs 매개변수탐색
- `이분탐색`은 배열안에서 구하고자 하는 값을 찾는 방법이다.
- `매개변수탐색`은 구하자고 하는 값을 찾는 게 아닌 **최대 거리**, **최대 높이**와 같은 최적화된 값을 찾는 방법이다.

## 관련 문제
수 찾기 - https://www.acmicpc.net/problem/1920 <br>
나무 자르기 - https://www.acmicpc.net/problem/2805

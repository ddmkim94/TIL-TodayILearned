# 투포인터 (Two Pointer) :: O(N)

> 리스트에 순차적으로 접근해야 할 때 두 개의 점의 위치를 기록하면서 처리하는 알고리즘 <br>
> 주로 수열에서 부분합을 찾는 문제 or 연속되는 수열의 합이 특정 값을 가지는 것을 확인하는 문제로 출제됨

## 알고리즘 진행 과정

- <b>주어진 수: M, 시작점: start, 끝점: end </b><br>

1. 시작점과 끝점이 첫 번째 원소의 인덱스를 가리키게 한다.
2. 현재 부분합이 M과 같다면 count++
3. 현재 부분합이 M보다 작은 경우 end + 1 `(끝점 + 1)`
4. 현재 부분합이 M보다 크거나 같은 경우 start + 1 `(시작점 + 1)`
5. 모든 경우를 확인 할 때까지 2~4번 과정을 반복!

   ### 그림과 함께 설명하기 🌄
   아래의 그림처럼 하나의 배열이 존재하고 M = 5 를 가진다고 가정해보겠습니다. <br>
   
   - **[초기단계]** : 시작점과 끝점이 첫 번째 인덱스를 가리키도록 합니다. <br><br>
   ![image](https://github.com/ehdals9412/TIL-TodayILearned/blob/38d3f973a8bdc64de184f4fb9e52c0ac3b579a3a/image/1%EB%B2%88.png) <br><br>
   ▶︎ 현재 부분합 : 1 <br>
   ▶︎ 현재 카운트 : 0 <br><br>
   
   - **[1단계]** : 이전 부분합(1) < M --> **`end + 1`** <br><br>
   ![image](https://github.com/ehdals9412/TIL-TodayILearned/blob/38d3f973a8bdc64de184f4fb9e52c0ac3b579a3a/image/2%EB%B2%88.png) <br><br>
   ▶︎ 현재 부분합 : 3 <br>
   ▶︎ 현재 카운트 : 0 <br><br>
   
   - **[2단계]** : 이전 부분합(3) < M --> **`end + 1`** <br><br>
   ![image](https://github.com/ehdals9412/TIL-TodayILearned/blob/38d3f973a8bdc64de184f4fb9e52c0ac3b579a3a/image/3%EB%B2%88.png) <br><br>
   ▶︎ 현재 부분합 : 6 <br>
   ▶︎ 현재 카운트 : 0 <br><br>
   
   - **[3단계]** : 이전 부분합(6) > M --> **`start + 1`** <br><br>
   ![image](https://github.com/ehdals9412/TIL-TodayILearned/blob/38d3f973a8bdc64de184f4fb9e52c0ac3b579a3a/image/4%EB%B2%88.png) <br><br>
   ▶︎ 현재 부분합 : 5 <br>
   ▶︎ 현재 카운트 : 1 <br>
   - **이런 방식으로 마지막 경우까지 모두 검사를 실시한다** <br><br>

   - **[마지막 단계]** <br><br>
   ![image](https://github.com/ehdals9412/TIL-TodayILearned/blob/38d3f973a8bdc64de184f4fb9e52c0ac3b579a3a/image/5%EB%B2%88.png) <br><br>
   ▶︎ 현재 부분합 : 5 (`검사완료`) <br>
   
   
   
   

# 토끼와 거북이 알고리즘(Tortoise and Hare)
### 💡 토끼와 거북이 알고리즘
- 플로이드가 고안한 그래프의 순환 구조를 확인 할 수 있는 알고리즘 (Cycle)
- 두 개의 속도가 다른 포인터가 핵심이다. (거북이는 1칸 토끼는 2칸씩 이동)
- 그래프가 순환 구조를 가지고 있다면 먼저 도착한 토끼는 계속 빙빙 돌고 있고 순환 구조에 늦게 들어온 거북이와 언젠간 만나게 될 것이라는 이론
- 거북이와 토끼가 만난다면 순환 구조를 가졌다는 뜻이고 만나지 않는다면 순환 구조를 가지지 않았다는 것을 뜻한다.
- 순환 구조의 시작 위치를 알고 싶다면 토끼와 거북이가 만난 자리에서 거북이를 처음으로 옮긴 뒤 토끼와 거북이를 한 칸씩 이동하다 보면 만나는 지점이 순환 구조의 시작 위치가 된다.
- 연결 리스트의 사이클의 존재 유무, 사이클 시작점, 사이클의 길이를 시간복잡도 O(N)으로 알아낼 수 있는 알고리즘 입니다.
- 관련 문제 : https://leetcode.com/problems/linked-list-cycle/

### cycle 유무 찾기
- 토끼와 거북이는 리스트의 시작점에서 출발합니다.**(거북이 1칸 토끼는 2칸씩 이동)**
- 만약 리스트에 사이클이 있다면 토끼와 거북이는 언젠가 만나게 됩니다. 

<img width="500" src="https://user-images.githubusercontent.com/61447654/139800300-5e909f0f-7c26-4656-8374-5e62a5cf2ebc.png">
<img width="500" src="https://user-images.githubusercontent.com/61447654/139800308-3c0dc1c3-041e-4fab-a6f1-9792516b11d5.png">
<img width="500" src="https://user-images.githubusercontent.com/61447654/139800313-3627126b-6f68-4d80-a3d2-44652361e737.png">

<hr>

### cycle 시작점 찾기
- 토끼와 거북이가 만났다면 거북이만 시작점으로 돌려보냅니다.
- 거북이와 토끼 모두 한 칸씩 이동하면서 둘이 처음으로 만나는 지점이 사이클의 시작점이 됩니다.

<img width="500" src="https://user-images.githubusercontent.com/61447654/139800942-2d772f0b-2b1c-4afe-9e04-a816fb94409e.png">
<img width="500" src="https://user-images.githubusercontent.com/61447654/139800951-22bd77d2-1bb1-4717-b5a0-7e62d0d5e223.png">

<hr>

### cycle 길이 구하기
- 사이클 시작점에서 토끼만 한 칸씩 이동하면서 길이를 세줍니다.
- 토끼가 다시 거북이가 있는 자리에 오게되면 그 때의 길이가 사이클의 길이가 됩니다.
- 아래 리스트의 사이클의 길이는 3이 됩니다.

<img width="500" src="https://user-images.githubusercontent.com/61447654/139801268-06eaf006-bf10-4ca0-bfa0-5bb8d798fe96.png">

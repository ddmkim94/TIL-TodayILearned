# DFS와 BFS 알고리즘

## 그래프(Graph)란?
- 정점(V)과 간선(E)으로 이루어진 자료구조의 일종, **G = (V,E)**
- 정점은 데이터가 저장되는 노드를 말하고 간선은 정점을 연결하는 선을 말한다.
- 그래프의 종류에는 무방향 그래프(**양방향**)와 방향 그래프(**단방향**)가 있다.

## 그래프 탐색
- 하나의 정점에서 시작해서 차례대로 모든 정점들을 한 번씩 방문하는 것
- 그래프 탐색 방법에는 DFS(**깊이 우선 탐색**)와 BFS(**너비 우선 탐색**)이 있다.
- DFS, BFS 탐색 둘 다 모든 정점을 한 번만 탐색하는 방법이지만 탐색 방법에 차이가 있다.
- 그래프 탐색의 경우 어떤 노드를 방문했는지를 반드시 검사해줘야한다. (무한루프에 빠질 수 있음) <br>
  아래 그림은 DFS와 BFS의 탐색 과정을 보여주는 그림이다. <br><br>
![2254723E588084F830](https://user-images.githubusercontent.com/61447654/140282691-862c84a2-5c6b-4825-a3a5-2615b2f333ef.gif)

## 깊이 우선 탐색 (DFS, Depth-First Search)란?
- 루트 노트(혹은 임의의 노드)에서 시작하여 다음 분기(branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법
- 미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.
- 넓게 탐색하기 전에 깊게 탐색하는 방법이다.
- 모든 노드를 방문해야할 때 DFS 탐색을 사용한다.
- 구현은 BFS보다 간단하지만 검색 속도는 BFS에 비해서 느리다.
  ### DFS의 특징
- 자기 자신을 호출하는 순환 알고리즘 형태를 가진다.
- `스택(Stack)`과 `재귀`로 구현 할 수 있다.

## 너비 우선 탐색 (BFS, Breadth-First Search)란?
- 루트 노트(혹은 임의의 노드)에서 시작해서 가까운 노드부터 탐색하는 방법
- 시작 노드에서 가까운 노드부터 방문하고 멀리 떨어진 노드는 나중에 방문하는 방법이다.
- 깊게 탐색하기 전에 넓게 탐색하는 방법이다.
- 두 노드 사이의 최단 경로를 찾을 때 사용한다.
  ### BFS의 특징
- 재귀적으로 동작하지 않는다.
- 방문한 노드들을 차례대로 저장하고 반환할 수 있는 큐를 사용하여 구현 -> **선입선출(FIFO) 방식으로 탐색**

# 자료구조 (data structure)
- 효율적인 접근 및 수정을 가능하게하는 자료의 집합을 의미하며, 각 원소들이 논리적으로 정의된 규칙에 의해 나열되며 자료에 대한 처리를 효율적으로 수행할 수 있도록 자료를 구분하여 표현한 것이다.
- 자료를 더 효율적으로 저장 & 관리하기 위해 사용하며, 적절한 자료구조의 사용은 메모리 용량의 절약시켜주고 실행시간을 단축시켜줄 수 있다.

## 자료구조의 선택 기준
- 자료의 처리 시간
- 자료의 크기
- 자료의 활용 빈도
- 자료의 갱신 정도
- 프로그램의 용이성

## 자료구조의 특징
### 1. 효율성
자료구조의 사용 목적은 효율적인 데이터의 관리 및 사용이다. 따라서 적절한 자료구조를 선택하여 사용한다면 데이터 관리가 훨씬 수월해질 수 있다. <br>
예를 들어, 검색 알고리즘을 구현할 때 데이터의 양이 엄청나게 많은 경우에는 순차 검색보다 이분 검색을 사용하는 게 더 효율적이다. <br>
데이터가 100만개가 있다고 가정했을 때 순차 검색으로 데이터를 검색하게 되면 1번의 검색으로도 데이터를 찾을 수 있지만 최악의 경우 100만번의 검색을 해야할 수도 있다. <br>
하지만 이분 검색을 사용한다면 보다 효율적인 검색 알고리즘을 구현할 수 있다. 이처럼 목적에 맞는 자료구조를 사용하는 것이 효율적이다.

### 2. 추상화
추상화란 복잡한 자료, 모듈, 시스템 등으로 부터 핵심적인 개념만 간추려 내는 것이다.<br>
자료구조 내부의 구현은 중요하지 않습니다. 어떻게 구현했는지 보다 어떻게 사용해야 하는지를 알고 있어야 한다.<br>
자료구조의 내부 구현을 몰라도 자료구조의 추상적인 개념을 알고있다면 사용할 수 있다.

### 3. 재사용성
자료구조는 특정 프로그램에서만 동작하도록 설계하지 않는다.<br>
다양한 프로그램에서 동작할 수 있도록 범용성있게 설계하기 때문에 해당 프로젝트가 아닌 다른 프로젝트에서도 사용이 가능하다.


## 자료구조의 분류
- 자료구조는 크게 선형 구조와 비선형 구조로 나뉜다.
<img width="700" src="https://user-images.githubusercontent.com/61447654/141278619-1cfab4fd-ff42-4fb3-985c-c1640d0a7009.png">

- **선형구조(Linear)** : 데이터가 순차적으로 나열시킨 형태 `[배열, 연결리스트, 스택, 큐]`
<img width="500" src="https://user-images.githubusercontent.com/61447654/141278450-a6233e44-1aaa-4157-857d-400ec680a2cb.jpg">

- **비선형구조(NonLinear)** : 하나의 데이터 뒤에 여러개의 데이터가 존재할 수 있는 형태 `[트리, 그래프]`
<img width="300" height="300" src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile9.uf.tistory.com%2Fimage%2F25FBB63359719D6937A583">


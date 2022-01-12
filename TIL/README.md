# TIL
## January
  1. 코딩테스트 준비
  2. 경험 정리 및 마스터 자소서 작성
  3. CS 면접 준비
  4. 데이콘

<details markdown="1">
<summary>22.01.10</summary>
</br>

__강의__
- [x] SDS 알고리즘 특강 듣기

__알고리즘__
- [x] 알고리즘 문제 5개 풀기

* [2667 단지번호붙이기](https://www.acmicpc.net/problem/2667)  /  [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/BFS%2BDFS/BackJoon/2667.py)  
  * `DFS`
  * DFS 돌면서 1이면 count증가  

* [11722 가장 긴 감소하는 부분수열](https://www.acmicpc.net/problem/11722)  /  [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/DP/11722.py)  
  * `DP`
  * dp에 i까지 감소한 수들 개수 넣기, 현재 수 이전의 수들 다 돌면서 이전의 수가 더 크면 max(dp[현재], dp[이전]+1)
* [11053 가장 긴 증가하는 부분수열](https://www.acmicpc.net/problem/11053)  /  [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/DP/11053.py) 
  * `DP`

* [1717 집합의 표현](https://www.acmicpc.net/problem/1717)  /   [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1717.py)  
  * `Union-find`
  * 파이썬 RecusionError 주의
* [1197 최소 스패닝 트리](https://www.acmicpc.net/problem/1197)  /   [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1197.py) 
  * `MST` `크루스칼`  
  * V 정렬, Uninon-find로 사이클 탐지, 사이클 없으면(find 결과 다르면) union하고 cost 더하기


__취업 준비__  
- [X] 자소서 특강 듣기
    
</details>

<details markdown="1">
<summary>22.01.11</summary>
</br>

__알고리즘__
- [X] 알고리즘 문제 5개 풀기 -> 4개

* [1753 최단경로](https://www.acmicpc.net/problem/1753) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1753.py)
  * `Dijkstra`
  * heapq.heappush(queue, (가중치, 노드)) 튜플 내 순서 중요  
    heapq에 튜플넣을 때 튜플 맨 앞에 있는 값을 기준으로 최소 힙이 구성된다.
  * Python 시간초과 주의
    반복문으로 여러 줄 입력받을 때는 input()대신 sys.stdin.readline()
    ```python
    import sys
    input = sys.stdin.readline
    ```
* [1238 파티](https://www.acmicpc.net/problem/1238) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1238.py)
  * `Dijkstra`
  * 각 학생마다 파티 장소로 가는 최단 거리 테이블 + 파티 장소에서 집으로 오는 최단거리 테이블

* [5014 스타트링크](https://www.acmicpc.net/problem/5014) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/BFS%2BDFS/BackJoon/5014.py)
  * `BFS`
  * 큐 사용해서 현재 위치에서 업/다운, 이미 방문했던 곳 큐에 넣지 말기
  
* [1520 내리막길](https://www.acmicpc.net/problem/1520) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/BFS%2BDFS/BackJoon/1520.py)
  * `DFS` `DP`
  * DFS로만 하면 시과초과가 나서 DP를 적용해야 함  
  <img src="https://user-images.githubusercontent.com/49435163/149088599-b266b4b0-442c-43be-9f47-82709a2273ed.png" width="500" height="250"/>
  
__취업 준비__ 
- [ ] 마스터 자소서 작성 

</details>

<details markdown="1">
<summary>22.01.12</summary>
</br>

__알고리즘__
- [x] 알고리즘 문제 3개 풀기
* [19238 스타트택시](https://www.acmicpc.net/problem/19238) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/BFS%2BDFS/BackJoon/19238.py)
  * `BFS`

* [1976 여행가자](https://www.acmicpc.net/problem/1976) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1976.py)
  * `Union-Find`
  * 연결된 여행지 Union, 가고자 하는 여행지 find했을 때 같으면 YES
* [1939 중량제한](https://www.acmicpc.net/problem/1939) / [풀이](https://github.com/sala0320/Daily_Algorithm/blob/main/Graph/BackJoon/1939.py)
  * 

__인공지능__
- [x] 데이콘 리더보드 제출

__취업 준비__ 
- [x] LG 자소서 작성 

  
</details>

<details markdown="1">
<summary>22.01.13</summary>
</br>

__알고리즘__
- [ ] 코딩테스트
- [ ] 알고리즘 문제 1개 풀기

__인공지능__
- [ ] 데이콘 리더보드 제출

__취업 준비__ 
- [ ] 면접 스터디 준비 
- [ ] LG 자소서 작성 

</details>

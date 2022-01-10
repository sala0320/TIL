# MST(Minimum Spanning Tree)
### 신장트리

하나의 그래프가 있을 때 모든 노드를 포함하면서 사이클이 존재하지 않는 부분 그래프

### 최소 신장 트리

그래프에서 간선의 가중치의 합이 최소힌 신장트리

- 프림 - 간선 많을 때
- 크루스칼 - 간선 적을 때

### 크루스칼 알고리즘
__풀이 방법__
1. 간선 데이터를 비용에 따라 오름차순을 정렬
2. 간선을 하나씩 확인하며 현재의 간선이 사이클이 발생하는지 확인
    - 사이클 X → 최소 신장트리에 포함
    - 사이클 O → 최소 신장트리에 포함 X
3. 모든 간선에 대해서 step 2 반복

```python
def find(parent, x):
    if parent[x] != x:
        parent[x] = find(parent,parent[x])
    return parent[x]

def union(parent, a, b):
    a = find(parent, a)
    b = find(parent, b)
    if a < b:
        parent[b] = a
    else:
        parent[a] = b

v, e = map(int, input().split())
parent = [0] * (v+1)
edges = []
result = 0

for i in range(v+1):
    parent[i] = i

for _ in range(e):
    a,b,cost = map(int, input().split())
    edges.append((cost,a,b))

edges.sort()

for edge in edges:
    cost, a, b = edge
    if find(parent, a) != find(parent, b):
        union(parent, a, b)
        result += cost
print(result)
```

### 프림 알고리즘
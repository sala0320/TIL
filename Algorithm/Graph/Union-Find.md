# Union-Find
- 각 노드마다 연결된 1개의 노드가 주어질 때, 트리를 구성하여 최상단 노드가 서로 같은 경우 같은 집단에 속함
  
1. 모든 부모노드를 자기 자신으로 초기화 
2. 연결관계가 주어질 때마다 union함수를 통해 트리를 구성
3. find함수를 통해 최상단 노드를 찾고 경로 압축
   

```python
# find 연산 
def find(target):
    if parent[target]!= target:
        parent[target] = find(parent[target])
    return parent[target]

# union 연산
def union(a, b):
    a = find(a)
    b = find(b)
 
    # 작은 루트 노드를 기준으로 합침
    if a < b:
        parent[b] = a
    else:
        parent[a] = b
 
parent = [0, 1, 2, 3, 4, 5]
 
# 노드 3과 노드 5가 같은 집합인지 비교
# 출력 결과 : 다른 집합입니다!
if find(3) == find(5):
    print("같은 집합입니다!")
else:
    print("다른 집합입니다!")
 
# 노드 3과 노드 5를 union 연산(합침)
union(3, 5)
 
# 노드 3과 노드 5가 같은 집합인지 비교
# 출력 결과 : 같은 집합입니다!
if find(3) == find(5):
    print("같은 집합입니다!")
else:
    print("다른 집합입니다!")
```
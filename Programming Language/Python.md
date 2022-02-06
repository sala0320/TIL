# Python
- [입출력 및 초기화](#입출력-및-초기화)
- [List, Array](#List,-Array)
- [Pythonic code](#Pythonic-code)
- [얕은 복사, 깊은 복사](#얕은-복사,-깊은-복사)
## 입출력 및 초기화
### 공백을 기준으로 구분된 데이터 받을 때

```python
data = list(map(int, input().split()))
a,b,c = map(int, input().split())
a,b,c = int(input().split())
board = [list(map(int, input().split())) for _ in range(n)]
```

### 좀 더 빠르게 입력받기

```python
import sys

X,Y = map(int, sys.stdin.readline().split())
#2차원 리스트 입력받기
board = [list(map(int, sys.stdin.readline().split())) for _ in range(X)]
board = [list(map(int, input().split())) for _ in range(X)]
#문자열 입력받기
data= sys.stdin.readline().rstip()
```

### 2차원 배열 초기화

```python
# COLUM : 가로 길이
# ROW : 세로 길이
board = [[0 for i in range(COLUM)] for j in range(ROW)]
```

## List, Array
### 패킹과 언패킹

```python
t = [1, 2, 3] # 1,2,3을 변수 t에 패킹
a , b , c = t # t에 있는 값 1, 2, 3 을 변수 a, b, c에 언패킹
print(t, a, b, c) 
>>> [1, 2, 3] 1 2 3
```
### 리스트 행열 변환

```python
arrr = [[1,2,3],[4,5,6]]
[list(x) for x in zip(*arr)]
list(map(list, zip(*arr)))
```
### Concatenation

```python
color = ['red', 'blue', 'green']
color2 = ['orange', 'black', 'white']
print (color + color2) # 두 리스트 합치기
>>> ['red', 'blue', 'green','orange', 'black', 'white']

print (color * 2) # color 리스트 2회 반복
>>> ['red', 'blue', 'green', 'red', 'blue', 'green']
```

### append, extend, insert, remove, del
- append  
  새로운 요소를 array맨끝에 객체로 추가, **입력한 값이 리스트와 같은 반복 가능한 iterable 자료형이더라도 객체로 저장**
- extend  
  입력한 iterable 자료형의 항목 각각을 array의 끝에 하나씩 추가

```python
color[0] = 'yellow'
color.append("white") # 리스트에 “white” 추가
color.extend(["black","purple"]) # 리스트에 새로운 리스트 추가
color.insert(0,"orange") # 0번째 주소에 “orange” 추가
print (color)
>>> ['orange', 'yellow', 'blue', 'green', 'white', 'black', 'purple']

color.remove("white") # 리스트에 “white” 삭제
del color[0] # 0번째 주소 리스트 객체 삭제
print (color)
>>> ['yellow', 'blue', 'green', 'black', 'purple']
```

### 리스트 메모리 저장방식

파이썬은 리스트 변수에는 리스트 주소값이 저장됨

```python
a = [5, 4, 3, 2, 1]
b = [1, 2, 3, 4, 5]

**b = a** #b의 메모리 주소에 a의 메모리 주소를 연결
print (b)
>>> [5, 4, 3, 2, 1]

a.sort() #b의 메모리 주소에 a의 메모리 주소가 연결되어있으므로 a를 sort하면 b는 sort된 a를 가리키게 됨
print (b) 
>>> [1, 2, 3, 4, 5] 

b = [6,7,8,9,10] #b가 a의 주소값을 가리키는 것을 해제하고 싶으면 값을 새로 할당하기
print (a, b)
>>> [1, 2, 3, 4, 5] [6, 7, 8, 9, 10]

#----------------------------------------------------------------#

**c = a[:]** #a의 값을 c에 복사
print (c) 
>>> [5, 4, 3, 2, 1]

a.sort() #a와 b의 메모리 주소가 연결되어 있지 않기 때문에 a를 sort해도 b의 값은 변하지 않는다
print (c) 
>>> [5, 4, 3, 2, 1]
```

### 이차원 리스트 복사

```python
kor_score = [49,79,20,100,80]
math_score = [43,59,85,30, 90]
eng_score = [49,79,48,60,100]
midterm_score = [kor_score, math_score, eng_score]

**midterm_copy = midterm_score[:]**
#1차원리스트에서는 원본리스트가 바뀌어도 복사된 리스트는 바뀌지 않지만,
#2차원리스트에서는 원본리스트가 바뀌면 복사된 리스트도 바뀜
midterm_score[0][0] = 10
print(midterm_score)
>>> [[10,79,20,100,80], [43,59,85,30, 90], [49,79,48,60,100]]
print(midterm_copy)
>>> [[10,79,20,100,80], [43,59,85,30, 90], [49,79,48,60,100]]

#----------------------------------------------------------#
import copy
**midterm_deepcopy = copy.deepcopy(midterm_score)**
# 원본 리스트가 바뀌어도 복사된 리스트는 안바뀌게 하고 싶으면, copy모듈 이용해서 deepcopy사용하기
midterm_score[0][0] = 500
print(midterm_score)
>>> [[500,79,20,100,80], [43,59,85,30, 90], [49,79,48,60,100]]
print(midterm_deepcopy)
>>> [[10,79,20,100,80], [43,59,85,30, 90], [49,79,48,60,100]]
```


## Pythonic code
### list/set/dict Comprehension

```python
#list
[i*j for i in range(1,6) for j in range(7,10)]
#set
(i*j for i in range(1,6) for j in range(7,10))
#dict
score_tuples = [('math', 90), ('history', 80), ('english', 95), ('computer engineering', 100)]
score_dict = {t[0]: t[1] for t in score_tuples}
```

- If문

```python
mylist = [3, 2, 6, 7]
answer = []
for number in mylist:
    if number % 2 == 0:
        answer.append(number**2)
#----------------------------------------------------------#
answer = [number**2 for number in mylist if number % 2 == 0]

case_1 = ["A","B","C"]
case_2 = ["D","E","A"]

result = [i+j for i in case_1 for j in case_2 if not(i==j)]
# Filter: i랑 j과 같다면 List에 추가하지 않음
# [i+j if not(i==j) else i for i in case_1 for j in case_2]
>>> ['AD', 'AE', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']
result.sort()
>>> ['AD', 'AE', 'BA', 'BD', 'BE', 'CA', 'CD', 'CE']
```

- 2차원

```python
case_1 = ["A","B","C"]
case_2 = ["D","E","A"]
result = [i+j for i in case_1 for j in case_2]
>>> ['AD', 'AE', 'AA', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']

result = [ [i+j for i in case_1] for j in case_2]
>>> [['AD', 'BD', 'CD'], ['AE', 'BE', 'CE'], ['AA', 'BA', 'CA']]
```

### enumerate

```python
for index, value in enumerate(a, start=1): #index 1부터
		print(index, value)
```

[https://freedeveloper.tistory.com/271](https://freedeveloper.tistory.com/271)

### lambda

lambda 인자 : 표현식

```python
def hap(x, y):
	return x + y

hap(10, 20) >>> 30

#----------------------------------------------------------------3
(lambda x,y: x + y)(10, 20) >>> 30
```

### Map

map(적용시킬 함수, 적용할 값들) 
: 리스트로부터 원소를 하나씩 꺼내서 함수를 적용시킨 다음, 그 결과를 새로운 리스트에 담아준다

```python
# 예제1) 리스트의 값을 정수 타입으로 변환 
result1 = list(map(int, [1.1, 2.2, 3.3, 4.4, 5.5])) 
print(f'map(int, 리스트) : {result1}') 

# 예제2) 리스트 값 제곱 
map(lambda x: x ** 2, [0,1,2,3,4]))             # 파이썬 2
>>> [0, 1, 4, 9, 16]  
list(map(lambda x: x ** 2, range(5)))     # 파이썬 2 및 파이썬 3
>>> [0, 1, 4, 9, 16]
```

 
- list여러개일때 list끼리 더하기

```python
a = [1,0]
b = [1,0]
c = [0,1]
d = [1,0]
list(map(sum, zip(a,b,c,d)))
output : [3,1]
```

### Iterable Object

```python
cities = ["Seoul", "Busan", "Jeju"] 
iter_obj = iter(cities) # 메모리저장
>>> <list_iterator at 0x16ace72410>
print(next(iter_obj)) 
>>> 'Seoul'
print(next(iter_obj))
>>> 'Busan'
```

### Generator

Iterable object보다 메모리를 절약할 수 있다.

![image](https://user-images.githubusercontent.com/49435163/152673633-a791624f-cff3-4984-a396-a47e5d67d465.png)


```python
def geneartor_list(value):
	result = []
	for i in range(value):
		yield i

result = generator_list(50)
print(next(result))
>>> 0
print(next(result))
>>> 1

#---------------------------------------------------------------#
# comprehension으로 구현
gen = (n*n for n in range(50))
for value in gen:
	print(value)
>>> 0 1 ...

# generator는 이전값을 기억하지 않고 부르는 값만을 반환하기 때문에,
# 한번 소비되면 다시 값을 부르지 못함
for value in gen:
	print(value)
>>> ...

```

### Asterisk

- 가변인자

개수가 정해지지 않은 변수를 함수의 parameter로 사용하는 법

입력된 값은 tuple type으로 사용

```python
def asterisk_test(a, b,*args):
	 return a+b+sum(args)

print(asterisk_test(1, 2, 3, 4, 5)) #[3,4,5]가 tuple형태로 *args로
```

- 키원드 가변인자

Parameter 이름을 따로 지정하지 않고 입력하는 방법 

입력된 값은 dict type으로 사용

```python
def kwargs_test_3(one,two,*args,**kwargs):
	print(one+two+sum(args))
	print(kwargs)

kwargs_test_3(3,4, 1,2, first=3, second=4, third=5)
>>> 10
>>> {'first':3, 'second':4, 'third':5}
```

- Unpacking

```python
def asterisk_test(a, *args):
	print(a, **args**)

asterisk_test(1, ***(2,3,4,5,6)**) # *하면 (1,2,3,4,5,6)형식으로 unpacking
>>> 1, (2,3,4,5,6)
asterisk_test(1, **(2,3,4,5,6)**)
>>> 1 ((2,3,4,5,6),)

a, b, c = ([1, 2], [3, 4], [5, 6])
print(a, b, c)
data = ([1, 2], [3, 4], [5, 6])
print(*data)
>> [1,2] [3,4] [5,6]
```

### 아스키/진법 변환
- 문자 -> 아스키
```python
print(chr(10)) #문자->아스키 C
print(ord('C')) #아스키 -> 문자 10
```
- n진수 → 10진수

```python
int(string, base)

print(int('111',2))
print(int('222',3))
print(int('333',4))
```

- 10진수 → 2, 8, 16진수

```python
print(bin(10))
print(oct(10))
print(hex(10))
```
## 얕은 복사, 깊은 복사
### 얕은 복사 (Shallow copy)

```python
# 얕은 복사
a = [1, 2, 3]
b = a

print(id(a), id(b)) # 두 개의 주소값 같음
print(a, b) # 주소가 같기 때문에 값 또한 같음

a[0] = 4 
print(a, b)
```

```
139768593349440 139768593349440
[1, 2, 3] [1, 2, 3]
[4, 2, 3] [4, 2, 3]
```

주소값이 같기에, a[0]만 변경했음에도 불구하고 b[0] 또한 같이 변경됨


💡 한가지 주의할 점은 위의 경우처럼 복사된 참조 변수를 수정했을때, 처음에 할당한 참조 변수의 값 역시 똑같이 수정되는 것은 **리스트와 같은 변경가능(mutable) 객체일 때만 해당**한다는 것입니다. 숫자나 문자열과 같은 불변의(immutable) 객체일때는 위의 경우가 해당되지 않습니다.
- Immutable인 상수와 string의 경우

```python
a = 10
b = a
print(b)    # 10 출력력
b = "abc"
print(b)    # abc 출력
print(a)    # 10 출력
```

```
10
abc
10
```

상수값과 string의 경우 각각이 다르게 표시된다.

### 깊은 복사(Deep copy)

```python
a = [1, 2, 3]
b = a[:]

print(id(a), id(b)) # 두 개의 주소값 같음
print(a, b) # 주소가 같기 때문에 값 또한 같음

a[0] = 4 
print(a, b)
```

```
1986080649600 1986080663040
[1, 2, 3] [1, 2, 3]
[4, 2, 3] [1, 2, 3]
```

깊은 복사의 경우에는 각각의 값의 주소값이 달라지고, 그 주소에 새롭게 값이 들어가므로 해당 값을 바꾸더라도 copy해 온 또는 copy한 값이 변경되지 않는다.

### 주의할 내용
 shallow copy와 deep copy의 표현이 어디를 기준으로 표현하는 지에 따라 다르다.

**단일 리스트의 경우**

- 단순 할당

```python
a = [1, 2, 3]
b = a
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(4)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소 주소 :', id(a[1]))
print('b의 원소 주소 :', id(b[1]))
```

```
a의 id:  1752289564736
b의 id:  1752289564736
a의 값:  [1, 2, 3, 4]
b의 값:  [1, 2, 3, 4]
==================
a의 원소 주소 : 140705754916672
b의 원소 주소 : 140705754916672
```

단순 할당을 할 경우, 각각의 list가 가지는 주소가 같기 때문에 얕은 복사에 해당된다.

- 리스트 슬라이싱하여 복사

```python
a = [1, 2, 3]
b = a[:]
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(4)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소 주소 :', id(a[1]))
print('b의 원소 주소 :', id(b[1]))
```

```
a의 id:  1752289375168
b의 id:  1752289633792
a의 값:  [1, 2, 3]
b의 값:  [1, 2, 3, 4]
==================
a의 원소 주소 : 140705754916672
b의 원소 주소 : 140705754916672
```

list를 슬라이싱하여 값을 복사할 경우, 각각의 list가 가리키는 주소값이 달라지므로 깊은 복사에 해당된다.

- Deep copy를 이용한 복사

```python
import copy

a = [1, 2, 3]
b = copy.deepcopy(a)
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(4)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소 주소 :', id(a[1]))
print('b의 원소 주소 :', id(b[1]))
```

```
a의 id:  1752289634752
b의 id:  1752289633472
a의 값:  [1, 2, 3]
b의 값:  [1, 2, 3, 4]
==================
a의 원소 주소 : 140705754916672
b의 원소 주소 : 140705754916672
```

외장함수를 이용하여 deep copy를 하였을 때에도 마찬가지로 각각의 list가 가지고 있는 주소값이 다르므로 깊은 복사에 해당된다.

### 이중 리스트의 경우

- 단순 할당

```python
x = [1, 2, 3]
y = [4, 5, 6]
z = [7, 8, 9]
k = [10, 11, 12]

a = [x, y, z]
b = a
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(k)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소y 주소 :', id(a[1]))
print('b의 원소y 주소 :', id(b[1]))
```

```
a의 id:  1752289975808
b의 id:  1752289975808
a의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]
b의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]
==================
a의 원소y 주소 : 1752289973248
b의 원소y 주소 : 1752289973248
```

이중 리스트에서 단순 할당의 경우, 바깥 리스트와 내부 리스트의 주소가 모두 각각 동일하다. 그러므로 둘 다 얕은 복사에 해당된다.

- 리스트 슬라이싱 하여 복사

```python
x = [1, 2, 3]
y = [4, 5, 6]
z = [7, 8, 9]
k = [10, 11, 12]

a = [x, y, z]
b = a[:]
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(k)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소y 주소 :', id(a[1]))
print('b의 원소y 주소 :', id(b[1]))
```

```
a의 id:  1752289973824
b의 id:  1752289973888
a의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
b의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]
==================
a의 원소y 주소 : 1752289926528
b의 원소y 주소 : 1752289926528
```

이중리스트를 슬라이싱을 통해 복사할 경우, 바깥 리스트의 주소는 서로 다른 값이 되지만 내부 리스트의 주소값은 같은 곳을 가리키게 된다. 그래서 이러한 경우에 바깥 리스트를 기준으로는 깊은 복사가 되지만 내부 리스트를 기준으로는 얕은 복사가 되는 것이다.

결국 외부에 감싸고 있는 리스트의 주소와 내부 리스트의 주소 중 어떤 것을 기준으로 깊은 복사인지 얕은 복사인지 구분할 것인지에 따라 다르게 얘기할 수 있다.

- Deep copy를 이용한 복사

```python
import copy

x = [1, 2, 3]
y = [4, 5, 6]
z = [7, 8, 9]
k = [10, 11, 12]

a = [x, y, z]
b = copy.deepcopy(a)
print('a의 id: ', id(a))
print('b의 id: ', id(b))
b.append(k)
print('a의 값: ', a)
print('b의 값: ', b)

print('==================')
print('a의 원소y 주소 :', id(a[1]))
print('b의 원소y 주소 :', id(b[1]))
```

```
a의 id:  1752290221120
b의 id:  1752289645120
a의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
b의 값:  [[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12]]
==================
a의 원소y 주소 : 1752289772800
b의 원소y 주소 : 1752289647872
```

외장 함수인 deepcopy()를 사용하면 바깥 리스트와 내부 리스트 모두 주소값이 각각 다른 것을 확인 할 수 있다. 그래서 deepcopy() 외장 함수를 통해 복사하는 것은 원래 이러한 내부리스트의 얕은 복사 문제를 해결하기 위해 수행한다고 볼 수 있다.

### 결론

- 주소값이 달라진다 → 깊은 복사
- 주소값이 같다 → 얕은 복사

결국 Deep copy란 mutable한 내부 객체(ex 내부 리스트)의 문제를 해결하기 위해 사용하는 함수로 슬라이싱을 통해 값을 copy하는 경우 외부 리스트는 원본과 복사본이 각각 주소값이 달라지므로, **외부 리스트**는 **깊은 복사**가 된 것이라고 볼 수 있고, **내부 리스트**의 경우는 각 값의 주소값이 같으므로 **얕은 복사**가 진행 되었다고 생각하면 된다.
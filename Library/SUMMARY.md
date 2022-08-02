# Summary
## - Catalog
* collections  
(1) deque()  
(2) Counter(`list` or `string`)  
(3) defaultdict(`data_type`)

* itertools  
(1) combinations(`list` or `string`, `'뽑은 개수'`)    
(2) combinations_with_replacement(`list` or `string`, `'뽑은 개수'`)    
(3) permutations(`list` or `string`, `'뽑은 개수'`)  
(4) product(`list` or `string`, repeat=`'뽑은 개수'`)



## - `collections`
### (1) `deque`
* How to import?  
`from collections import deque`
* Basic Usage    
```python
# Queue 구현
from collections import deque

q = deque([1,2,3])
q.append(1)
print(q) #deque([1, 2, 3, 1])

q.popleft()
print(q) #deque([1, 2, 3])
```
- Example
```python
# In BFS,
from collections import deque

def bfs(x,y):
    dxs, dys = [-1, 1, 0, 0], [0, 0, -1, 1]
    queue = deque((x,y))
    while queue:
        x, y = queue.popleft()
        for dx, dy in zip(dxs, dys):
            nx, ny = x+dx, y+dy
            # nx, ny로 갈 수 있다면,
            if can_go(nx, ny):
                queue.append((nx, ny))
                #방문 체크
```
### (2) `Counter`
* How to import?  
`from collections import Counter`

* Basic Usage
``` python
Counter('list' or 'string')
```

* Example
```python
from collections import Counter

num_list = [1,2,2,3,3,3,4,4,4,4,5]
counter = Counter(num_list)
print(counter)
# Counter({4: 4, 3: 3, 2: 2, 1: 1, 5: 1})

num_string = 'hello world'
counter = Counter(num_string)
print(counter)
# Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, ' ': 1, 'w': 1, 'r': 1, 'd': 1}) 
```
### (3) `defaultdict`
* How to import?  
`from collections import defualtdict`

* Basic Usage
``` python
defaultdict('data type')
```

* Example
```python
from collections import defaultdict

person_dict = defaultdict(int)
person_dict['muji'] = 3
person_dict['peach'] += 1 
# 자동적으로 person_dict['peach']의 값이 0으로 초기화되어 1이 저장

print(person_dict) #defaultdict(<class 'int'>, {'muji': 3, 'peach': 1})
```
## - `itertools`
### (1) `combinations`
* How to import?  
`from itertools import combinations`

* Basic Usage
```python
# 조합
combinations('list' or 'string', '뽑는 개수')
```
* Example
``` python
from itertools import combinations

num_list = [1,2,3,4,5]
result = list(combinations(num_list, 2))
print(len(result))
# 5C2 = 10

print(result) 
# [(1, 2), (1, 3), (1, 4), (1, 5), (2, 3), (2, 4), (2, 5), (3, 4), (3, 5), (4, 5)]

```


### (2) `combinations_with_replacement`
* How to import?  
`from itertools import combinations_with_replacement`

* Basic Usage
``` python
# 중복 조합(자기 자신을 중복해서 뽑는 경우를 추가한 조합)
combinations_with_replacement('list' or 'string', '뽑는 개수')
```

* Example
```python
from itertools import combinations_with_replacement

num_list = '12345'
result = combinations_with_replacement(num_list, 2)
print(len(result)) 
# 5C2+5(자기 자신을 2번 뽑은 경우) = 15


print(result)
# [('1', '1'), ('1', '2'), ('1', '3'), ('1', '4'), ('1', '5'), ('2', '2'), ('2', '3'), ('2', '4'), ('2', '5'), ('3', '3'), ('3', '4'), ('3', '5'), ('4', '4'), ('4', '5'), ('5', '5')]
```

### (3) `permutations`
* How to import?  
`from itertools import permutations`

* Basic Usage
``` python
# 순열
permutations('list' or 'string', '뽑는 개수')
```

* Example
```python
from itertools import permutations

num_list = '12345'
result = list(permutations(num_list, 2))
print(len(result))
# 5P2 = 5*4 = 20

print(result)
# [('1', '2'), ('1', '3'), ('1', '4'), ('1', '5'), ('2', '1'), ('2', '3'), ('2', '4'), ('2', '5'), ('3', '1'), ('3', '2'), ('3', '4'), ('3', '5'), ('4', '1'), ('4', '2'), ('4', '3'), ('4', '5'), ('5', '1'), ('5', '2'), ('5', '3'), ('5', '4')]
```

### (4) `product`
* How to import?  
`from itertools import product`

* Basic Usage
``` python
# 중복 순열
product('list' or 'string', repeat='뽑는 개수')
```

* Example
```python
from itertools import product

num_list = [1,2,3,4,5]
result = list(product(num_list, repeat=2))
print(len(result))
# 5π2 = 5^2 = 25
# 5P2(순열) + 5(자기 자신을 2번 뽑은 경우) = 25

print(result)
# [(1, 1), (1, 2), (1, 3), (1, 4), (1, 5), (2, 1), (2, 2), (2, 3), (2, 4), (2,5), (3, 1), (3, 2), (3, 3), (3, 4), (3, 5), (4, 1), (4, 2), (4, 3), (4, 4), (4, 5), (5, 1), (5, 2), (5, 3), (5, 4), (5, 5)]
```




## Format

### ()``
* How to import?  

* Basic Usage
``` python

```

* Example
```python

```
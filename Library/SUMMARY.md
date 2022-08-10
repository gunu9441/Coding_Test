# Summary
## - Catalog
* collections  
(1) [deque](#1-deque)()  
(2) [Counter](#2-counter)(`list` or `string`)  
(3) [defaultdict](#3-defaultdict)(`data_type`)

* itertools  
(1) [combinations](#1-combinations)(`list` or `string`, `'뽑은 개수'`)    
(2) [combinations_with_replacement](#2-combinationswithreplacement)(`list` or `string`, `'뽑은 개수'`)    
(3) [permutations](#3-permutations)(`list` or `string`, `'뽑은 개수'`)  
(4) [product](#4-product)(`list` or `string`, repeat=`'뽑은 개수'`)

* re  
(1) [Meta character](#1-meta-character)  
(2) [search](#2-search)(`찾으려는 string`, `찾으려는 string을 갖고 있는 string`)  
(3) [findall](#3-findall)(`찾으려는 string`, `찾으려는 string을 갖고 있는 string`)  
(4) [match](#4-match)(`찾으려는 string`, `찾으려는 string을 갖고 있는 string`)

* sys  
(1) [setrecursionlimit](#1-setrecursionlimit)(`recursiondepthlimit`)

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

## -`re`
* How to import?  
`import re`  

### (1) Meta character  
#### 1.  `[ ]`: 문자 클래스  
* Description  
`[` 와 `]` 안에 있는 문자열이나 숫자를 찾아낸다.
```python
sentence = "I have a delicious pizza in the refrigerator."
extracted = re.search('[abc]', sentence)
print(extracted)
#<re.Match object; span=(3, 4), match='a'>
#a나 b나 c를 가지는 문자 하나만!! 가지고 오게 된다.

sentence = "I have a delicious pizza in the refrigerator."
extracted = re.findall('[abc]', sentence)
print(extracted)
return 
#['a', 'a', 'c', 'a', 'a']
#sentence 변수 안에 있는 문자열에서 a, b, c를 갖는 모든 문자를 문장안에 배열되어있는
#순서대로 가져온다.
```
* 문자 클래스 표기법  
1.`\d`: 모든 숫자와 매치(=`[0-9]`)  
2.`\D`: 숫자가 아닌 것과 매치(=`[^0-9]`)  
3.`\s`: whitespace 문자(tab, 개행 등등..)와 매치(=`[\t\n\r\f\v]`)  
4.`\S`: whitespace 문자가 아닌 것과 매치  
5.`\w`: 문자+숫자와 매치(=`[a-zA-Z0-9]`)  
6.`\W`: 문자+숫자가 아닌 것과 매치(=`^a-zA-Z0-9`)  
```python
sentence = "I have a delicious 9 pizza in the refrigerator?!.$"
# whitespace와 매치 되지 않는([^\s]) 모든 것(findall)을 골라라
extracted = re.findall('[^\s]', sentence) 
print(extracted)
#['I', 'h', 'a', 'v', 'e', 'a', 'd', 'e', 'l', 'i', 'c', 'i', 'o', 'u', 's', '9', 'p', 'i', 'z', 'z', 'a', 'i', 'n', 't', 'h', 'e', 'r', 'e', 'f', 'r', 'i', 'g', 'e', 'r', 'a', 't', 'o', 'r', '?', '!', '.', '$']
```
#### 2. `.` : Dot
* Description  
개행인 `\n`을 제외한 모든 하나의 문자와 매치되는 것을 의미한다.
```python
sentence = "I have a delicious 9 pizza in the refrigerator?!.$"
# a 바로 뒤 개행을 제외한 모든 하나의 문자와 매치(a.) 되는 모든 것(findall)을 골라라
extracted = re.findall('a.', sentence)
print(extracted)
#['av', 'a ', 'a ', 'at']

sentence = "I have a delicious 9 pizza in the refrigerator?!.$"
#a와 .을 갖는([a.]) 모든 문자(findall)를 골라라
extracted = re.findall('[a.]', sentence)
print(extracted)
#['a', 'a', 'a', 'a', '.']
```
#### 3. `*`  
* Description  
메타 문자 앞의 글자가 **0번 이상** 반복되는 모든 문자열과 매치된다.
```python
sentence = "nanaver ver naver jjver kaver never nver naaaver!"
#n(0번 이상 반복되는 a)aver 꼴을 모두 골라라
extracted = re.findall('na*ver', sentence)
print(extracted)
#['naver', 'naver', 'nver', 'naaaver']

sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver"
# n 또는 a가 0번 이상 반복되는([na]*) 꼴을 모두 골라라
# n이나 a가 0번 이상이므로 n뒤에 꼭 a가 와야하는 것이아니라 
# 순서에 상관없이 n이나 a가 연속적으로 반복된다면 그 꼴이 골라진다.
extracted = re.findall('[na]*', sentence)
print(extracted)
#['nana', '', '', '', '', '', '', '', '', 'na', '', '', '', '', '', '', '', '', '', '', '', 'a', '', '', '', '', 'n', '', '', '', '', '', 'n', '', '', '', '', 'naaa', '', '', '', '', '', 'an', '', '', '', '', 'annnn', '', '', '', '', 'aaannnn', '', '', '', '']

sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
#n이나 a가 0번 이상 반복되면서 뒤에 ver로 종료되는 꼴을 모두 골라라
extracted = re.findall('[na]*ver', sentence)
print(extracted)
#['nanaver', 'ver', 'naver', 'ver', 'aver', 'ver', 'nver', 'naaaver', 'anver', 'annnnver', 'aaannnnver']
```

#### 4. `+`
* Description  
`+` 앞의 글자가 1번이상 반복되는 모든 문자열과 매치된다.
```python
sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
#n이나 a가 적어도 한번 이상 반복되며 ver로 종료되는 꼴을 모두 골라라
extracted = re.findall('[na]+ver', sentence)
print(extracted)
#['nanaver', 'naver', 'aver', 'nver', 'naaaver', 'anver', 'annnnver', 'aaannnnver']
```

#### 5. `{m, n}`
* Description  
앞의 문자가 `m`번 이상 `n`번 이하로 반복되는 모든 문자열과 매치된다.
```python
sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
# n이나 a가 1번 이상 3번 이하로 반복되면서 ver로 종료되는 꼴을 골라라.
extracted = re.findall('[na]{1,3}ver', sentence)
print(extracted)
#['anaver', 'naver', 'aver', 'nver', 'aaaver', 'anver', 'nnnver', 'nnnver']
# a와 n의 반복 횟수를 합쳐서 계산한다.
#'anaver'의 경우 nanaver에서 n과 a의 반복 횟수가 합쳐서 1이상 3이하가 되야하므로
# 맨 앞의 n이 포함되지 않고 anaver만 골라서 반복 횟수를 3으로 맞춰준 상태로
# 골라졌다.
```

### (2) `search`
* Description  
찾아려는 문자열을 하나만 찾아준다.  
()과 .group을 사용하여 원하는 문자열을 뽑아낼 수도 있다.
* Basic Usage
``` python
 for page in pages:
        print(re.search('<meta property="og:url" content="[\S]+/>', page))
    return 
```

* Example
```python
 for page in pages:
        print(re.search('<meta property="og:url" content="[\S]+"/>', page)) 
#	<re.Match object; span=(102, 151), match='<meta property="og:url" content="https://a.com"/>>
#<re.Match object; span=(102, 151), match='<meta property="og:url" content="https://b.com"/>>
#<re.Match object; span=(102, 151), match='<meta property="og:url" content="https://c.com"/>>

for page in pages:
        sentence = re.search(' <meta property="og:url" content="(\S+)"/>', page)
        print(sentence)
#<re.Match object; span=(101, 151), match=' <meta property="og:url" content="https://a.com"/>
#<re.Match object; span=(101, 151), match=' <meta property="og:url" content="https://b.com"/>
#<re.Match object; span=(101, 151), match=' <meta property="og:url" content="https://c.com"/>
#()는 group해주는 함수로 group(1)을 하면 첫번쨰에 존재하는 group이 나오게 된다.

for page in pages:
        sentence = re.search(' <meta property="og:url" content="(\S+)"/>', page).group(1)
        print(sentence)
#https://a.com
#https://b.com
#https://c.com
#()는 group해주는 함수 이므로 .group(1)을 써서 ()자리에 어떤 문자열이 존재했는지 가져올 수 있다.
```
### (3) `findall`
* Description  
찾으려는 문자열과 mapping되는 모든 문자열을 찾아 **list형태**로 반환한다.
* Basic Usage
``` python
 for f in re.findall(r'[a-zA-Z]+', page.lower()):
            if f == word.lower():
                word_count += 1
```

* Example
```python
pages = ["<html lang=\"ko\" xml:lang=\"ko\" xmlns=\"http://www.w3.org/1999/xhtml\">\n<head>\n  <meta charset=\"utf-8\">\n  <meta property=\"og:url\" content=\"https://a.com\"/>\n</head>  \n<body>\nBlind Lorem Blind ipsum dolor Blind test sit amet, consectetur adipiscing elit. \n<a href=\"https://b.com\"> Link to b </a>\n</body>\n</html>", "<html lang=\"ko\" xml:lang=\"ko\" xmlns=\"http://www.w3.org/1999/xhtml\">\n<head>\n  <meta charset=\"utf-8\">\n  <meta property=\"og:url\" content=\"https://b.com\"/>\n</head>  \n<body>\nSuspendisse potenti. Vivamus venenatis tellus non turpis bibendum, \n<a href=\"https://a.com\"> Link to a </a>\nblind sed congue urna varius. Suspendisse feugiat nisl ligula, quis malesuada felis hendrerit ut.\n<a href=\"https://c.com\"> Link to c </a>\n</body>\n</html>", "<html lang=\"ko\" xml:lang=\"ko\" xmlns=\"http://www.w3.org/1999/xhtml\">\n<head>\n  <meta charset=\"utf-8\">\n  <meta property=\"og:url\" content=\"https://c.com\"/>\n</head>  \n<body>\nUt condimentum urna at felis sodales rutrum. Sed dapibus cursus diam, non interdum nulla tempor nec. Phasellus rutrum enim at orci consectetu blind\n<a href=\"https://a.com\"> Link to a </a>\n</body>\n</html>"]
for page in pages:
    page = page.lower()
    count = 0
    print('찾아야할 word:',word)
    # 모든 소문자 알파벳이 1번이상 반복되는 것과 매칭되는 문자열을 모두 찾아 list형태로 반환
    for i in re.findall('[a-z]+', page):
        print('가져온 word:',i)
        if i == word:
            count += 1
    print('count:', count)
    """
    찾아야할 word: blind
    가져온 word: html
    가져온 word: lang
    가져온 word: ko
    가져온 word: xml
    가져온 word: lang
    가져온 word: ko
    가져온 word: xmlns
    가져온 word: http
    ...
    count: 3
    ...
    count:1
    ...
    count:1
    """

    link = re.findall('<a href="(\S+)">', page)
    print(link)
    """
    ['https://b.com']
    ['https://a.com', 'https://c.com']
    ['https://a.com']
    """
    link = re.findall('<a href="[\S]+">', page)
    print(link)

    """
    ['<a href="https://b.com">']
    ['<a href="https://a.com">', '<a href="https://c.com">']
    ['<a href="https://a.com">']
"""
```

### (4) `match`
* Description  
반드시 처음부터 찾으려는 문자열과 mapping되는 문자열을 하나만 찾아준다.
* Basic Usage
``` python
sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
#처음부터 n이나 a를 갖고 ver로 종료되는 꼴([na]ver)을 하나만(match) 골라라
extracted = re.match('[na]ver', sentence)
print(extracted)
#None
#처음부터 검사하는데 처음부터 틀렸으므로 None을 반환한다.

sentence = "nanaver ver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
# 처음부터 n이나 a가 반복되고 ver로 종료되는 꼴([na]*ver)을 하나만(match) 골라라
extracted = re.match('[na]*ver', sentence)
print(extracted)
#<re.Match object; span=(0, 7), match='nanaver'>

sentence = "naanaverver naver jjver kaver never nver naaaver! anver annnnver aaannnnver aannve aaaannnnvr"
# 처음부터 n이나 a가 반복되고 ver로 종료되는 꼴([na]*ver)을 하나만(match) 골라라
extracted = re.match('[na]*ver', sentence)
print(extracted)
# <re.Match object; span=(0, 8), match='naanaver'>
```

## sys

### (1) `setrecursionlimit`
* Description  
재귀를 사용할 때, depth의 limit을 설정한다.  
보통 인자로 `10**6`을 사용한다.

* Basic Usage
``` python
import sys
sys.setrecursionlimit(10**6)
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

## Reference
* re library  
    - meta character 정리: https://doorbw.tistory.com/127  
    - 문자열 처리 소개(find(), count(), replace, strip(), upper(), lower() 등등): https://buyandpray.tistory.com/48
    - 정규 표현식 정리 1: https://whatisthenext.tistory.com/116
    - 정규 표현식 정리 2: https://buyandpray.tistory.com/49
    - 프로그래머스-매칭-점수-solution: https://velog.io/@ckstn0778/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-42893%EB%B2%88-%EB%A7%A4%EC%B9%AD-%EC%A0%90%EC%88%98-X-1-Python

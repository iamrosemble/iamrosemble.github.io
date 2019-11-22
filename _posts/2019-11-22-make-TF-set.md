---
layout: post
title:  "itertools.product를 활용한 True False 셋 조합 만들기"
author: rosemble
categories: [ python ]
featured: true
hidden: false
tag: python, itertools
---
## 리스트 요소를 조합하여 여러 세트로 만들고 싶을 때 사용한 트릭


```python
# TF 조합을 요소 수만큼 만들기
from itertools import *
for x in list(product([True,False],repeat=len(facs))):
    print(x)
```
```
(True, True, True)
(True, True, False)
(True, False, True)
(True, False, False)
(False, True, True)
(False, True, False)
(False, False, True)
(False, False, False)
```

```python
# 응용
from itertools import *

facs = ['one','two','three']

l1 = []
l2 = []

for pattern in product([True,False],repeat=len(facs)):
    l1.append([x[1] for x in zip(pattern,facs) if x[0]])
    l2.append([x[1] for x in zip(pattern,facs) if not x[0]])

for i in range(len(l1)):
    print(l1[i],'------', l2[i])
```
```
['one', 'two', 'three'] ------ []
['one', 'two'] ------ ['three']
['one', 'three'] ------ ['two']
['one'] ------ ['two', 'three']
['two', 'three'] ------ ['one']
['two'] ------ ['one', 'three']
['three'] ------ ['one', 'two']
[] ------ ['one', 'two', 'three']
```

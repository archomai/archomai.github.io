---
layout: post
title:  "Python Basic"
date:   2018-01-18
desc: "Python Basic"
keywords: "python"
categories: [Python]
tags: [python]
icon: icon-python
---

## variable and object

* object (객체) : 정수, 문자열, 함수 등 파이썬에서 쓰이는 모든것

 - integer (정수) : 1, 2, 3, 4, 5
 - float (소수) : 1.0, 2.5, 3.14
 - string (문자열) : a, b, c, abc, 가나다
 - function (함수)

* variable (변수)

```
var1 = 100
```

> var1 변수에 정수 100을 할당

---

## ID

```
>> id(var1)
4520513920
```

> 메모리 상 고유의 주소를 출력하는 내장함수

---

## Type

```
>> type(var1)
'int'
```

> variable의 형태를 알려 주는 내장함수

---

## Input

```
>> var = input('how old are you? : ')
(20)
>> print(var)
20
```

> 사용자의 정보 입력을 요구하는 내장함수

---
layout: post
title:  "Python Function"
date:   2018-01-19
desc: "Python Function"
keywords: "python"
categories: [Python]
tags: [python]
icon: icon-python
---

## Fucntion 함수

> 반복적 작업을 하는 코드를 재사용이 가능하게 정의해 놓은것

```
def 'name of function'(parameters):
	action
```
```
def school(name):
	return name

>> school('cho')
cho
```

- function : 'function' object(객체)를 참조하는 variable(변수)
 - 즉, function 자체가 하나의 변수
- name = parameter(매개변수)
- 'cho' = argument(인자


## 리턴값이 없는 함수

```
def school():
	print('school')
```

> return 값 없이
> 실행문이 print일 경우 아무 값도 가지고 있지


```
>> school
<function __main__.school>

>> school()
hi

>> a = school()
>> print(a)
None
```
> return이 없는 school()은 variable 임으로 값이 없음
>
> school()이 값을 가지고 있지 않음으로 None 으로 출력
>
> print는 지정된 object를 단순히 보여주는 역할 (줄바꿈 등 기능)

## 리턴값이 있는 함수

```
def return_true():
	return True

>> return_true()
True
```

## 기본 parameter 값의 정의 시점

```
def return_list(value, result=[]):
   result.append(value)
   return result

>> return_list('apple')
['apple']
>> return_list('banana')
['apple', 'banana']
```

> 함수가 '정의'되는 시점에 계산

```
def return_list(value, result=None):
   if result is None:
     result = []
   result.append(value)
   return result

>> return_list('apple')
['apple']
>> return_list('banana')
['banana']
```

> 함수가 '실행'되는 시점에 계산

## Function as argument

```
def f1():
	print('call func')

def f2(func)
	print('I am number 2')
	func()

>> f2(f1)
I am number 2
call func
```

## Function in function

```
def f1(st):
    def inner_function(s):
        return s.upper()

    return inner_function(st)

>> f1(word)
WORD
```

> 내부 함수(f2)의 경우 f1함수의 return 전에 정의 되어야 한다

## Scope (영역)

```
champion = 'Lux'

def show_global_champion():
    print('show_global_champion : {}'.format(champion))

def change_global_champion():
    champion = 'Ahri'
    print('change_global_champion : {}'.format(champion))

>> show_global_champion()
>> change_global_champion()

show_global_champion : Lux
change_global_champion : Ahri
```

* show_global_champion() 의 경우 전역변수를 사용

* change_global_champion() 의 경우 지역변수를 사용


## Built-in Functions

```
dir(__builin__)
```

- 내부 함수를 볼수 있음

> 작업 창은 전역 영역 (Global scope)에 위치
>
> 내부 함수와 같은 이름으로 변수를 지정할 경우
>
> 지역 영역(local scope)에 있는 내부 함수가 덮어쓰기가 된다

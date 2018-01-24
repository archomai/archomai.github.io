---
layout: post
title:  "Python Module"
date:   2018-01-18
desc: "Python Module"
keywords: "python"
categories: [Python]
tags: [python]
icon: icon-python
---

## Module 모듈

* 문자열 줄 바꿔 쓰기 간단 표현

```
SELECTION = '''1. play game
2. buy item
3. exit'''

>> print(SELECTION)
1. play game
2. buy item
3. exit
```
---

## import module

```
import game

if SELECTION == 1:
	game.play_game()
```

---

## from ... import

```
from game import play.game()

if SELECTION == 1:
	play_game()
```

> 'game' 을 생략해 줄 수 있다

---

## from ... import *


* import * 을 사용할 경유 모든 기능을 불러온다

* 해당 모듈에서 선택적으로 사용하고 싶을때는 모듈에서 아래와 같이 입력

```
__all__ (
	'game.py',
)
```
----

## Folder Package

* 파이썬3 에서 부터는 폴더도 하나의 패키지로 취급

* 파이썬2 에서는 폴더 내부에 아래와 같은 파일이 있어야함


```
__init__.py
```

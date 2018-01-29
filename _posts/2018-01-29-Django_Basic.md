---
layout: post
title:  "Django Basic"
date:   2018-01-29
desc: "Django Basic"
keywords: "django"
categories: [Django]
tags: [django]
icon: icon-django
---

# Django 장고

> 웹어플리케이션을 만들기 위한 프레임워크
>
> 애플리케이션 : 누군가 쓸수 있는 모든 프로그램

- Python framework 종류 : Django(시장대세) / flask

---

## 프레임워크란

> 자주사용하는 블럭의 모음 (클래스와 라이브러리의 모임)

* 프레임워크 > 패키지 >= 라이브러리 > 모듈(파일한개)

----

## 웹프레임 워크 빠른 순서

<위에서 부터 빠른 순서>

spring(java) : 빠름 (장점 java 사용자가 많음 / 단점 java 언어가 어려움)

node.js (javascript) : 백엔드

express (쌩 javascript) : 장고와 같은 역활

Django (python)

rails (Ruby) : 개발자간 코드 구성이 너무 달라 협업에 어려움



------

## 프레임워크 시장 현황

<위에서 부터 많이 사용하는 순서>

sprint/php : 일자리는 많으나 일자리의 질이 떨어짐

* 쌩 php x / lalarvel 괜찮음

node.js : 사실 대세 (javascript를 사용하는 프론트 언어의 영향)

django

rails

------

## 프론트 엔드 프로그램

프론트에서 javascript가 대세

- angular2 / es6 문법: react vuejs

개발 언어 역사

- %^&%^& -> angular1.x -> react - > react / angular2 / vuejs

react 추천 (많은 업체가 이미 사용중)

새로 시작하기는 vueJS

---

## 웹서버

브라우저 http요청 -> dns -> ip -> request -> 서버컴퓨터에 도착

-> 서버컴퓨터의 웹 서버 프로그램이 해당 요청을 받음

-> 웹 서버 프로그램은 웹 어플리케이션에 요청에 대한 응답의 제작을 요청

-> 웹 어플리케이션은 요청에 대한 응답을 동적으로 생성해서 웹 서버에게 돌려줌

-> 웹 서버는 자신이 요청하고 받은 응답을 다시 사용자에게 전송

-> 브라우저에서 해당 결과를 봄


즉, 요청을 받고 응답을 줄수 프로그램. 응답을 보낼수는 있지만 응답을 만들 수는 없다.

---

## Django 시작하기

```
>> django-admin startproject mysite
```

> 'mysite' 이름의 프로젝트 시작


```
~/projects/django/djangogirls_tutorial master
fc-djangogirls ❯ django-admin startproject mysite

drwxr-xr-x   4 archomai  staff   128B Jan 29 14:20 mysite
```

> mysite/mysite (외부 폴더는 프러젝트 폴더 이름 / 내부 폴더는 패키지 이름)

- 외부 폴더는 django로 이름 변경 (체크 2개 해제)

- 내부 폴더 config로 이름 변경 (2개 체크)
 - 별도의 창 활성화 (do refactor 클릭)

---

## 소스루트 지정

> python django 에서는 폴더는 패키지로 취급 (장고에서는 패키지를 애플리케이션이라 함)

- django 폴더를 소스루트로 지정 (패키지 취급이 안되게)
 - (원래는 최상위 폴더가 소스루트로 지정)

- django 폴더 우클릭 - mark directory as 'sources root'

---
## Setting 기본 설정

> setting.py 에서 아래와 같이 변경

```
LANGUAGE_CODE = 'ko-ko'

TIME_ZONE = 'Asia/Seoul'
```

----

## 로컬 장고 열기

> 로컬 http://localhost:8000/ 에서 장고를 열기 위한 명령어

```
~/projects/django/djangogirls_tutorial/django master*
fc-djangogirls ❯ python manage.py runserver
```

----

## 패키지 버젼 저장 하기

```
~/projects/django/djangogirls_tutorial master*
fc-djangogirls ❯ pip list


~/projects/django/djangogirls_tutorial master*
fc-djangogirls ❯ pip freeze


~/projects/django/djangogirls_tutorial master*
fc-djangogirls ❯ pip freeze > requirements.txt
```

> requirement.txt 에 현재 버전 내용 저장

----

## 블로그 만들기

```
~/projects/django/djangogirls_tutorial/django master
fc-djangogirls ❯ python manage.py startapp blog
```

> django 하위 폴더에 'blog' 폴더 생성

---

## Model.py

```
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey(
        'auth.User',
        on_delete=models.CASCADE,
    )

    title = models.CharField(max_length=200)
    content = models.TextField(blank=True)
    created_data = models.DateTimeField(
        default=timezone.now
    )
    published_data = models.DateTimeField(
        blank=True, null=True
    )

    def publish(self):
        self.published_data = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```


- class Post(models.Model):
 - models.Model : 상속 (데이터 베이스의 형태를 결정 )

- ForeignKey('auth.User') : 연결 기능
 - auth 모듈 / user 클래스

- CharField(max_length=200)
 - 캐릭터 최대길이 제한

- TextField(blank=True)
 - 캐릭터 제한 없음

```
on_delete=models.CASCADE,
```

- 연결된 auth.User 의 정보가 날라갈 경우 같이 삭제 될수 있도록

```
 def publish(self):
        self.published_data = timezone.now()
        self.save()
```

 - 객체를 저장하고 나서 / 서버에 저장하기 때문에 save() 함수 사용
  - 클래스 객체 저장과 서버저장은 다르기 때문에

----

## migrate

 > 데이터 베이스에 테이블 구조를 적용 하는 명령어

```
 ~/projects/django/djangogirls_tutorial/django master
fc-djangogirls ❯ python manage.py migrate  
```

```
-rw-r--r--  1 archomai  staff   128K Jan 29 15:51 db.sqlite3
```

> db.sqlite3 자동으로 생성 (디폴트로 로그인 관련 폴더 생성)


----

## settings.py 'blog' 추가

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'blog',
]
```


---

공동작업시 클래스 변경되면 데이터 베이스 설정을 바꿔주도록 실행
```
~/projects/django/djangogirls_tutorial/django master*
fc-djangogirls ❯ python manage.py makemigrations
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Post
```

----

## SQLECTRON

> sqlectron download

https://github.com/sqlectron/sqlectron-gui/releases/tag/v1.29.0

Sqlectron-1.29.0.dmg

mac에서 실행시 파일 폴더에서 실행

---

~/projects/django/djangogirls_tutorial/django master*
fc-djangogirls ❯ python manage.py makemigrations
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Post


- sqlectron

 - add -> sqllie -> 위치 : 폴더 내 db.sqlite3
 - connect

----

## Admin 계정 생성

```
~/projects/django/djangogirls_tutorial/django master*
fc-djangogirls ❯ python manage.py createsuperuser
```

```
Username (leave blank to use 'archomai'): ri
Email address:
Password:
Password (again):
Superuser created successfully.
```

> 이메일 필요없음 / 비번 입력 (r!)

접속주소 : http://localhost:8000/admin

----

## POST 만들기

http://localhost:8000/admin

포스트 작성 후 sqlectron 에서 확인

> blog_post 폴더
> 우클릭 - select raws

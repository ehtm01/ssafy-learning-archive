# Template System

## Django Template System
- **파이썬 데이터(context)를 HTML 문서(Template)와 결합**하여, **로직과 표현을 분리**한 채 동적인 웹페이지를 생성하는 도구

### HTML의 콘텐츠를 변수 값에 따라 변경하기
- 빨간 상자의 내용이 변수에 따라 바뀌게 해보자

```html
<!-- articles/index.html -->

<body>
  <h1>Hello, Django!</h1>
</body>
```

![0919_Template&URLs_2025-09-19-09-03-07](images/0919_Template&URLs_2025-09-19-09-03-07.png)

- 빨간 상자의 내용이 변수에 따라 바뀌게 해보자
    - context['name']이 변경되면 응답 받은 HTML의 모습도 변경되는 걸 확인하자

```py
# views.py

def index(request):
    context = {
        'name': 'Jane',
    }
    return render(request, 'article/index.html', context)
```

```html
<!-- articles/index.html -->

<body>
  <h1>Hello, {{ name }}!</h1>
</body>
```

![0919_Template&URLs_2025-09-19-09-05-31](images/0919_Template&URLs_2025-09-19-09-05-31.png)

### Django Template system의 목적
- <b>'페이지 틀'에 '데이터'를 동적으로 결합</b>하여 수 많은 페이지를 효율적으로 만들어내기 위함

## Django Template Language(DTL)
- Template에서 조건, 반복, 변수 등의 프로그래밍적 기능을 제공하는 시스템

### DTL Syntax
1. Variable
2. Filters
3. Tags
4. Comments

### 1. Variable
- Django Template에서의 변수
- render 함수의 세 번째 인자로 딕셔너리 타입으로 전달됨
- 해당 딕셔너리 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨
- dot('.')을 사용하여 변수 속성에 접근할 수 있음

`{{ variable }}`

`{{ variable.attribute }}`

```py
context = {
    'variable_1': 'value_1',    # {{ varialbe_1 }}
    'variable_2': {
        'attribute': 'value_2', # {{ variable_2.attribute }}
    },
}
```

### 2. Filters
- 표시할 변수를 수정할 때 사용 (변수 + '|' + 필터)
- chained(연결)이 가능하며 일부 필터는 인자를 받기도 함
- 약 60개의 built-in template filters를 제공

`{{ variable|filter }}`

`{{ name|truncatewords:30 }}`

### 3. Tags
- 반복 또는 논리를 수행하여 제어 흐름을 만듦
- 일부 태그는 시작과 종료 태그가 필요
- 약 24개의 built-in template tags를 제공

`{% tag %}`

`{% if %} {% endif %}`

- if, else, endif 태그
```py
context = {
    'login': False,
}
```
```django
{% if login %}
    <h1>Hello, User!!!</h1>
{% else %}
    <h1>Please, login.</h1>
{% endif %}
```
```django
<h1>Please, login.</h1>
```
---
```py
context = {
    'nums': [1, 2, 3],
}
```
```django
<ul>
    {% for num in nums %}
        <li>{{ num }}</li>
    {% endfor %}
</ul>
```
```django
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```

### 4. Comments
- 주석
    - inline<br>
    ```django
    <h1>Hello, {# name #}</hi>
    ```
    - multiline<br>
    ```django
    {% comment %}
        ...
    {% endcomment %}
    ```

### DTL 예시
- 다음과 같은 화면을 DTL을 활용해 구성해 보자

    ![0919_Template&URLs_2025-09-19-09-26-03](images/0919_Template&URLs_2025-09-19-09-26-03.png)

    ```py
    # urls.py

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('articles/', views.index),
        path('dinner/', views.dinner),
    ]
    ```
    ```py
    # views.py

    import random

    def dinner(request):
        foods = ['국밥', '국수', '카레', '탕수육']
        picked = random.choice(foods)
        context = {
            'foods': foods,
            'picked': picked,
        }
        return render(request, 'articles/dinner.html', context)
    ```
    ```django
    <!-- articles/dinner.html -->
    <p>{{ picked }} 메뉴는 {{ picked|length }}글자 입니다.</p>

    <h2>메뉴판</h2>
    <ul>
        {% for food in foods %}
            <li>{{ food }}</li>
        {% endfor %}
    </ul>

    {% if foods|length == 0 %}
        <p>메뉴가 소진 되었습니다.</p>
    {% else %}
        <p>아직 메뉴가 남았습니다.</p>
    {% endif %}
    ```

# 템플릿 상속

### 기본 템플릿 구조의 한계
- 만약 모든 템플릿에 Bootstrap을 적용하려면?

> 모든 템플릿에 Bootstrap CDN을 작성해야 할까?

### 템플릿 상속(Template inheritance)
1. 페이지의 **공통요소를 포함**
2. 하위 템플릿이 **재정의할 수 있는 공간**을 정의

> 여러 템플릿이 **공통요소를 공유할 수 있게** 해주는 기능

### 상속 구조 만들기
- skeleton 역할을 하게 되는 상위 템플릿(base.html) 작성
    - 모든 템플릿이 공유했으면 좋겠는 공통요소 작성
    - 템플릿 별로 재정의할 부분은 bloce 태그 활용
    
    ```django
    <!-- articles/base.html -->
    <!DOCTYPE html>
    <html lang="en">    
    <head>
        ...
        {% comment %} 생략 {% endcomment %}
    </head>
    <body>
        {% block content %}
        {% endblock content %}
        {% comment %} 생략 {% endcomment %}
    </body>
    </html>
    ```
    - 파일명이 반드시 base일 필요는 없음

- 기존 하위 템플릿들이 상위 템플릿을 상속받도록 변경
    - extends 태그로 상속받을 템플릿 결정
    - block 태그를 활용해 base.html의 같은 이름으로 작성된 block 태그의 내용을 대체

    ```django
    {% extends 'articles/base.html' %}
  
    {% block content %}
      <h1>Hello, {{ name }}</h1>
    {% endblock content %}
    ```

    ```django
    {% extends 'articles/base.html' %}

    {% block content %}
      <p>{{ picked }} 메뉴는 {{ picked|length }}글자 입니다.</p>

      <h2>메뉴판</h2>
      <ul>
        {% for food in foods %}
        <li>{{ food }}</li>
        {% endfor %}
      </ul>

      {% if foods|length == 0 %}
        <p>메뉴가 소진 되었습니다.</p>
      {% else %}
        <p>아직 메뉴가 남았습니다.</p>
      {% endif %}
    {% endblock content %}
    ```

- 최종 형태

    ![0919_Template&URLs_2025-09-19-11-45-04](images/0919_Template&URLs_2025-09-19-11-45-04.png)

## 상속 관련 DTL 태그

### 'extends' tag

```django
{% extends 'articles/base.html' %}
```

- 자식(하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
- 반드시 자식 템플릿 최상단에 작성되어야 함
    - extends 태그는 2개 이상 사용 불가

### 'block' tag

```django
{% block 'content' %} {% endblock 'content' %}
```

- 하위 템플릿에서 재정의할 수 있는 블록을 정의
- 상위 템플릿에서 작성하며 하위 템플릿이 작성할 수 있는 공간을 지정하는 것

### 다시 살펴보기
- 하위 템플릿의 block이 상위 템플릿의 block의 내용을 대체하게 됨

    ![0919_Template&URLs_2025-09-19-11-45-32](images/0919_Template&URLs_2025-09-19-11-45-32.png)

# 요청과 응답

## HTML form

### 데이터를 보내고 가져오기(Sending and Retrieving form data)
- HTML **'form'** element를 통해 사용자와 애플리케이션 간의 상호작용 이해하기

### HTML form
- HTTP 요청을 서버에 보내는 가장 편리한 방법

    ![0919_Template&URLs_2025-09-19-10-07-09](images/0919_Template&URLs_2025-09-19-10-07-09.png)

    - 클라이언트 서버 구조: 인터넷에 연결된 서로 다른 두 컴퓨터가 데이터를 주고받는 웹의 동작방식 중 하나
---
- HTTP 요청을 서버에 보내는 가장 편리한 방법

    ![0919_Template&URLs_2025-09-19-10-08-35](images/0919_Template&URLs_2025-09-19-10-08-35.png)

### 실제 웹 서비스에서 form이 사용되는 예시
- 네이버 & 구글의 로그인 화면에서 사용하는 HTML form 요소

    ![0919_Template&URLs_2025-09-19-11-48-12](images/0919_Template&URLs_2025-09-19-11-48-12.png)

### 'form' element
- 사용자로부터 할당된 데이터를 서버로 전송하는 HTML 요소

- 웹에서 사용자 정보를 입력하는 여러 방식<br>
(text, password, checkbox 등)을 제공

### form을 이용해 Naver로 요청 보내기: "fake Naver"

![0919_Template&URLs_2025-09-19-11-48-40](images/0919_Template&URLs_2025-09-19-11-48-40.png)

- 검색어를 입력하면,

![0919_Template&URLs_2025-09-19-11-48-51](images/0919_Template&URLs_2025-09-19-11-48-51.png)

- 네이버로 검색이 되도록

### fake Naver 실습
- form을 이용해 Naver에 요청을 보내보자.
    - form 요소로 검색창을 만들기

    ```py
    # urls.py

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('articles/', views.index),
        path('dinner/', views.dinner),
        path('search/', views.search),
    ]
    ```
    ```py
    # views.py

    def search(request):
        return render(request, 'articles/search.html')
    ```
    ```django
    <!-- articles/search.html -->

    {% extends "articles/base.html" %}

    {% block content %}
      <form action="#" method="GET">
        <label for="message">검색어</label>
        <input type="text" name="query" id="message">
        <input type="submit" value="submit">
      </form>
    {% endblock content %}
    ```

    - input에 hello를 입력하고 제출 버튼을 누른 뒤 브라우저 URL 확인

    ![0919_Template&URLs_2025-09-19-11-54-57](images/0919_Template&URLs_2025-09-19-11-54-57.png)
    
    ---
    - 실제 Naver에서 검색 후 URL 확인

    ![0919_Template&URLs_2025-09-19-10-19-21](images/0919_Template&URLs_2025-09-19-10-19-21.png)    

    - action의 URL 변경 후 테스트

    ```django
    {% extends "articles/base.html" %}

    {% block content %}
      <form action="https://search.naver.com/search.naver" method="GET">
        <label for="message">검색어</label>
        <input type="text" name="query" id="message">
        <input type="submit" value="submit">
      </form>
    {% endblock content %}
    ```

## HTML form 핵심 속성

### action & method 란
- form의 핵심 속성 2가지
- 데이터를 어디(**action**)로 어떤 방식(**method**)으로 요청할지

### action & method 예시

```django
<form action="https://search.naver.com/search.naver" method="GET">
  <label for="message">검색어</label>
  <input type="text" name="query" id="message">
  <input type="submit" value="submit">
</form>
```

- action
    - 입력 데이터가 전송될 URL을 지정(목적지)
        - action을 지정하지 않으면 데이터는 현재 페이지의 URL로 설정됨
- method
    - 데이터를 어떤 방식으로 보낼 것인지 정의
    - 데이터의 HTTP request method(GET, POST)를 지정

### 'input' element
- 사용자의 데이터를 입력받을 수 있는 HTML 요소
- type 속성 값에 따라 다양한 유형의 입력 데이터를 받음

> 핵심 속성: '**name**'

### 'name' attribute

```django
<input type="text" name="query" id="message">
```

- input 요소의 핵심 속성
- 사용자가 입력한 데이터에 붙이는 이름(key)
- 데이터를 제출했을 때 서버는 name 속성에 설정된 값을 통해서만 사용자가 입력한 데이터에 접근할 수 있음

### Query String Parameters
- 사용자의 입력 데이터를 URL 주소에 파라미터를 통해 서버로 보내는 방법
- 문자열은 앰퍼샌드('&')로 연결된 key=value 쌍으로 구성되며, 기본 URL과는 물음표('?')로 구분됨
- 예시
    - http://host:port/path?key=value&key=value

## HTML form 활용

### 용자 입력 데이터를 받아 그대로 출력하는 서버 만들기
- view 함수는 몇 개가 필요할까?

    ![0919_Template&URLs_2025-09-19-10-25-31](images/0919_Template&URLs_2025-09-19-10-25-31.png)

### 1. throw 로직 작성
- fake Naver를 참고하여 작성해보기

```py
# urls.py

urlpatterns = [
    path('throw/', views.throw),
]
```

```py
# viwes.py

def throw(request):
    return render(request, 'articles/throw.html')
```

```django
<!-- articles/throw.html -->

{% extends "article/base.html" %}

{% block content %}
  <h1>Throw</h1>
  <form action="/catch/" method="GET">
    <input type="text" id="message" name="message">
    <input type="submit">
  </form>
{% endblock content %}
```

### 2. catch 로직 작성
- throw 페이지에서 요청한 사용자 입력 데이터는 어떻게 가져와야 할까?

```py
# urls.py

urlpatterns = [
    path('catch/', views.catch),
]
```

```py
# viwes.py

def throw(request):
    context = ???
    return render(request, 'articles/catch.html')
```

```django
<!-- articles/throw.html -->

{% extends "article/base.html" %}

{% block content %}
  <h1>Catch</h1>
  <h3>{{ ??? }}를 받았습니다!</h3>
{% endblock content %}
```

### request 객체
- HTTP request 객체: form으로 전송한 데이터 뿐만 아니라 Django로 들어오는 모든 요청 관련 데이터가 담겨 있음.<br>(view 함수가 호출될 때 첫 번째 인자로 전달됨)

### request 객체 살펴보기
- view 함수의 request 매개변수의 여러가지 정보를 확인해보자.

    ```py
    def catch(request):
        print(request)
        print(type(request))
        print(dir(request))
        print(request.GET)
        print(request.GET.get('message'))
        return render(request, 'articles/catch.html')
    ```

    ![0919_Template&URLs_2025-09-19-10-36-56](images/0919_Template&URLs_2025-09-19-10-36-56.png)

### request 객체에서 form 데이터 추출
- request.GET에 작성한 message가 담겨있음을 확인할 수 있다.

    ![0919_Template&URLs_2025-09-19-10-37-35](images/0919_Template&URLs_2025-09-19-10-37-35.png)

### 3. catch 로직 마무리
- throw 페이지에서 요청한 사용자 입력 데이터는 어떻게 가져와야 할까?

    ```py
    # views.py

    def catch(request):
        message = request.GET.get('message')
        context = {
            'message': message,
        }
        return render(request, 'articles/catch.html', context)
    ```

    ```django
    <!-- articles/catch.html -->

    {% extends 'article/base.html' %}

    {% block content %}
    <h1>Catch</h1>
    <h3>{{ message }}를 받았습니다!</h3>
    {% endblock %}
    ```

### throw - catch 간 요청과 응답 정리
- 브라우저에 http://127.0.0.1:8000/throw/ 를 입력하면 발생하는 일

    ![0919_Template&URLs_2025-09-19-10-41-19](images/0919_Template&URLs_2025-09-19-10-41-19.png)

- throw 페이지에서 일어나는 일

    ![0919_Template&URLs_2025-09-19-10-41-33](images/0919_Template&URLs_2025-09-19-10-41-33.png)

# Django URLs

### 요청과 응답에서 Django URLs의 역할
- 요청 URL에 따라 실행될 view 함수가 달라진다.

    ![0919_Template&URLs_2025-09-19-10-42-03](images/0919_Template&URLs_2025-09-19-10-42-03.png)

### URL dispatcher(운항 관리자, 분배기)
- URL 패턴을 정의하고 해당 패턴이 일치하는 요청을 처리할 view 함수를 연결(매핑)

## Variable Routing

### 현재 URL 관리의 문제점
- 템플릿의 많은 부분이 중복되고, URL의 일부만 변경되는 상황이라면?
    - 계속해서 비슷한 URL과 템플릿을 작성해야 할까?

    ```py
    urlpatterns = [
        path('articles/1/', ...),
        path('articles/2/', ...),
        path('articles/3/', ...),
        path('articles/4/', ...),
        path('articles/5/', ...),
        ...,
    ]
    ```

### Variable Routing
- URL 일부에 변수를 포함시키는 것
    - 변수는 view 함수의 인자로 전달할 수 있음

```django
<path_converter:variable_name>
```

```py
urlpatterns = [
    path('articles/<int:num>/', ...),
]
```

---

```django
<path_converter:variable_name>
```

```py
path('articles/<int:num>/', views.detail)
path('articles/<str:name>/', views.greeting)
```

- 요청 URL의 <int:num>, <str:name>의 위치에 들어있는 값이 변수처럼 취급됨
    - 정수 num 변수가 views.detail에, 문자열 name 변수가 views.greeting에 <u>키워드 인자</u>로 전달됨
    - 예) 요청 URL이 /articles/**10**/ 이면, views.detail(request, **num=10**)의 형태로 호출
- Path Converter
    - URL 변수의 타입을 지정
    - str, int 등 5가지 타입 지원

---
- 키워드 인자: 함수 호출 시 인자의 순서를 무시하고 특정 매개변수에 값을 할당하는 인자

### Variable Routing 실습

```py
# urls.py

urlpatterns = [
    path('articles/<int:num>/', views.detail),
]
```

```py
# views.py

def detail(request, num):
    context = {
        'num': num,
    }
    return render(request, 'articles/detail.html', context)
```

```django
<!-- articles/detail.html -->

{% extend 'articles/base.html' %}

{% block content %}
  <h1>Detail</h1>
  <h3>{{ num }}번 글 입니다.</h3>
{% endblock content %}
```

> Path Converter의 변수명과 View 함수의 파라미터 이름은 같아야 함.

- URL 변화에 따른 템플릿 관찰

![0919_Template&URLs_2025-09-19-12-18-58](images/0919_Template&URLs_2025-09-19-12-18-58.png)

```py
# urls.py

urlpatterns = [
    path('hello/<str:name>/', views.greeting),
]
```

```py
# views.py

def detail(request, name):
    context = {
        'name': name,
    }
    return render(request, 'articles/greeting.html', context)
```

```django
<!-- articles/greeting.html -->

{% extend 'articles/base.html' %}

{% block content %}
  <h1>Greeting</h1>
  <h3>{{ name }}님 안녕하세요 !</h3>
{% endblock content %}
```

- URL 변화에 따른 템플릿 관찰

![0919_Template&URLs_2025-09-19-12-20-49](images/0919_Template&URLs_2025-09-19-12-20-49.png)

## App URL 정의

### App URL mapping
- 각 앱에 URL을 정의하는 것
    - 프로젝트와 각 앱이 URL을 나누어 관리를 편하게 하기 위함
    - 현재는 앱이 하나밖에 없지만, 앞으로 앱이 늘어나면 서로 다른 앱의 URL들이 섞이지 않게 나눠 관리하는 법

### 2번째 앱 pages 생성 후 발생할 수 있는 문제
- view 함수 이름이 같거나, 같은 패턴의 URL 주소를 사용하게 되는 경우
- 아래와 같이 해결해 볼 수 있으나 더 나은 방법 필요

    ```py
    # urls.py

    from articles import views as article_views     # 본래 views로 사용되던 곳들을 article_views로 바꿔야 함
    from pages import views as page_views           # 권장되지 않으므로 작성하지 말 것

    urlpatterns = [
        ...,
        path('pages', page_views.index),
    ]
    ```

    > **"URL을 각자 app에서 관리하자"**

### 기존 URL 구조
- 프로젝트 urls.py에 모든 URL이 담겨있음

![0919_Template&URLs_2025-09-19-10-52-24](images/0919_Template&URLs_2025-09-19-10-52-24.png)

### 변경된 URL 구조
- 각 앱의 urls.py에서 각자의 URL 관리

![0919_Template&URLs_2025-09-19-10-52-50](images/0919_Template&URLs_2025-09-19-10-52-50.png)

### include 함수

```py
include('app.urls')
```

- 프로젝트 내부 앱들의 URL을 참조할 수 있도록 매핑하는 함수
    - URL의 일치하는 부분까지 잘라내고, 남은 문자열 부분은 후속 처리를 위해 include된 URL로 전달

---
- 각 앱에서 urls.py를 만들고

    ```py
    # articles/urls.py

    from django.urls import path
    from . import views

    urlpatterns = [
        path('index/', views.index),
    ]
    ```

- 프로젝트 urls.py에서 include()로 추가

    ```py
    # firstpjt/urls.py

    from django.urls import path, include

    urlpatterns = [
        path('articles/', include('articles.urls')),
    ]
    ```

- 요청 URL이 http://127.0.0.1:8000/articles/index/ 일 때
    - firstpjt/urls.py 에서 articles/ 까지 일치한 뒤
        ```py
        # firstpjt/urls.py

        from django.urls import path, include

        urlpatterns = [
            path('articles/', include('articles.urls')),
        ]
        ```
    - articles/urls.py 에서 나머지 index/ 를 찾음
        ```py
        # articles/urls.py

        from django.urls import path
        from . import views

        urlpatterns = [
            path('index/', views.index),
        ]
        ```

### URL 구조 변화
- 지금까지 만든 URL 이동시키기

```py
# firstpjt/urls.py

from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    
    # path('articles/', views.index),
    # path('dinner/', views.dinner),
    # path('search/', views.search),
    # path('throw/', views.throw),
    # path('catch/', views.catch),
    # path('articles/<int:num>/', views.detail),
    # path('hello/<str:name>/', views.greeting),
    # path('pages/', pages_views.index),

    path('articles/', include('articles.urls')),
    path('pages/', include('pages.urls')),
]
```

```py
# articles/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('index/', views.index),
    path('dinner/', views.dinner),
    path('search/', views.search),
    path('throw/', views.throw),
    path('catch/', views.catch),
    path('<int:num>/', views.detail),
    path('hello/<str:name>/', views.greeting),
]
```

```py
# pages/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('index/', pages_views.index),
]
```

- 주석 정리 후
```py
# firstpjt/urls.py

from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
    path('pages/', include('pages.urls')),
]
```

```py
# articles/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('index/', views.index),
    path('dinner/', views.dinner),
    path('search/', views.search),
    path('throw/', views.throw),
    path('catch/', views.catch),
    path('<int:num>/', views.detail),
    path('hello/<str:name>/', views.greeting),
]
```

```py
# pages/urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('index/', pages_views.index),
]
```

# URL 이름 지정

## Naming URL patterns

### URL 구조 변경에 따른 문제점
- 기존 'articles/' 주소가 'articles/index/'로 변경됨에 따라 해당 URL을 사용하는 모든 위치를 찾아가 변경해야 함

    ```py
    # firstpjt/urls.py

    from django.urls import path, include

    urlpatterns = [
        path('articles/', include('articles.urls')),
    ]
    ```

    ```py
    # articles/urls.py

    from django.urls import path, include
    from . import views

    urlpatterns = [
        path('index/', views.index)
    ]
    ```

    > "URL에 **<mark>이름</mark>을 지어주면 <mark>이름</mark>만 기억**하면 되지 않을까?

### Naming URL patterns
- URL에 이름을 지정하는 것
    - path 함수에 name 인자를 <u>키워드 인자</u>로 정의해서 사용

    ```py
    # articles/urls.py

    from django.urls import path
    from . import views

    urlpatterns = [
        path('index/', views.index, name='index'),
        path('dinner/', views.dinner, name='dinner'),
        path('search/', views.search, name='search'),
        path('throw/', views.throw, name='throw'),
        ...,
    ]
    ```

    ```py
    # pages/urls.py

    from django.urls import path
    from . import views

    urlpatterns = [
        path('index/', views.index, name='index'),
    ]
    ```

---
- 키워드 인자: 함수 호출 시 인자의 순서를 무시하고 특정 매개변수에 값을 할당하는 인자

### URL 표기 변화
- 해당 url을 사용했던 곳의 링크 변경
    - 새로운 articles/urls.py

     ```py
    # articles/urls.py

    from django.urls import path
    from . import views

    urlpatterns = [
        path('index/', views.index, name='index'),
        path('dinner/', views.index, name='dinner'),
        path('search/', views.index, name='search'),
        path('throw/', views.index, name='throw'),
        ...,
    ]
    ```

    - articles/index.html 변화

    ```django
    <!-- articles/index.html -->

    {% extends 'article/base.html' %}

    {% block content %}
      <h1>Hello, {{ name }}</h1>
      <a href='/dinner/'>dinner</a>
      <a href='/search/'>search</a>
      <a href='/throw/'>throw</a>
    {% endblock content %}
    ```

    ```django
    <!-- articles/index.html -->

    {% extends 'article/base.html' %}

    {% block content %}
      <h1>Hello, {{ name }}</h1>
      <a href="{% url 'dinner' %}">dinner</a>
      <a href="{% url 'search' %}">search</a>
      <a href="{% url 'throw' %}">throw</a>
    {% endblock content %}
    ```

    > a 태그의 href 속성 값 뿐만 아니라 form의 action 속성 등도 변경해 주어야 한다.

- 브라우저 상의 실제 링크 확인

![0919_Template&URLs_2025-09-19-11-06-46](images/0919_Template&URLs_2025-09-19-11-06-46.png)

```django
<!-- articles/index.html -->

{% extends 'article/base.html' %}

{% block content %}
    <h1>Hello, {{ name }}</h1>
    <a href="{% url 'dinner' %}">dinner</a>
    <a href="{% url 'search' %}">search</a>
    <a href="{% url 'throw' %}">throw</a>
{% endblock content %}
```

## DTL URL tag

```django
'url' tag
{% url 'url_name' arg1 arg2 %}
```

- 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환
    - URL에 이름을 붙였을 경우 **url 태그**와 **이름**을 이용해 템플릿 상에서 이름으로 실제 주소를 작성할 수 있게 해줌8

### 'url' tag

```django
{% url 'url_name' arg1 arg2 %}
```

- 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환

```django
<!-- articles/index.html -->

{% extends 'article/base.html' %}

{% block content %}
    <h1>Hello, {{ name }}</h1>
    <a href="{% url 'dinner' %}">dinner</a>
    <a href="{% url 'search' %}">search</a>
    <a href="{% url 'throw' %}">throw</a>
{% endblock content %}
```

![0919_Template&URLs_2025-09-19-11-09-05](images/0919_Template&URLs_2025-09-19-11-09-05.png)

> 태그 이름, URL 이름, 인자 등은 콤마(,)로 구분되지 않는다.

- URL 패턴에 변수가 포함되어 있으면, 'url_name' 이후 추가

```django
<!-- articles/index.html -->

{% extends 'article/base.html' %}

{% block content %}
    <h1>Articles</h1>
    <a href="{% url 'detail' 1 %}">Article 1</a>
    <a href="{% url 'detail' 2 %}">Article 2</a>
    <a href="{% url 'detail' 3 %}">Article 3</a>
{% endblock content %}
```

```py
path('<int:num>/', views.detail),
```

![0919_Template&URLs_2025-09-19-14-07-45](images/0919_Template&URLs_2025-09-19-14-07-45.png)

- DTL의 for 태그에서 사용한 변수 이름 사용 가능

```py
# articles/views.py

def index(request):
    context = {
        'nums': [1, 2, 3],
    }
    return render(request, 'articles/index.html', context)
```

> 실행 결과는 이전과 동일

# URL 이름 공간

## app_name 속성

### URL 이름 지정 후 남은 문제
- articles 앱의 url 이름과 pages 앱의 url 이름이 같은 상황
- 단순히 이름만으로는 완벽하게 분리할 수 없음
    - articles와 pages 모두 index가 있다.

    ```py
    # articles/urls.py

    urlpatterns = [
        path('index/', views.index, name='index'),
    ]
    ```

    ```py
    # pages/urls.py

    urlpatterns = [
        path('index/', views.index, name='index'),
    ]
    ```

> "이름에 <mark>성(key)</mark>을 붙이자"

### 'app_name' 속성 지정
- urls.py에 app_name 변수 설정

    ```py
    # articles/urls.py

    app_name = 'articles'
    urlpatterns = [
        path('index/', views.index, name='index'),
    ]
    ```

    ```py
    # pages/urls.py

    app_name = 'pages'
    urlpatterns = [
        path('index/', views.index, name='index'),
    ]
    ```

- app_name 이 추가 또는 수정되면 url 태그에도 해당 내용이 반영되어야 함
    ```django
    {% url 'url_name' arg1 arg2 %} -> {% url 'app_name:path_name' arg1 arg2 %}
    ```

- HTML 반영 후 확인

    ```django
    <!-- articles/index.html -->

    {% extends 'article/base.html' %}

    {% block content %}
        <h1>Hello, {{ name }}</h1>
        <a href="{% url 'articles:dinner' %}">dinner</a>
        <a href="{% url 'articles:search' %}">search</a>
        <a href="{% url 'articles:throw' %}">throw</a>
    {% endblock content %}
    ```

- 최종 링크는 변하지 않음

    ![0919_Template&URLs_2025-09-19-14-19-53](images/0919_Template&URLs_2025-09-19-14-19-53.png)

# 참고

## 추가 템플릿 경로

### 추가 템플릿 경로 지정
- 앱 폴더 내부 templates 폴더 (기본 경로)외에 템플릿을 위치하고 싶을 때

    ![0919_Template&URLs_2025-09-19-11-13-09](images/0919_Template&URLs_2025-09-19-11-13-09.png)

- 새로운 템플릿 경로

    ![0919_Template&URLs_2025-09-19-11-13-38](images/0919_Template&URLs_2025-09-19-11-13-38.png)

- 하위 템플릿에서 extends의 경로 수정 필요

    ```django
    {% extends 'base.html' %}
    ```

### BASE_DIR
- settings.py에서 경로지정을 편하게 하기 위해 최상단 지점을 지정해 둔 변수
    ```py
    # settings.py

    BASE_DIR = Path(__file__).resolve().parent.parent
    ```

    ![0919_Template&URLs_2025-09-19-14-24-29](images/0919_Template&URLs_2025-09-19-14-24-29.png)

- [Python의 객체 지향 파일 시스템 경로](https://docs.python.org/ko/3.9/library/pathlib.html#module-pathlib)

## DTL 주의사항
- Python 처럼 일부 프로그래밍 구조(if, for 등)를 사용할 수 있지만 명칭을 그렇게 설계했을 뿐
- Python 코드로 실행되는 것이 아니며 **Python과는 관련 없음**
- 프로그래밍적 로직이 아니라 표현을 위한 것임을 명심하기
- **프로그래밍적 로직은 되도록 view 함수에서 작성 및 처리할 것**
- [공식 문서](https://docs.djangoproject.com/en/5.2/ref/templates/builtins/)를 참고해 다양한 태그와 필터 사용해보기

## Trailing Slashes

### URL의 Trailing Slashes
- Django는 URL 끝에 '/'가 없다면 자동으로 붙임
- "기술적인 측면에서, `foo.com/bar`와 `foo.com/bar/`는 서로 다른 URL"
    - 검색 엔진 로봇이나 웹 트래픽 분석 도구에서는 이 두 주소를 서로 다른 페이지로 보기 때문
- 그래서 Django는 검색 엔진이 혼동하지 않게 하기 위해 무조건 붙이는 것을 선택
- 그러나 모든 프레임워크가 이렇게 동작하는 것은 아니니 주의

### 실습
- Template System
    - 3022. base template 만들기
    - 3226. 도서 조회 서비스 만들기 - 데이터 수집 및 처리
    - 3227. 도서 조회 서비스 만들기 - 베스트 셀러
- 요청과 응답
    - 2648. form tag 실습 예제
    - 3023. 페이지 간 데이터 주고 받기
- Django URLs
    - 2649. Django에서의 URL
- URL 이름 지정
    - 3228. 도서 조회 서비스 만들기 - 코드 개선

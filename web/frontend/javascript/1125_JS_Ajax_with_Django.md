# Ajax와 서버

### [복습] Ajax란
- Ajax(Asynchronous JavaScript and XML): 비동기적인 웹 애플리케이션 개발을 위한 기술

### [복습] Ajax를 활용한 클라이언트 서버 간 동작
- **XHR 객체 생성 및 요청** -> **응답 데이터 생성** -> **JSON 데이터 응답** -> **Promise 객체를 활용해 DOM 조작**<br>(웹 페이지의 일부분 만을 다시 로딩)

  ![1125_JS_Ajax_with_Django_2025-11-25-08-54-26](images/1125_JS_Ajax_with_Django_2025-11-25-08-54-26.png)

# Ajax with follow

## 비동기 팔로우 구현

### 사전 준비
1. M:N 관계 모델링까지 진행된 Django 프로젝트 준비
2. 가상 환경 생성, 활성화 및 패키지 설치

### 비동기 팔로우 구현 - Ajax 적용
- 프로필 페이지에 axios CDN 작성

![1125_JS_Ajax_with_Django_2025-11-25-08-58-21](images/1125_JS_Ajax_with_Django_2025-11-25-08-58-21.png)

- form 요소 선택을 위해 id 속성 지정 및 선택
- action과 method 속성은 삭제
  > 요청은 axios로 대체할 예정

![1125_JS_Ajax_with_Django_2025-11-25-08-58-50](images/1125_JS_Ajax_with_Django_2025-11-25-08-58-50.png)

- form 요소에 이벤트 핸들러 할당
- submit 이벤트의 기본 동작 취소하기

![1125_JS_Ajax_with_Django_2025-11-25-09-04-41](images/1125_JS_Ajax_with_Django_2025-11-25-09-04-41.png)

- axios 요청 코드 작성
  1. 요청 url에 필요한 사용자 pk는 어떻게 작성해야 할까?
  2. CSRF 토큰은 어떻게 보내야 할까?

  ![1125_JS_Ajax_with_Django_2025-11-25-09-06-32](images/1125_JS_Ajax_with_Django_2025-11-25-09-06-32.png)

### '[data-*](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/data-*)' 속성
- 사용자 지정 데이터 속성을 만들어, HTML과 DOM 사이에서 임의의 데이터를 교환하는 방법
- 모든 사용자 지정 데이터는 JavaScript에서 **dataset 속성**을 통해 접근
- 주의사항
  - 대소문자 여부에 상관없이 'xml' 문자로 시작 불가
  - 세미콜론 포함 불가
  - 대문자 포함 불가

![1125_JS_Ajax_with_Django_2025-11-25-09-09-21](images/1125_JS_Ajax_with_Django_2025-11-25-09-09-21.png)

### 비동기 팔로우 구현 - Ajax 적용
- 요청 url 작성 마무리

![1125_JS_Ajax_with_Django_2025-11-25-09-11-03](images/1125_JS_Ajax_with_Django_2025-11-25-09-11-03.png)

- 문서상 input hidden 타입으로 존재하는 csrf token 데이터를 이제는 **axios**로 전송해야 함

![1125_JS_Ajax_with_Django_2025-11-25-09-11-43](images/1125_JS_Ajax_with_Django_2025-11-25-09-11-43.png)

![1125_JS_Ajax_with_Django_2025-11-25-09-12-22](images/1125_JS_Ajax_with_Django_2025-11-25-09-12-22.png)

- 팔로우 버튼을 토글하기 위해서는 현재 팔로우 상태인지 언팔로우 상태인지에 대한 상태 확인이 필요
- Django의 view 함수에서 **팔로우 여부를 나타내는 변수(is_followed)** 를 추가하여 JSON 형식으로 응답
- 팔로우 상태 여부를 JS에게 전달한 데이터 작성
- 응답은 HTML 문서가 아닌 **JSON 데이터로 응답**하도록 변경 (**JsonResponse** 활용)

![1125_JS_Ajax_with_Django_2025-11-25-09-15-14](images/1125_JS_Ajax_with_Django_2025-11-25-09-15-14.png)

- 팔로우 요청 후 Django 서버로부터 받은 응답 데이터 확인하기

![1125_JS_Ajax_with_Django_2025-11-25-09-17-32](images/1125_JS_Ajax_with_Django_2025-11-25-09-17-32.png)

- 응답 데이터 is_followed 에 따라 팔로우 버튼을 조작하기

![1125_JS_Ajax_with_Django_2025-11-25-09-22-08](images/1125_JS_Ajax_with_Django_2025-11-25-09-22-08.png)

- 클라이언트와 서버 간 XHR 객체를 주고 받는 것을 확인하기
- 개발자도구 - Network

![1125_JS_Ajax_with_Django_2025-11-25-09-23-28](images/1125_JS_Ajax_with_Django_2025-11-25-09-23-28.png)

- "팔로잉 수와 팔로워 수 비동기 적용"
- Django view 함수에서 팔로워, 팔로잉 인원 수 연산을 진행하여 결과를 응답 데이터로 전달

![1125_JS_Ajax_with_Django_2025-11-25-09-26-19](images/1125_JS_Ajax_with_Django_2025-11-25-09-26-19.png)

- 해당 요소를 선택할 수 있도록 span 태그와 id 속성 작성
- 각 span 태그를 선택 후 응답 데이터를 받아 각 태그의 인원 수 값 변경에 활용

![1125_JS_Ajax_with_Django_2025-11-25-09-27-35](images/1125_JS_Ajax_with_Django_2025-11-25-09-27-35.png)

# Ajax with likes

## 비동기 좋아요 구현

### Ajax 좋아요 적용 시 유의사항
- 전반적인 Ajax 적용 방식은 팔로우 구현 과정과 동일
- 하지만 팔로우와 달리 '좋아요' 버튼은 한 페이지에 여러 개가 존재할 수 있음
- 그렇다면 모든 '좋아요' 버튼에 각각 이벤트 리스너를 등록해야 할까?

![1125_JS_Ajax_with_Django_2025-11-25-09-32-03](images/1125_JS_Ajax_with_Django_2025-11-25-09-32-03.png)

### [복습] 버블링 (Bubbling)
- 한 요소에 이벤트가 발생하면, 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러가 동작하는 현상
- 가장 최상단의 조상 요소(document)를 만날 때까지 이 과정이 반복되면서 요소 각각에 할당된 핸들러가 동작

![1125_JS_Ajax_with_Django_2025-11-25-09-32-51](images/1125_JS_Ajax_with_Django_2025-11-25-09-32-51.png)

> 최하위의 \<p> 요소를 클릭하면 p -> div -> form 순서로 3개의 이벤트 핸들러가 모두 순차적으로 동작

### [복습] 버블링이 필요한 이유
- 만약 다음과 같이 각자 다른 동작을 수행하는 버튼이 여러 개가 있다고 가정하면, 각 버튼마다 서로 다른 이벤트 핸들러를 할당해야 할까?
> **각 버튼의 공통 조상인 div 요소에 이벤트 핸들러 단 하나만 할당하기**

![1125_JS_Ajax_with_Django_2025-11-25-09-34-09](images/1125_JS_Ajax_with_Django_2025-11-25-09-34-09.png)

- **요소의 공통 조상**에 **이벤트 핸들러**를 단 하나만 할당하면, 여러 버튼 요소에서 발생하는 이벤트를 한꺼번에 다룰 수 있음
- 공통 조상(div)에 할당한 핸들러에서 event.target을 이용하면 실제 어떤 버튼에서 이벤트가 발생했는지 알 수 있기 때문

![1125_JS_Ajax_with_Django_2025-11-25-09-34-58](images/1125_JS_Ajax_with_Django_2025-11-25-09-34-58.png)

### 비동기 좋아요 구현 - Ajax 적용
- 모든 좋아요 form 요소를 포함하는 최상위 요소 작성

![1125_JS_Ajax_with_Django_2025-11-25-09-35-20](images/1125_JS_Ajax_with_Django_2025-11-25-09-35-20.png)

1. 최상위 요소 선택
2. 이벤트 핸들러 할당
3. 하위 요소에서 발생하는 submit 이벤트를 감지하고, form의 기본 제출 동작을 취소

![1125_JS_Ajax_with_Django_2025-11-25-09-35-48](images/1125_JS_Ajax_with_Django_2025-11-25-09-35-48.png)

- axios 코드 작성
> url 작성에 필요한 article pk는 어떻게 작성해야 할까?

![1125_JS_Ajax_with_Django_2025-11-25-09-36-12](images/1125_JS_Ajax_with_Django_2025-11-25-09-36-12.png)

- 각 form에 data-article-id="{{ article.pk }}" 와 같이 data-* 속성을 부여하여 JS에서 참조할 수 있도록 하기

  ![1125_JS_Ajax_with_Django_2025-11-25-09-37-13](images/1125_JS_Ajax_with_Django_2025-11-25-09-37-13.png)

### [복습] 이벤트가 정확히 어디서 발생했는지 접근할 수 있는 방법
1. event.currentTarget
    - '현재' 요소
    - 항상 이벤트 핸들러가 연결된 요소만을 참조하는 속성
    - 'this'와 같음
2. event.target
    - 이벤트가 발생한 가장 안쪽의 요소(target)를 참조하는 속성
    - **실제 이벤트가 시작된 요소**
    - 버블링이 진행되어도 변하지 않음

### 비동기 좋아요 구현 - Ajax 적용
- url 완성 후 요청 및 응답 확인

![1125_JS_Ajax_with_Django_2025-11-25-09-39-27](images/1125_JS_Ajax_with_Django_2025-11-25-09-39-27.png)

- 좋아요 버튼을 토글하기 위해서는 현재 사용자가 좋아요를 누른 상태인지 좋아요를 누르지 않은 상태인지에 대한 **상태 확인**이 필요
> Django의 view 함수에서 좋아요 여부를 파악할 수 있는 변수 추가 생성

> JSON 타입으로 응답하기

- 좋아요 상태 여부를 JS에게 전달할 데이터 작성 및 JSON 데이터 응답

![1125_JS_Ajax_with_Django_2025-11-25-09-40-30](images/1125_JS_Ajax_with_Django_2025-11-25-09-40-30.png)

- 응답 데이터 is_liked를 받아 isLiked 변수에 할당

![1125_JS_Ajax_with_Django_2025-11-25-09-40-48](images/1125_JS_Ajax_with_Django_2025-11-25-09-40-48.png)

- isLiked에 따라 좋아요 버튼을 토글하기
  > 어떤 게시글의 '좋아요' 버튼을 선택했는지 구별할 방법이 필요

![1125_JS_Ajax_with_Django_2025-11-25-09-41-38](images/1125_JS_Ajax_with_Django_2025-11-25-09-41-38.png)

- 문자열과 article.pk 값을 조합하여 각 '좋아요' 버튼(또는 관련 요소)에 고유한 id 속성을 부여
- 각 좋아요 버튼을 선택 후 isLiked에 따라 버튼을 토글

![1125_JS_Ajax_with_Django_2025-11-25-09-42-17](images/1125_JS_Ajax_with_Django_2025-11-25-09-42-17.png)

### 비동기 좋아요 구현 - 버블링을 활용하지 않았다면?
1. querySelectorAll()을 사용해 전체 좋아요 버튼을 선택
    - querySelectorAll() 선택을 위한 class 적용

![1125_JS_Ajax_with_Django_2025-11-25-09-44-08](images/1125_JS_Ajax_with_Django_2025-11-25-09-44-08.png)

2. forEach()를 사용해 전체 좋아요 버튼을 순회하면서 진행 

![1125_JS_Ajax_with_Django_2025-11-25-09-44-18](images/1125_JS_Ajax_with_Django_2025-11-25-09-44-18.png)

### 실습
- Ajax
  - 1933\. Ajax - 팔로잉 요청 준비
  - 1934\. Ajax - 팔로잉 요청 구현
  - 1935\. Ajax 요청 - 게시글 삭제
- Ajax 활용
  - 3088\. Ajax를 활용한 좋아요 구현하기 - axios 요청
  - 3089\. Ajax를 활용한 좋아요 구현하기 - json 응답 및 DOM 조작
  - 3297\. Ajax를 활용한 좋아요 구현하기 - 좋아요 버튼 스타일링
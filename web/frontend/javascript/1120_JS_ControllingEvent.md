# 이벤트

### 일상속의 이벤트
- 컴퓨터 키보드를 눌러 텍스트를 입력하는 것
- 전화벨이 울려 전화가 왔음을 알리는 것
- 손을 흔들어 인사하는 것
- 전화기의 버튼을 눌러서 통화를 시작하는 것
- 리모컨을 사용하여 채널을 변경하는 것

  ![1120_JS_ControllingEvent_2025-11-20-08-52-52](images/1120_JS_ControllingEvent_2025-11-20-08-52-52.png)

### 웹에서의 이벤트
- 화면을 스크롤하는 것
- 버튼을 클릭했을 때 팝업 창이 출력되는 것
- 마우스 커서의 위치에 따라 드래그 앤 드롭하는 것
- 사용자의 키보드 입력 값에 따라 새로운 요소를 생성하는 것
> 웹에서의 거의 **모든 상호작용은 이벤트와 함께 함**

  ![1120_JS_ControllingEvent_2025-11-20-08-53-06](images/1120_JS_ControllingEvent_2025-11-20-08-53-06.png)

## event

### event
- event: 웹 페이지 상에서 '무언가 일어났다는 신호 또는 사건'
  - JS 이벤트는 '영화 서비스'와 같음
  - 우리가 보고 싶은 영화 포스터에 마우스를 올리면(**이벤트**), 시스템은 마우스의 움직임을 감지(리스너)
  - 작은 미리보기 영상이나 설명을 보여주는(핸들러) 반응을 보임
  - 마우스 움직임 하나하나가 이벤트가 될 수 있고, 이러한 다양한 클릭, 입력, 변경하는 행위가 이벤트에 해당함

### DOM 요소와 이벤트
- 모든 DOM 요소는 다양한 형태의 이벤트를 발생시킬 수 있음
  - DOM 요소: HTML 문서의 각 태그를 하나의 객체로 변환한 것
- 예: button 을 클릭하면 click 이벤트, input 값 변경 시 input 이벤트, ...

  ![1120_JS_ControllingEvent_2025-11-20-08-55-50](images/1120_JS_ControllingEvent_2025-11-20-08-55-50.png)

## evnet object

### event object
- DOM에서 이벤트가 발생하면, 브라우저는 해당 이벤트에 관한 정보를 담은 'event object'를 자동으로 생성
- 이벤트 종류
  - mouse
  - input
  - keyboard
  - ...

  ![1120_JS_ControllingEvent_2025-11-20-08-57-08](images/1120_JS_ControllingEvent_2025-11-20-08-57-08.png)

#### TIP
- 이벤트 객체는 이벤트 발생 순간의 상황(어떤 요소에서 이벤트가 발생했는지, 마우스 좌표는 어디인지, 눌린 키는 무엇인지 등)과 관련된 상세 정보를 담고 있음
- 이를 통해 이벤트와 관련된 구체적인 정보를 참조할 수 있음

### DOM 요소에서 event가 발생하면, 해당 event는 연결된 이벤트 처리기(**event handler)** 에 의해 처리됨

![1120_JS_ControllingEvent_2025-11-20-08-58-29](images/1120_JS_ControllingEvent_2025-11-20-08-58-29.png)

## event handler

### event handler
- event handler: 특정 이벤트가 발생했을 때 실행되는 (콜백)함수
  - 보통 addEventListener를 통해 DOM 요소에 event handle를 등록

### .addEventListener()
- .addEventListener(): 특정 DOM 요소에, 지정한 이벤트가 발생했을 때 실행할 이벤트 핸들러를 **등록하는 메서드**
  - 이벤트 핸들러(콜백 함수)를 DOM 요소에 연결하는 역할을 담당

### .addEventListener() 예시
- handleClick 함수가 이벤트 핸들러이며, button.addEventListener()는 그 핸들러를 click 이벤트에 연결해주는 역할

![1120_JS_ControllingEvent_2025-11-20-09-02-08](images/1120_JS_ControllingEvent_2025-11-20-09-02-08.png)

### 이벤트 등록(addEventListener)
- DOM 요소: HTML 문서의 각 태그를 하나의 객체로 변환한 것
- 수신할 이벤트: 무언가 일어났다는 신호 또는 사건
- 핸들러: 특정 이벤트가 발생했을 때 실행되는 (콜백)함수

![1120_JS_ControllingEvent_2025-11-20-09-02-52](images/1120_JS_ControllingEvent_2025-11-20-09-02-52.png)

### addEventListener 구조
- 메서드 구문
  - `.addEventListener(type, handler)`

    ![1120_JS_ControllingEvent_2025-11-20-09-05-03](images/1120_JS_ControllingEvent_2025-11-20-09-05-03.png)

- type
  - 수신할 이벤트 유형
  - 문자열로 작성 (ex: 'click', 'mouseover' 등)
- handler
  - 이벤트 발생 시 호출되는 콜백 함수
  - 자동으로 event 객체를 첫 번째 매개변수로 받음
  - 반환 값 없음

### 이벤트 객체 전달
- 이벤트 발생 시, 이벤트 객체는 자동으로 이벤트 핸들러 함수에 인자로 전달됨
- 핸들러 함수는 이 인자를 통해 이벤트에 대한 상세 정보(이벤트 발생 요소, 이벤트 타입, 추가 데이터 등)에 접근하고 적절한 동작을 수행

![1120_JS_ControllingEvent_2025-11-20-09-06-35](images/1120_JS_ControllingEvent_2025-11-20-09-06-35.png)

### 이벤트 핸들러에서의 this
- 일반 함수를 핸들러로 사용 시, this는 이벤트 리스너가 연결된 요소를 가리킴<br>
(event 객체의 currentTarget 속성 값과 동일)

![1120_JS_ControllingEvent_2025-11-20-09-08-18](images/1120_JS_ControllingEvent_2025-11-20-09-08-18.png)

# 버블링

### 버블링 개요
- form > div > p 형태의 중첩된 구조에 각각 이벤트 핸들러가 연결되어 있을 때, 만약 \<p> 요소를 클릭하면 어떻게 될까?

![1120_JS_ControllingEvent_2025-11-20-09-09-26](images/1120_JS_ControllingEvent_2025-11-20-09-09-26.png)

- \<p> 요소만 클릭했는데도 불구하고 모든 핸들러가 동작함
> 왜 p만을 클릭했는데 부모 요소 \<div>와 \<form>에 할당된 핸들러까지 동작할까?

![1120_JS_ControllingEvent_2025-11-20-09-14-45](images/1120_JS_ControllingEvent_2025-11-20-09-14-45.png)

### 버블링 (Bubbling)
- 한 요소에 이벤트가 발생하면, 해당 요소의 핸들러가 동작한 후 이어서 부모 요소의 핸들러가 동작하는 현상
- 가장 최상단의 조상 요소(document)를 만날 때까지 이 과정이 반복되면서 요소 각각에 할당된 핸들러가 동작
> 최하위의 \<p> 요소를 클릭하면 p -> div -> form 순서로 3개의 이벤트 핸들러가 모두 순차적으로 동작했던 것

#### TIP
- 이벤트가 제일 깊은 곳에 있는 요소에서 시작해 부모 요소를 거슬러 올라가며 발생하는 것이 마치 물속 거품과 닮았기 때문에 버블링이라 칭함

### 이벤트가 정확히 어디서 발생했는지 접근할 수 있는 방법
1. event.**currentTarget**
    - '현재' 요소
    - 항상 이벤트 핸들러가 연결된 요소만을 참조하는 속성
    - 'this'와 같음
2. event.**target**
    - 이벤트가 발생한 가장 안쪽의 요소(target)를 참조하는 속성
    - 실제 이벤트가 시작된 요소
    - 버블링이 진행되어도 변하지 않음

### 'target' & 'currentTarget' 예시
- 세 요소 중 가장 최상위 요소인 **outerouter 요소**에만 핸들러가 연결
- 각 요소를 클릭했을 때 event의 target과 currentTarget의 차이 비교

![1120_JS_ControllingEvent_2025-11-20-09-18-48](images/1120_JS_ControllingEvent_2025-11-20-09-18-48.png)

- 핸들러는 outerouter에만 연결되어 있지만, 하위 요소 outer와 inner를 클릭해도 해당 핸들러가 동작함
- 클릭 이벤트가 어디서 발생했든 상관없이 outerouter까지 이벤트가 버블링되어 핸들러를 실행시키기 때문

![1120_JS_ControllingEvent_2025-11-20-09-19-57](images/1120_JS_ControllingEvent_2025-11-20-09-19-57.png)

## 캡처링과 버블링

### 캡처링(capturing)
- 이벤트가 최상위 조상에서 타겟 요소까지 하위로 전파되는 단계 (버블링과 반대)
- table 의 하위 요소 td를 클릭하면, 이벤트는 먼저 **최상위 요소부터 아래로 전파**됨 (캡처링)
- 실제 이벤트가 발생한 지점(event.target)에서 실행된 후 **다시 위로 전파** (버블링)

  ![1120_JS_ControllingEvent_2025-11-20-09-22-07](images/1120_JS_ControllingEvent_2025-11-20-09-22-07.png)

#### TIP
- 캡처링은 실제 개발자가 다루는 경우가 거의 없으므로 버블링을 집중해서 학습하는 것이 좋음

## 버블링의 필요성

### 버블링이 필요한 이유
- 만약 다음과 같이 각자 다른 동작을 수행하는 버튼이 여러 개가 있다고 가정하면, 각 버튼마다 서로 다른 이벤트 핸들러를 등록해야 할까?
> **각 버튼의 공통 조상인 div 요소에 이벤트 핸들러 단 하나만 할당하기**

![1120_JS_ControllingEvent_2025-11-20-09-23-14](images/1120_JS_ControllingEvent_2025-11-20-09-23-14.png)

- **요소들의 공통 조상에** 이벤트 핸들러를 **하나만 등록**하면, 여러 자식 요소에서 발생하는 이벤트를 한 곳에서 효율적으로 다룰 수 있음
- 공통 조상(div)에 할당한 핸들러에서 event.target을 이용하면 실제 어떤 버튼에서 이벤트가 발생했는지 알 수 있기 때문

![1120_JS_ControllingEvent_2025-11-20-09-24-11](images/1120_JS_ControllingEvent_2025-11-20-09-24-11.png)

# event handler 활용

### event handler 활용 실습 목록
1. 버튼을 클릭하면 숫자를 1씩 증가해서 출력하기
2. 사용자 입력 값을 실시간으로 출력하기
3. 사용자 입력 값을 실시간으로 출력하기 + 버튼을 클릭하면 출력된 값의 CSS 스타일을 변경하기
4. todo 프로그램 구현
5. 로또 번호 생성기 구현

### 1. click 이벤트 실습
- 버튼을 클릭하면 숫자를 1씩 증가

  ![1120_JS_ControllingEvent_2025-11-20-09-25-24](images/1120_JS_ControllingEvent_2025-11-20-09-25-24.png)

![1120_JS_ControllingEvent_2025-11-20-09-25-46](images/1120_JS_ControllingEvent_2025-11-20-09-25-46.png)

### 2. input 이벤트 실습
- 사용자의 입력 값을 실시간으로 출력하기

  ![1120_JS_ControllingEvent_2025-11-20-09-33-06](images/1120_JS_ControllingEvent_2025-11-20-09-33-06.png)

![1120_JS_ControllingEvent_2025-11-20-09-33-30](images/1120_JS_ControllingEvent_2025-11-20-09-33-30.png)

### 'currentTarget' 주의사항
- console.log()로 event 객체를 출력할 경우, currentTarget 키의 값은 null을 가짐
- currentTarget은 이벤트가 처리되는 동안에만 사용할 수 있기 때문
- 대신 console.log(event.currentTarget)로 확인 가능
- currentTarget 이후의 속성 값들은 **'target'을 참고해서 사용하기**

  ![1120_JS_ControllingEvent_2025-11-20-09-44-27](images/1120_JS_ControllingEvent_2025-11-20-09-44-27.png)

### 3. click & input 이벤트 실습
- 입력 값을 실시간으로 출력하고, 클릭 버튼을 클릭 시 출력 값의 CSS 변경하기

  ![1120_JS_ControllingEvent_2025-11-20-09-44-54](images/1120_JS_ControllingEvent_2025-11-20-09-44-54.png)

![1120_JS_ControllingEvent_2025-11-20-09-45-21](images/1120_JS_ControllingEvent_2025-11-20-09-45-21.png)

### 4. todo 실습
- 입력 후 '+' 버튼 클릭 시, 실시간으로 리스트에 출력

  ![1120_JS_ControllingEvent_2025-11-20-09-50-34](images/1120_JS_ControllingEvent_2025-11-20-09-50-34.png)

  ![1120_JS_ControllingEvent_2025-11-20-09-50-43](images/1120_JS_ControllingEvent_2025-11-20-09-50-43.png)

  ![1120_JS_ControllingEvent_2025-11-20-09-50-48](images/1120_JS_ControllingEvent_2025-11-20-09-50-48.png)

- 추가 기능 구현
  1. 빈 문자열 입력 방지
  2. 입력이 없을 경우 경고 대화상자를 띄움

  ![1120_JS_ControllingEvent_2025-11-20-10-04-18](images/1120_JS_ControllingEvent_2025-11-20-10-04-18.png)

### 5. 로또 번호 생성기 실습
- '행운 번호 받기' 버튼 클릭 시, 6자리 랜덤 숫자가 실시간으로 리스트에 출력

  ![1120_JS_ControllingEvent_2025-11-20-10-04-48](images/1120_JS_ControllingEvent_2025-11-20-10-04-48.png)

  ![1120_JS_ControllingEvent_2025-11-20-10-04-57](images/1120_JS_ControllingEvent_2025-11-20-10-04-57.png)

  ![1120_JS_ControllingEvent_2025-11-20-10-05-21](images/1120_JS_ControllingEvent_2025-11-20-10-05-21.png)

### lodash
- [lodash](https://lodash.com/): 모듈성, 성능 및 추가 기능을 제공하는 JavaScript 유틸리티 라이브러리 array/object 등 자료구조를 다룰 때, 간편하고 유용한 함수들을 제공

  ![1120_JS_ControllingEvent_2025-11-20-10-12-07](images/1120_JS_ControllingEvent_2025-11-20-10-12-07.png)

## 이벤트 기본 동작 취소하기

### 이벤트 기본 동작 취소하기
- HTML의 각 요소가 기본적으로 가지고 있는 이벤트가 때로는 방해가 되는 경우가 있어 이벤트의 기본 동작을 취소할 필요가 있음
- 예시
  - form 요소의 제출 이벤트를 취소하여 페이지 새로고침을 막을 수 있음
  - \<a> 태그를 클릭했을 때 페이지 이동을 막고, 대신 다른 로직을 수행하게 할 수 있음

### preventDefault
- .preventDefault(): 해당 이벤트에 대한 기본 동작을 실행하지 않도록 지정
  - '회원가입 시 실수'를 막는 것과 같음
  - 회원가입 정보를 입력하다 실수로 뒤로가기를 눌렀을 때, "정말 이동하시겠습니까?"라는 문구 발생
  - 입력한 정보가 초기화되는 실수를 막아주기 위해 사용한 기능이 preventDefault

### 이벤트 동작 취소 실습 목록
1. copy 이벤트 동작 취소
2. form 제출 시 페이지 새로고침 동작 취소

### 1. copy 이벤트 동작 취소
- 복사 이벤트를 실행하지 못하도록 하기 (콘텐츠를 복사하는 것을 방지)

  ![1120_JS_ControllingEvent_2025-11-20-10-15-52](images/1120_JS_ControllingEvent_2025-11-20-10-15-52.png)

  ![1120_JS_ControllingEvent_2025-11-20-10-16-00](images/1120_JS_ControllingEvent_2025-11-20-10-16-00.png)

### 2. form 제출 시 페이지 새로고침 동작 취소
- form 요소의 submit 동작(action 값으로 요청)을 취소시킴
- 실습 시 submit 버튼을 눌러도 새로고침이 안 되는 것을 확인할 수 있음

![1120_JS_ControllingEvent_2025-11-20-10-17-39](images/1120_JS_ControllingEvent_2025-11-20-10-17-39.png)

# 참고

## addEventListener와 화살표 함수 관계

### addEventListener에서의 화살표 함수 주의사항
- 화살표 함수는 자신만의 this를 가지지 않음
- 대신, 자신이 선언된 상위 스코프의 this를 그대로 물려받아 사용
- 따라서 이벤트 핸들러로 화살표 함수를 사용하면, this는 대부분 전역 객체(window)를 가리키게 됨
- 해결책
  - 일반 함수로 사용하기
  - 화살표 함수일 경우 event.currentTarget을 사용하기

![1120_JS_ControllingEvent_2025-11-20-10-19-57](images/1120_JS_ControllingEvent_2025-11-20-10-19-57.png)

### 실습
- 이벤트
  - 1917\. input Event - Bad Word Filter
  - 1923\. Click Event - ThemeSwitcher
  - 1919\. change Event - Form Validator
  - 1920\. submit Event - Card Maker
  - 3083\. 이벤트 핸들러와 DOM 조작 - 기초
- 버블링
  - 3082\. 버블링과 캡처링
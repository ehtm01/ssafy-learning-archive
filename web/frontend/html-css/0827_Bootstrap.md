# Bootstrap
<u>CSS</u> 프론트엔드 프레임워크 (Toolkit)

- 미리 만들어진 다양한 디자인 요소들을 제공하여 웹 사이트를 빠르고 쉽게 개발할 수 있도록 함
- 현재 가장 인기있는 프론트엔드 프레임워크

### Bootstrap 사용해보기
- Bootstrap 설치
    - https://getbootstrap.com/ 접속 후 Read the docs

![0827_Bootstrap_2025-08-29-09-09-05](images/0827_Bootstrap_2025-08-29-09-09-05.png)

- "2. Include Bootstrap's CSS and JS." 코드 복사

![0827_Bootstrap_2025-08-29-09-09-17](images/0827_Bootstrap_2025-08-29-09-09-17.png)

- Bootstrap은 CSS와 JacaScript로 만들어져 있음
    - link와 script 요소로 HTML에 추가

### CDN(Content Delivery Network)
- 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간을 최소화
    - 웹 페이지 로드 속도를 높임
- 지리적으로 사용자와 가까운 CDN 서버에 콘텐츠를 저장해서 사용자에게 전달

![0827_Bootstrap_2025-08-29-09-08-28](images/0827_Bootstrap_2025-08-29-09-08-28.png)

### Bootstrap CDN
1. Bootstrap 홈페이지 - Docs - Download - "Compiled CSS and JS" 다운로드
2. bootstrap.css, bootstrap.js 파일 참고
    - 온라인 CDN에 업로드 된 CSS 및 JS 파일을 불러와서 사용하는 것

![0827_Bootstrap_2025-08-29-09-10-49](images/0827_Bootstrap_2025-08-29-09-10-49.png)

## Bootstrap 사용 가이드

### Bootstrap 기본 사용법
- Bootstrap에는 특정한 규칙이 있는 클래스 이름으로 스타일 및 레이아웃이 미리 작성되어 있음
- Spacing을 표현하는 방법
    - property: <u>margin</u> 또는 <u>padding</u>
    - sides: 방향 (top, left, x, y 등)
    - size: Spacing의 상대적 너비

![0827_Bootstrap_2025-08-29-09-16-40](images/0827_Bootstrap_2025-08-29-09-16-40.png)

### Bootstrap에서 클래스 이름으로 Spacing을 표현하는 방법

![0827_Bootstrap_2025-08-29-09-17-35](images/0827_Bootstrap_2025-08-29-09-17-35.png)

- https://getbootstrap.com/docs/5.3/utilities/spacing/#margin-and-padding

![0827_Bootstrap_2025-08-29-09-18-28](images/0827_Bootstrap_2025-08-29-09-18-28.png)

# Reset CSS

### Bootstrap 적용 전/후 비교
- Bootstrap을 HTML에 반영하면 일부 스타일이 바뀜
    - h1 요소의 폰트 변경됨
    - body와의 여백 사라짐

![0827_Bootstrap_2025-08-29-09-19-05](images/0827_Bootstrap_2025-08-29-09-19-05.png)

### Reset CSS
모든 HTML 요소 스타일을 일관된 기준으로 재설정하는 간결하고 압축된 규칙 시트

- HTML Element, Table, List 등의 요소들에 일관성 있게 스타일을 적용시키는 기본 단계이다.

### Reset CSS 사용 배경
- 모든 브라우저는 각자의 'user agent stylesheet'를 가지고 있음
    - 웹 사이트를 보다 읽기 편하게 하기 위해
- 문제는 이 설정이 브라우저마다 상이하다는 것
- 모든 브라우저에서 웹사이트를 동일하게 보이게 만들어야 하는 개발자에겐 매우 골치 아픈 일

> 모두 똑같은 스타일 상태로 만들고 스타일 개발을 시작하자!

### User-agent stylesheets
- 모든 문서에 기본 스타일을 제공하는 기본 스타일 시트

![0827_Bootstrap_2025-08-29-09-21-31](images/0827_Bootstrap_2025-08-29-09-21-31.png)

### Normalize CSS
- Reset CSS 방법 중 대표적인 방법
- 웹 표준 기준으로 브라우저 중 하나가 불일치한다면 차이가 있는 브라우저를 수정하는 방법
    - 경우에 따라 IE 또는 EDGE 브라우저는 표준에 따라 수정할 수 없는 경우도 있는데,<br>이 경우 IE 또는 EDGE의 스타일을 나머지 브라우저에 적용시킴

### Bootstrap에서의 Reset CSS
- Bootstrap은 bootstrap-reboot.css라는 파일명으로 normalize.css를 자체적으로 커스텀해서 사용중

![0827_Bootstrap_2025-08-29-09-23-36](images/0827_Bootstrap_2025-08-29-09-23-36.png)

# Bootstrap 활용

## Typograpy
- 제목, 본문 텍스트, 목록 등

![0827_Bootstrap_2025-08-29-09-23-52](images/0827_Bootstrap_2025-08-29-09-23-52.png)

### Disply headings
- 기존 Heading보다 더 눈에 띄는 제목이 필요할 경우
    - 더 크고 약간 다른 스타일

![0827_Bootstrap_2025-08-29-09-24-54](images/0827_Bootstrap_2025-08-29-09-24-54.png)

### Inline text elements
- HTML inline 요소에 대한 스타일

![0827_Bootstrap_2025-08-29-09-25-27](images/0827_Bootstrap_2025-08-29-09-25-27.png)

### Lists
- HTML list 요소에 대한 스타일

![0827_Bootstrap_2025-08-29-09-25-57](images/0827_Bootstrap_2025-08-29-09-25-57.png)

## Colors

### Bootstrap Color System
- Bootstrap이 지정하고 제공하는 색상 시스템
- 일관성 있는 의미론적 관점의 색상을 적용할 수 있게 해줌
    - 'blue' 대신 'primary', 'red' 대신 'danger' 등

![0827_Bootstrap_2025-08-29-09-27-51](images/0827_Bootstrap_2025-08-29-09-27-51.png)

## Component

### Bootstrap Component
Bootstrap에서 제공하는 <mark>UI 관련 요소</mark>

![0827_Bootstrap_2025-08-29-15-50-30](images/0827_Bootstrap_2025-08-29-15-50-30.png)

- <mark>UI 관련 요소</mark>란 버튼, 네비게이션 바, 카드, 폼, 드랍다운 등을 의미함

### Component 이점
- 일관된 디자인을 제공하여 웹 사이트의 구성 요소를 구축하는데 유용하게 활용

### 대표 컴포넌트 사용해보기
- Alerts
- Badges
- Cards
- Navbar

![0827_Bootstrap_2025-08-29-15-51-32](images/0827_Bootstrap_2025-08-29-15-51-32.png)

- Component의 동작은 JavaScript를 활용해서 만들어짐
- 만약 동작이 잘 되지 않을 경우, 다음을 확인해 본다.
    - Bootstrap의 \<script> 요소를 잘 추가되어 있는지 확인
    - "data-*"로 시작하는 속성들이 잘 정의되어 있는지 확인

# Semantic Web
웹 데이터를 의미론적으로 구조화된 형태로 표현하는 방식

- 요소의 시각적 측면이 아닌 요소의 목적과 역할에 집중하는 방식

## Semantic in HTML

### HTML 요소가 의미를 가진다는 것
- 외형보다는 요소 자체의 의미에 집중하는 것

![0827_Bootstrap_2025-08-29-15-58-58](images/0827_Bootstrap_2025-08-29-15-58-58.png)

### HTML Semantic Element
기본적인 모양과 기능 이외의 의미를 가지는 HTML 요소

- 검색엔진 및 개발자가 웹 페이지의 콘텐츠를 이해하기 쉽게 해준다.

### HTML Semantic Element 예시
- header
    - 소개 및 탐색에 도움을 주는 콘텐츠
- nav
    - 현재 페이지 내, 또는 다른 페이지로의 링크를 보여주는 구획
- main
    - 문서의 주요 콘텐츠
- article
    - 독립적으로 구분해 배포하거나 될 수 있는 구성의 콘텐츠 구획
- section
    - 문서의 독립적인 구획
    - 더 적합한 요소가 없을 때 사용
- aside
    - 문서의 주요 내용과 간접적으로만 연관된 부분
- footer
    - 가장 가까운 조상 구획(main, article 등)의 작성자, 저작권 정보, 관련 문서

![0827_Bootstrap_2025-08-29-16-02-54](images/0827_Bootstrap_2025-08-29-16-02-54.png)

---
- Semantic 요소가 브라우저에 보여질 때는 div 요소와 똑같이 나오게 된다.
---

## Semantic in CSS

### CSS 방법론
CSS를 효율적이고 유지 보수가 용이하게 작성하기 위한 일련의 가이드라인

### OOCSS(Object Oriented CSS)
객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론

- 다음과 같은 순서로 진행함
    1. 구조와 스킨을 분리
    2. 컨테이너와 콘텐츠를 분리

### 1. 구조와 스킨 분리
- 구조와 스킨을 분리함으로써 가능성을 높임

![0827_Bootstrap_2025-08-29-16-07-51](images/0827_Bootstrap_2025-08-29-16-07-51.png)

![0827_Bootstrap_2025-08-29-16-07-57](images/0827_Bootstrap_2025-08-29-16-07-57.png)

### 2. 컨테이너와 콘텐츠를 분리
- 객체에 직접 적용하는 대신 객체를 둘러싸는 컨테이너에 스타일을 적용
- 스타일을 정의할 때 위치에 의존적인 스타일을 사용하지 않도록 함
- 콘텐츠를 다른 컨테이너로 이동시키거나 재배치할 때 스타일이 깨지는 것을 방지
---
- Bootstrap의 미디어 객체(Utilities > Flex > Media object)는 컨테이너와 콘텐츠 분리 원칙을 잘 보여주는 예시이다.
---
### OOCSS 적용 예시
- 변경 전
    - .header와 .footer 클래스가 폰트 크기와 색 둘 다 영향을 주고 있음

![0827_Bootstrap_2025-08-29-16-10-55](images/0827_Bootstrap_2025-08-29-16-10-55.png)

- 변경 후
    - .container .title은 폰트 크기 담당 (콘텐츠 스타일)
    - .header와 .footer는 폰트 색 담당 (컨테이너 스타일)

![0827_Bootstrap_2025-08-29-16-11-34](images/0827_Bootstrap_2025-08-29-16-11-34.png)

![0827_Bootstrap_2025-08-29-16-11-54](images/0827_Bootstrap_2025-08-29-16-11-54.png)

# 참고

## Bootstrap을 사용하는 이유
- 가장 많이 사용되는 CSS 프레임워크
- 사전에 디자인된 다양한 컴포넌트 및 기능
    - 빠른 개발과 유지보수
- 손쉬운 반응형 웹 디자인 구현
- 커스터마이징(customizing)이 용이
- 크로스 브라우징(Cross browsing) 지원
    - 모든 주요 브라우저에서 작동하도록 설계되어 있음

## CDN 없이 사용하기

### Bootstrap 코드 파일을 다운받아 활용
1. Bootstrap 코드 파일 다운로드
    - https://getbootstrap.com/docs/5.3/getting-started/download/
2. bootstrap.css 와 bootstrap.bundle.js 만 선택
3. CSS 파일은 HTML head 태그에 가져와서 사용
4. JS 파일은 HTML body 태그에 가져와서 사용

> 파일 별 포함된 기능이 다르므로 공식 문서를 통해 확인
    - https://getbootstrap.com/docs/5.3/getting-started/contents/

- 파일 배치 및 불러오기 코드 예시

![0827_Bootstrap_2025-08-29-16-23-12](images/0827_Bootstrap_2025-08-29-16-23-12.png)

## 의미론적 마크업

### 의미론적인 마크업이 필요한 이유
- "검색엔진 최적화(SEO)"
    - 검색 엔진이 해당 웹 사이트를 분석하기 쉽게 만들어 검색 순위에 영향을 줌
- "웹 접근성(Web Accessibility)"
    - 웹 사이트, 도구, 기술이 고령자나 장애를 가진 사용자들이 사용할 수 있도록 설계 및 개발하는 것
    - ex) 스크린 리더를 통해 전맹 시각장애 사용자에게 웹의 글씨를 읽어줌
    - https://nuli.navercorp.com/

### 책임과 역할

#### HTML
콘텐츠의 구조와 의미

#### CSS
레이아웃과 디자인

### 실습
- Bootstrap 활용
    - 2622. Bootstrap Class 활용, 컴포넌트 만들기
    - 2628. Bootstrap 활용, 로그인 화면 구현
    - 2627. Bootstrap 종합 실습, 웹페이지 만들기 1
    - 2630. Bootstrap 종합 실습, 웹페이지 만들기 2
- Semantic Web
    - 2980. 시멘틱 태그와 OOCSS

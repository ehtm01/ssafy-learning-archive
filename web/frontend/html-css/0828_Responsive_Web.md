# Bootstrap Grid system
웹 페이지의 <u>레이아웃</u>을 조정하는데 사용되는 **12개의 컬럼**(세로로 12개의 칸)으로 구성된 시스템

- 반응형 디자인을 지원해 웹 페이지를 모바일, 태블릿, 데스크탑 등 다양한 기기에서 적절하게 표시할 수 있도록 도와줌
---
**12칸으로 나눈 이유**
- 약수가 많다. (1, 2, 3, 4, 6, 12)
- 그래서 다양한 조합의 숫자를 배치할 수 있기 때문이다.

---
### 반응형 웹 디자인(Responsive Web Design)
디바이스 종류나 화면 크기에 상관없이, 어디서든 일관된 레이아웃 및 사용자 경험을 제공하는 디자인 기술

- 32인치 모니터, 태블릿, 스마트폰 등 화면 크기에 따라 요소의 배치를 변경하여 일관된 사용자 경험을 제공할 수 있음

### 12개의 컬럼 사용 예시
- 12칸 중 크기에 따라 필요한 만큼의 컬럼을 차지하게 요소를 배치
    - 내부의 요소도 12칸으로 나눠서 활용

![0828_Responsive_Web_2025-08-28-09-16-06](images/0828_Responsive_Web_2025-08-28-09-16-06.png)

## Grid system 구조

### Grid system 기본 요소
- Container
    - Column들을 담고 있는 공간

![0828_Responsive_Web_2025-08-28-09-19-51](images/0828_Responsive_Web_2025-08-28-09-19-51.png)

- Column
    - 실제 컨텐츠를 포함하는 부분

![0828_Responsive_Web_2025-08-28-09-20-48](images/0828_Responsive_Web_2025-08-28-09-20-48.png)

- Gutter
    - 컬럼과 컬럼 사이의 여백 영역(상하좌우)
    - 컬럼간의 padding, margin 조절

![0828_Responsive_Web_2025-08-28-09-20-59](images/0828_Responsive_Web_2025-08-28-09-20-59.png)

- 1개의 row 안에 12개의 column 영역이 구성
    - 각 요소는 12개 중 몇 개를 차지할 것인지 지정됨

![0828_Responsive_Web_2025-08-28-09-31-39](images/0828_Responsive_Web_2025-08-28-09-31-39.png)

## Grid system 실습

### Grid System 실습 - 기본
- 다음과 같이 12칸을 분배해보자.

    ![0828_Responsive_Web_2025-08-28-09-32-10](images/0828_Responsive_Web_2025-08-28-09-32-10.png)

    - 첫 번째 줄

    ![0828_Responsive_Web_2025-08-28-09-41-32](images/0828_Responsive_Web_2025-08-28-09-41-32.png)

    ![0828_Responsive_Web_2025-08-28-09-33-20](images/0828_Responsive_Web_2025-08-28-09-33-20.png)

    - 두 번째 줄

    ![0828_Responsive_Web_2025-08-28-09-41-25](images/0828_Responsive_Web_2025-08-28-09-41-25.png)

    ![0828_Responsive_Web_2025-08-28-09-34-10](images/0828_Responsive_Web_2025-08-28-09-34-10.png)

    - 세 번째 줄

    ![0828_Responsive_Web_2025-08-28-09-41-16](images/0828_Responsive_Web_2025-08-28-09-41-16.png)

    ![0828_Responsive_Web_2025-08-28-09-40-56](images/0828_Responsive_Web_2025-08-28-09-40-56.png)

---
**\* class box는 컬럼의 영역을 보기 위해 직접 작성한 CSS 스타일을 적용하기 위해 작성한 것이며, Bootstrap Grid system과 관련 없다.**

![0828_Responsive_Web_2025-08-28-09-42-26](images/0828_Responsive_Web_2025-08-28-09-42-26.png)

---
### Grid System 실습 - 중첩(Nesting)
- 하나의 Column에 또다른 Row를 넣어보자.

![0828_Responsive_Web_2025-08-28-09-44-12](images/0828_Responsive_Web_2025-08-28-09-44-12.png)

![0828_Responsive_Web_2025-08-28-09-44-25](images/0828_Responsive_Web_2025-08-28-09-44-25.png)

![0828_Responsive_Web_2025-08-28-09-44-43](images/0828_Responsive_Web_2025-08-28-09-44-43.png)

### Grid System 실습 - 상쇄(Offset)
- Offset으로 Column을 생략해보자.

![0828_Responsive_Web_2025-08-28-09-45-41](images/0828_Responsive_Web_2025-08-28-09-45-41.png)

![0828_Responsive_Web_2025-08-28-09-48-52](images/0828_Responsive_Web_2025-08-28-09-48-52.png)

![0828_Responsive_Web_2025-08-28-09-51-27](images/0828_Responsive_Web_2025-08-28-09-51-27.png)

### Gutters
- Grid system에서 column 사이에 여백 영역
    - x축은 padding, y축은 margin으로 여백 생성

![0828_Responsive_Web_2025-08-28-09-52-14](images/0828_Responsive_Web_2025-08-28-09-52-14.png)

---
**\* 실제 컬럼 간에 좌우 간격(x축)은 변하지 않고, padding으로 인해 컬럼 안에 contents의 너비가 변함. (col 사이 공간이 생긴 것처럼 보임)**

**\*좌우는 제한이 있어 제한을 넘길 수 없기에 margin으로 밀 수 없다.**

---
### Grid System 실습 - gutters
- Gutter를 이용해 간격을 조정해보자.
    - gx-0
    - col 사이 여백 제거

    ![0828_Responsive_Web_2025-08-28-09-58-59](images/0828_Responsive_Web_2025-08-28-09-58-59.png)

    ![0828_Responsive_Web_2025-08-28-09-59-09](images/0828_Responsive_Web_2025-08-28-09-59-09.png)

    - gy-5
    - row 사이 여백 증가

    ![0828_Responsive_Web_2025-08-28-09-59-39](images/0828_Responsive_Web_2025-08-28-09-59-39.png)

    ![0828_Responsive_Web_2025-08-28-09-59-52](images/0828_Responsive_Web_2025-08-28-09-59-52.png)

    - g-5

    ![0828_Responsive_Web_2025-08-28-10-00-10](images/0828_Responsive_Web_2025-08-28-10-00-10.png)

    ![0828_Responsive_Web_2025-08-28-10-00-19](images/0828_Responsive_Web_2025-08-28-10-00-19.png)

# Grid system for responsive web

### Responsive Web Design
디바이스 종류나 화면 크기에 상관없이, 어디서든 일관된 레이아웃 및 사용자 경험을 제공하는 디자인 기술

![0828_Responsive_Web_2025-08-28-10-14-43](images/0828_Responsive_Web_2025-08-28-10-14-43.png)

- Bootstrap grid system에서는 12개의 column과 **6개의 breakpoints**를 사용해서 반응형 웹 디자인 구현

## Grid system Breakpoints
- 웹 페이지를 다양한 화면 크기에서 적절하게 배치하기 위한 분기점
    - 화면 너비에 따라 6개의 분기점 제공(xs, sm, md, lg, xl, xxl)

![0828_Responsive_Web_2025-08-28-10-16-35](images/0828_Responsive_Web_2025-08-28-10-16-35.png)

- 각 breakpoints 마다 설정된 최대 너비 값 **"이상으로"** 화면이 커지면 grid system 동작이 변경됨

## Breakpoints 실습
- 화면 사이즈가 변함에 따라 column의 배치를 바꿔보자.

    ![0828_Responsive_Web_2025-08-28-10-19-42](images/0828_Responsive_Web_2025-08-28-10-19-42.png)

    ![0828_Responsive_Web_2025-08-28-10-23-43](images/0828_Responsive_Web_2025-08-28-10-23-43.png)

    - Offset도 같이 사용해보자.

    ![0828_Responsive_Web_2025-08-28-10-24-15](images/0828_Responsive_Web_2025-08-28-10-24-15.png)

    ![0828_Responsive_Web_2025-08-28-10-24-28](images/0828_Responsive_Web_2025-08-28-10-24-28.png)

### 참고
- 실제 Bootstrap에 작성된 Grid system 코드
    - Media Query로 작성됨

![0828_Responsive_Web_2025-08-28-10-30-37](images/0828_Responsive_Web_2025-08-28-10-30-37.png)

- 결국 Grid System은 화면 크기에 따라 12개의 칸을 각 요소에 나눠주는 것

---
**\* Media Query는 장치의 크기나 특징에 따라 적용되는 스타일을 바꿀 수 있는 CSS의 기능이다.**

---
# CSS Layout 종합 정리

### 어떤 레이아웃 기술이 사용됐는지 생각해보자

![0828_Responsive_Web_2025-08-28-10-36-13](images/0828_Responsive_Web_2025-08-28-10-36-13.png)

- Grid System

![0828_Responsive_Web_2025-08-28-10-36-36](images/0828_Responsive_Web_2025-08-28-10-36-36.png)

- Flexbox

![0828_Responsive_Web_2025-08-28-10-36-58](images/0828_Responsive_Web_2025-08-28-10-36-58.png)

- Position

![0828_Responsive_Web_2025-08-28-10-37-11](images/0828_Responsive_Web_2025-08-28-10-37-11.png)

- CSS 레이아웃 기술들은 각각 고유한 특성과 장단점을 가지고 있음
- 이들은 상호 보완적이며, 특정 상황에 따라 적합한 도구가 달라짐
- 최적의 기술을 선택하고 효과적으로 활용하기 위해서는 다양한 실제 개발 경험이 필수적

# UX & UI

## UX(User Experience)
제품이나 서비스를 사용하는 사람들이 느끼는 전체적인 경험과 만족도를 개선하고 최적화하기 위한 디자인과 개발 분야

### <u>UX</u> 예시

![0828_Responsive_Web_2025-08-28-10-40-52](images/0828_Responsive_Web_2025-08-28-10-40-52.png)

- 백화점 1층에서 느껴지는 좋은 향수 향기
- 러쉬 매장 근처만 가도 맡을 수 있는 러쉬 향기
- 원하는 음악을 검색할 때, 검색 기능이 적절하게 작동하고 검색 결과가 정확하게 나오는 것

### UX 설계
- 사람들의 마음과 생각을 이해하고 정리해서 제품에 녹여내는 과정
- 유저 리서치, 데이터 설계 및 정제, 유저 시나리오, 프로토타입 설계

---
**\* 프로토타입(Prototype)은 제품 개발 전 실제 작동 방식을 미리 보고 검증하기 위한 초기 모델이다.

---
## UI(User Interface)
서비스와 사용자 간의 상호작용을 가능하게 하는 디자인 요소들을 개발하고 구현하는 분야

### <u>UI</u> 예시

![0828_Responsive_Web_2025-08-28-10-49-18](images/0828_Responsive_Web_2025-08-28-10-49-18.png)

- 리모컨
    - 사용자가 버튼을 누르면 TV가 켜지고, 채널 변경과 볼륨 조절 가능
- ATM
    - 사용자가 터치스크린을 통해 사용자 정보를 입력, 원하는 금액 선택 가능
- 웹 사이트
    - 사용자가 로그인 버튼을 누르면 이동하는 화면의 디자인 및 레이아웃

### UI 설계
- 예쁜 디자인보다는 사용자가 더 쉽고 편리하게 사용할 수 있도록 고려
- 이를 위해서는 디자인 시스템, 중간 산출물, 프로토타입 등이 필요

### 디자이너와 기획자 그리고 개발자
- 많은 회사에서 UX/UI 디자인을 함께하는 디자이너를 채용하거나 UX는 기획자, UI는 디자이너의 역할로 채용하기도 함
---
- UX (직무: UX Researcher, User Researcher)
    - 구글: 사용자의 경험을 이해하기 위한 통계 모델을 설계
    - MS: 리서치를 기획하고 사용자에 대한 지표를 정의
    - Meta: 정성적인 방법과 정량적인 방법을 사용해서 사용자 조사 실시
- UI (직무: Product Designer, Interaction Designer)
    - 구글: 다양한 디자인 프로토타이핑 툴을 사용해서 개발 가이드를 제공
    - MS: 시각 디자인을 고려해서 체계적인 디자인 컨셉을 보여줌
    - Meta: 제품을 이해하고 더 나은 UI Flow와 사용자 경험을 디자인

### 만약 기능만을 생각한다면...

![0828_Responsive_Web_2025-08-28-10-54-17](images/0828_Responsive_Web_2025-08-28-10-54-17.png)

- UI 디자인은 깔끔하게 되었지만, UX를 고려하지 않음
- 사용자들은 잔디밭 위로 지름길을 만들어서 이용하게 됨

# 참고

## The Grid System
- CSS가 아닌 편집 디자인에서 나온 개념으로 구성 요소를 잘 배치해서 시각적으로 좋은 결과물을 만들기 위함
- 기본적으로 안쪽에 있는 요소들의 오와 열을 맞추는 것에서 기인
- 정보 구조와 배열을 체계적으로 작성하여 정보의 질서를 부여하는 시스템

## Grid cards
- row-cols 클래스를 사용하여 행당 표시할 열(카드) 수를 손쉽게 제어할 수 있음

![0828_Responsive_Web_2025-08-28-10-56-08](images/0828_Responsive_Web_2025-08-28-10-56-08.png)

```html
<div class="container">
    <div class="row row-cols-1 row-cols-sm-3 row-cols-md-2 g-4">
      <div class="col">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">...</p>
          </div>
        </div>
      </div>
      <div class="col">...</div>
      <div class="col">...</div>
      <div class="col">...</div>
    </div>
  </div>
```

## UI Design Guidelines

### 기업별 UI Design Guidelines
- 삼성 (One UI)
- 애플 (Design guide)
- 구글 (Material Design)

### Can't Unsee
- https://cantunsee.space/
    - 더 나은 UX/UI를 고민해볼 수 있는 웹 게임

![0828_Responsive_Web_2025-08-28-11-01-21](images/0828_Responsive_Web_2025-08-28-11-01-21.png)

### 실습
- Bootstrap Grid system
    - 3212. 음악 스트리밍 서비스 - 마크업
    - 3213. 음악 스트리밍 - 음악 목록
- Grid system for responsive web
    - 3210. grid card를 활용한 도서 구매 시스템
    - 3211. 반응형 소셜 커머스 페이지
    - 3016. 여행 블로그 만들기 - Navigation Bar
    - 3017. 여행 블로그 만들기 - 목록 화면 구성

# CSS Box Model

## display 속성(박스의 화면 배치 방식)

### 박스 타입
- 박스 타입에 따라 페이지에서의 배치 흐름 및 다른 박스와 관련하여 박스가 동작하는 방식이 달라짐

### 박스 타입 종류
1. Block 타입
2. Inline 타입

### block 타입
블록 타입은 하나의 독립된 덩어리처럼 동작하는 요소

![0826_CSS_Layout_2025-08-26-09-06-26](images/0826_CSS_Layout_2025-08-26-09-06-26.png)

- 항상 새로운 행으로 나뉨 (한 줄 전체를 차지, 너비 100%)
- width, height, margin, padding 속성을 모두 사용할 수 있음
- padding, margin, border로 인해 다른 요소를 상자로부터 밀어냄
- width 속성을 지정하지 않으면 박스는 inline 방향으로 사용 가능한 공간을 모두 차지함
    - 상위 컨테이너 너비 100%로 채우는 것
- 대표적인 block 타입 태그
    - h1~6, p, div, ul, li

### block 타입의 대표: div
- 다른 HTML 요소들을 그룹화하여 레이아웃을 구성하거나 스타일링을 적용할 수 있음
- 헤더, 푸터, 사이드바 등 웹 페이지의 다양한 섹션을 구조화하는데 가장 많이 쓰이는 요소

![0826_CSS_Layout_2025-08-26-09-09-54](images/0826_CSS_Layout_2025-08-26-09-09-54.png)

### inline 타입
문장 안의 단어처럼 흐름에 따라 자연스럽게 배치되는 요소

![0826_CSS_Layout_2025-08-26-09-11-48](images/0826_CSS_Layout_2025-08-26-09-11-48.png)

- 줄바꿈이 일어나지 않음 (콘텐츠의 크기만큼만 영역을 차지)
- width와 height 속성을 사용할 수 없음
- 수직 방향 (상하)
    - padding, margin, border가 적용되지만, 다른 요소를 밀어낼 수는 없음
- 수평 방향 (좌우)
    - padding, margin, border가 적용되어 다른 요소를 밀어낼 수 있음
- 대표적인 inline 타입 태그
    - a, img, span, strong

### inline 타입의 대표: span
- 자체적으로 시각적 변화 없음
    - 스타일을 적용하기 전까지는 특별한 변화 없음
- 텍스트 일부 조작
    - 문장 내 특정 단어나 구문에만 스타일을 적용할 때 유용
- 블록 요소처럼 줄바꿈을 일으키지 않으므로, 문서의 구조에 큰 변화를 주지 않음

```html
<p>이 문장에서 <span style="color: blue;">파란색</span> 단어만 색상이 다릅니다.</p>
<p>이 단어는 <span class="highlight-text">강조</span>되었습니다.</p>
<p>이것은 <span id="changeText">클릭</span>하면 변경됩니다.</p>
```

![0826_CSS_Layout_2025-08-26-09-21-28](images/0826_CSS_Layout_2025-08-26-09-21-28.png)

## Normal flow
일반적인 흐름 또는 레이아웃을 변경하지 않은 경우 웹 페이지 요소가 배치되는 방식

- 워드(Word) 문서를 예로 들면
- 엔터를 눌러 문단을 나누는 것이 block 요소의 배치 방식
- 엔터를 누르지 않고 계속 타이핑하는 것이 inline 요소의 배치 방식

### Normal flow 예시
- 블록은 한 줄 전체를, 인라인은 콘텐츠만큼의 공간만 차지하며 줄을 바꾸지 않음

![0826_CSS_Layout_2025-08-26-09-24-18](images/0826_CSS_Layout_2025-08-26-09-24-18.png)

## 기타 display 속성

### inline-block 타입
inline과 block의 특징을 모두 가진 특별한 display 속성 값

- inline-block 타입은 '줄 서 있는 사람들'과 같다
- 각 사람은 한 줄로 나란히 서 있지만(inline)
- 사람마다 키와 덩치가 다르지만, 각자 공간을 가지고 있다(block).

```css
.index {
    display: inline-block;
}
```

- Block과 Inline의 특징을 합친 것 (줄바꿈 없이, 크기 지정 간으)
- width 및 height 속성 사용 가능
- padding, margin 및 border로 인해 다른 요소가 상자에서 밀려남
---
- 주로 가로로 정렬된 네비게이션 메뉴나 여러 개의 버튼, 이미지 갤러리처럼 수평으로 나열하면서, 각 항목의 크기를 직접 제어하고 싶을 때 매우 유용하게 사용됨

### inline-block 타입 예시

![0826_CSS_Layout_2025-08-26-09-34-45](images/0826_CSS_Layout_2025-08-26-09-34-45.png)

### none 타입
요소를 화면에 표시하지 않고, 공간조차 부여되지 않음

![0826_CSS_Layout_2025-08-26-09-35-05](images/0826_CSS_Layout_2025-08-26-09-35-05.png)

### none 타입 예시

![0826_CSS_Layout_2025-08-26-09-35-24](images/0826_CSS_Layout_2025-08-26-09-35-24.png)

# CSS position

### CSS Layout
- 각 요소의 **위치**와 **크기를 조정**하여 웹 페이지의 디자인을 결정하는 것
- 요소들을 상하좌우로 정렬하고, 간격을 맞추고, 전체적인 페이지의 뼈대를 구성
- 핵심 속성: display(block, inline, flex, grid, ...)

### CSS Position
- 요소를 Normal Flow에서 제거하여 **다른 위치로 배치**하는 것
- 다른 요소 위에 올리기, 화면의 특정 위치에 고정시키기 등
- 핵심 속성: position(static, relative, absolute, fixed, sticky, ...)

### Position 이동 방향
- 네 가지 방향 속성(상, 하, 좌, 우)를 이용해 요소의 위치를 조절할 수 있음
- 겹치는 요소의 쌓이는 순서를 조절할 수 있음

![0826_CSS_Layout_2025-08-26-09-38-07](images/0826_CSS_Layout_2025-08-26-09-38-07.png)

## Position 유형

![0826_CSS_Layout_2025-08-26-09-40-26](images/0826_CSS_Layout_2025-08-26-09-40-26.png)

### Position: static
- 요소를 Normal Flow에 따라 배치
- top, right, bottom, left 속성이 적용되지 않음
- 기본 값

```css
.static {
    position: static;
    background-color: lightcoral;
}
```

### Position: relative
- 요소를 Normal Flow에 따라 배치
- 자신의 원래 위치(static)을 기준으로 이동
- top, right, bottom, left 속성으로 위치를 조정
- 다른 요소의 레이아웃에 영향을 주지 않음<br>(요소가 차지하는 공간은 static일 때와 같음)

```css
.relative {
    position: relative;
    background-color: lightblue;
    top: 100px;
    left: 100px;
}
```

### Position: absolute
- 요소를 Normal Flow에서 제거
- 가장 가까운 relative 부모 요소를 기준으로 이동
    - 만족하는 부모 요소가 없다면 body 태그를 기준으로 함
- top, right, bottom, left 속성으로 위치를 조정
- 문서에서 요소가 차지하는 공간이 없어짐

```css
.absolute {
    position: absolute;
    background-color: lightgreen;
    top: 100px;
    left: 100px;
}
```

### Position: fixed
- 요소를 Normal Flow에서 제거
- 현재 화면영역(viewport)을 기준으로 이동
- 스크롤해도 항상 같은 위치에 유지됨
- top, right, bottom, left 속성으로 위치를 조정
- 문서에서 요소가 차지하는 공간이 없어짐

```css
.fixed {
    position: fixed;
    background-color: gray;
    top: 0;
    right: 0;
}
```

### Position: sticky
- relative와 fixed의 특성을 결합한 속성
- 스크롤 위치가 임계점에 도달하기 전에는 relative처럼 동작
- 스크롤 위치가 임계점에 도달하면 fixed처럼 화면에 고정
- 다음 stick 요소가 나오면 이전 sticky 요소의 자리를 대체
    - 이전 sticky 요소와 다음 sticky 요소의 위치가 겹치게 되기 때문

![0826_CSS_Layout_2025-08-26-10-16-46](images/0826_CSS_Layout_2025-08-26-10-16-46.png)

### Position absolute 활용

![0826_CSS_Layout_2025-08-26-10-17-30](images/0826_CSS_Layout_2025-08-26-10-17-30.png)

## z-index
요소의 쌓임 순서를 정의하는 속성

![0826_CSS_Layout_2025-08-26-10-20-50](images/0826_CSS_Layout_2025-08-26-10-20-50.png)

- 정수 값을 사용해 Z축 순서를 지정
- 값이 클 수록 요소가 위에 쌓이게 됨
- static이 아닌 요소에만 적용됨
- 기본값은 auto 로 부모 요소의 z-index 값에 영향을 받음
- 같은 부모 내에서만 z-index 값을 비교하고, 값이 같으면 HTML 문서 순서대로 쌓임
- 부모의 z-index가 낮으면 자식의 z-index가 아무리 높아도 부모보다 위로 올라갈 수 없음
---
- position 속성이 static(기본값)이 아닌 요소에만 z-index가 적용됨
- 음수 z-index 값은 요소를 부모 요소의 뒤(배경)로 보낼 때 사용

### z-index 예시

![0826_CSS_Layout_2025-08-26-10-22-50](images/0826_CSS_Layout_2025-08-26-10-22-50.png)

# CSS Flexbox

### 박스 표시(Display) 타입
1. Outer display 타입
    - <u>block 타입</u>
    - <u>inline 타입</u>
2. Inner display 타입
    - 박스 내부의 요소들이 어떻게 배치될 지를 결정
    - CSS Flexbox(속성: flex)

### CSS Flexbox
요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식

![0826_CSS_Layout_2025-08-26-10-26-46](images/0826_CSS_Layout_2025-08-26-10-26-46.png)

> '공간 배열' & '정렬'

![0826_CSS_Layout_2025-08-26-10-27-36](images/0826_CSS_Layout_2025-08-26-10-27-36.png)

## Flexbox 구성 요소
- main axis
- cross axis
- flex container
- flex item

![0826_CSS_Layout_2025-08-26-10-28-13](images/0826_CSS_Layout_2025-08-26-10-28-13.png)

### main axis (주 축)
- flex item들이 배치되는 기본 축
- main start에서 시작하여 main end 방향으로 배치 (기본 값)

![0826_CSS_Layout_2025-08-26-10-29-26](images/0826_CSS_Layout_2025-08-26-10-29-26.png)

### cross axis (교차 축)
- main axis에 수직인 축
- cross start에서 시작하여 cross end 방향으로 배치 (기본 값)

![0826_CSS_Layout_2025-08-26-10-30-05](images/0826_CSS_Layout_2025-08-26-10-30-05.png)

### Flex Container
- display: flex; 혹은 display: inline-flex; 가 설정된 부모 요소
- 이 컨테이너의 1차 자식 요소들이 Flex Item이 됨
- flexbox 속성 값들을 사용하여 자식 요소 Flex Item들을 배치하는 주체

![0826_CSS_Layout_2025-08-26-10-31-17](images/0826_CSS_Layout_2025-08-26-10-31-17.png)

### Flex Item
- Flex Container 내부에 레이아웃 되는 항목
- 이후 배우는 내용을 이용해 자유로운 순서 변경 및 정렬 가능

![0826_CSS_Layout_2025-08-26-10-31-56](images/0826_CSS_Layout_2025-08-26-10-31-56.png)

## Flexbox 속성

### 1. Flex Container 지정
- display 속성을 flex 로 설정하면, Flex Container로 지정됨
- flex item은 기본적으로 행(주 축의 기본값인 가로 방향)으로 나열
- flex item은 주 축의 시작 선에서 시작
- flex item은 교차 축의 크기를 채우기 위해 늘어남

![0826_CSS_Layout_2025-08-26-10-35-59](images/0826_CSS_Layout_2025-08-26-10-35-59.png)

### 2. flex-direction
- flex item이 **나열되는 방향을 지정**
- 속성
    - row(기본값): 아이템을 가로 방향으로, 왼쪽에서 오른쪽으로 배치
    - column: 아이템을 세로 방향으로, 위에서 아래로 배치
    - "-reverse"로 지정하면 flex item 배치의 시작 선과 끝 선이 서로 바뀜

![0826_CSS_Layout_2025-08-26-10-37-51](images/0826_CSS_Layout_2025-08-26-10-37-51.png)

### 3. flex-wrap
- flex item 목록이 flex container의 한 행에 들어가지 않을 경우, **다른 행에 배치할지 여부 설정**
- 속성
    - nowrap(기본 값): 줄 바꿈을 하지 않음
    - wrap: 여러 줄에 걸쳐 배치될 수 있게 설정

![0826_CSS_Layout_2025-08-26-10-39-35](images/0826_CSS_Layout_2025-08-26-10-39-35.png)

### 4. justify-content
- 주 축을 따라 flex item 들을 정렬하고 간격을 조정
- 속성
    - flex-start(기본값): 주 축의 시작점으로 정렬
    - center: 주 축의 중앙으로 정렬
    - flex-end: 주 축의 끝점으로 정렬

![0826_CSS_Layout_2025-08-26-10-40-57](images/0826_CSS_Layout_2025-08-26-10-40-57.png)

### 5. align-content
- 컨테이너에 여러 줄의 flex item이 있을 때, 그 줄들 사이의 공간을 어떻게 분배할지 지정
    - flex-wrap이 wrap 또는 wrap-reverse로 설정된 여러 행에만 적용됨
    - Flex 아이템이 두 줄 이상일 때만 의미가 있음 (flex-wrap이 nowrap으로 설정된 경우)
- 속성
    - stretch(기본값): 여러 줄을 교차 축에 맞게 늘려 빈 공간을 채움
    - center: 여러 줄을 교차 축의 중앙에 맞춰 정렬
    - flex-start: 여러 줄을 교차 축의 시작점(보통 위쪽)에 맞춰 정렬
    - flex-end: 여러 줄을 교차 축의 끝점(보통 아래쪽)에 맞춰 정렬

![0826_CSS_Layout_2025-08-26-10-44-31](images/0826_CSS_Layout_2025-08-26-10-44-31.png)

### 6. align-items
- 컨테이너 안에 있는 flex item 들의 **교차 축 정렬** 방법을 지정
- 속성
    - stretch(기본값): 아이템을 교차 축 높이를 꽉 채우도록 늘어남
    - center: 아이템을 교차 축의 중앙에 맞춰 정렬
    - flex-start: 아이템을 교차 축의 시작점(가로 방향일 경우 위쪽)에 맞춰 정렬
    - flex-end: 아이템을 교차 축의 끝점(가로 방향일 경우 아래쪽)에 맞춰 정렬

![0826_CSS_Layout_2025-08-26-10-46-55](images/0826_CSS_Layout_2025-08-26-10-46-55.png)

### 7. align-self
- 컨테이너 안에 있는 flex item 들을 교차 축을 따라 개별적으로 정렬
- 속성
    - auto(기본값): 부모 컨테이너의 <u>align-items</u> 속성 값을 상속
    - stretch: 해당 아이템만 교차 축 방향으로 늘어나 컨테이너를 꽉 채우도록 정렬
    - center: 해당 아이템만 교차 축의 중앙에 정렬
    - flex-start: 해당 아이템만 교차 축의 시작점(가로 방향일 경우 위쪽)에 정렬
    - flex-end: 해당 아이템만 교차 축의 끝점(가로 방향일 경우 아래쪽)에 정렬
    
![0826_CSS_Layout_2025-08-26-10-49-18](images/0826_CSS_Layout_2025-08-26-10-49-18.png)

### 목적에 따른 속성 분류
- 배치 (flex-direction, flex-wrap)
- 공간 분배 (justify-content, align-content)
- 정렬 (align-items, align-self)

### 속성 쉽게 이해하는 방법
- justify - 주축
- align - 교차 축
---
**justify-items 및 justify-self 속성이 없는 이유는?**
- 애초에 필요가 없음
- 간단하게 margin auto를 통해 정렬 및 배치가 가능

### 8. flex-grow
- 남는 행 여백을 비율에 따라 각 flex item에 분배
- flex item이 컨테이너 내에서 확장하는 비율을 지정

![0826_CSS_Layout_2025-08-26-10-52-32](images/0826_CSS_Layout_2025-08-26-10-52-32.png)

---
#### flex-shrink
- flex-grow의 반대되는 개념
- 컨테이너의 공간이 부족할 때, flex item이 줄어드는 비율을 지정하는 속성
---
- 남는 여백을 각 flex item의 비율만큼 추가

![0826_CSS_Layout_2025-08-26-10-54-00](images/0826_CSS_Layout_2025-08-26-10-54-00.png)

### flex-basis
- flex item의 초기 크기 값을 지정
- flex-basis와 width 값을 동시에 적용한 경우 flex-basis가 우선

![0826_CSS_Layout_2025-08-26-10-55-40](images/0826_CSS_Layout_2025-08-26-10-55-40.png)

## flex-wrap 응용

### 반응형 레이아웃 작성
- 다양한 디바이스와 화면 크기에 자동으로 적응하여 콘텐츠를 최적으로 표시하는 웹 레이아웃 방식
- flex-wrap을 사용해 반응형 레이아웃 작성 (flex-grow & flex-basis 활용)

![0826_CSS_Layout_2025-08-26-10-56-36](images/0826_CSS_Layout_2025-08-26-10-56-36.png)

1. .card 요소를 flex 컨테이너로 설정
2. 컨테이너의 공간이 부족할 경우, 여러 줄로 나뉘어 배치되도록 허용
3. 각 flex item의 기본 너비를 설정
4. 컨테이너에 여유 공간이 있을 때 공간을 차지하며 늘어날 수 있도록 함<br>(두 flex item 모두 값이 1이므로 절반씩 나눠가짐)

![0826_CSS_Layout_2025-08-26-10-58-01](images/0826_CSS_Layout_2025-08-26-10-58-01.png)

# 참고

## 마진 상쇄(Margin collapsing)
- 두 block 타입 요소의 martin top과 bottom이 만나 더 큰 margin으로 결합되는 현상

![0826_CSS_Layout_2025-08-26-11-01-48](images/0826_CSS_Layout_2025-08-26-11-01-48.png)

## Margin collapsing (마진 상쇄) 예시
- 두 요소 모두 margin 20px이지만 실제 두 요소의 상/하 공간은 40이 아닌 20으로 상쇄

![0826_CSS_Layout_2025-08-26-11-02-47](images/0826_CSS_Layout_2025-08-26-11-02-47.png)

---
**Margin collapsing (마진 상쇄) 이유**
- 복잡한 레이아웃에서 요소 간 간격을 일관되게 유지 가능(일관성)
- 요소 간의 간격을 더 예측 가능하고 관리하기 쉽게 만들 수 있음(단순성)

## 박스 타입 별 수평 정렬

### Block 요소의 수평 정렬
- margin: auto 사용
- 블록의 너비를 지정하고 좌우 마진을 auto로 설정

```html
<div class="box margin-auto">
</div>
```

```css
.box {
    width: 100px;
    height: 100px;
    background-color: crimson;
    border: 1px solid black;
}

.margin-auto {
    margin: 0 auto;
}
```

### Inline 요소의 수평 정렬
- text-align 사용
- 부모 요소에 적용

```html
<div class="text-center">
    <span>inline 요소</span>
</div>
```

```css
.text-center {
    text-align: center;
}
```

### <u>Inline-block</u> 요소의 수평 정렬
- text-align 사용
- 부모 요소에 적용

```html
<div class="text-center">
    <div class="box inline-block"></div>
</div>
```

```css
.text-center {
    text-align: center;
}

.inline-block {
    display: inline-block;
}
```

## 실제 Position 활용 예시

### 실제 Position 활용 예시: absolute
- 특정 요소 위에 다른 요소를 겹쳐서 배치할 때 유용하게 사용됨

![0826_CSS_Layout_2025-08-26-11-23-18](images/0826_CSS_Layout_2025-08-26-11-23-18.png)

### 실제 Position 활용 예시: fixed
- 페이지를 스크롤해도 항상 같은 자리에 표시되는 요소를 만들 때 사용

![0826_CSS_Layout_2025-08-26-11-24-03](images/0826_CSS_Layout_2025-08-26-11-24-03.png)

### 실제 Position 활용 예시: sticky
- 일반적인 문서 흐름에 따라 배치되다가, 스크롤이 특정 위치에 도달하면 고정되는 속성

![0826_CSS_Layout_2025-08-26-11-25-24](images/0826_CSS_Layout_2025-08-26-11-25-24.png)

## Flexbox Shorthand 속성

### Shorthand: "flex-flow"
- <u>flex-direction</u>과 <u>flex-wrap</u> 속성을 한 번에 지정할 수 있는 단축 속성

```css
/* 기본 속성 사용 시 */

.container {
    flex-flow: flex-direction flex-wrap
}
```

```css
/* 단축 속성 사용 시 */

.container {
    flex-direction: row;
    flex-wrap: wrap;
}
```

### shorthand: "flex"
- flex-grow, flex-shrink, flex-basis 속성을 한 번에 설정할 수 있는 단축 속성<br>(기본값으로는 1, 1, 0% 로 설정)

![0826_CSS_Layout_2025-08-26-11-30-38](images/0826_CSS_Layout_2025-08-26-11-30-38.png)

## Flexbox 속성 정리

### flex-direction
1. row(기본값): 아이템을 가로 방향으로, 왼쪽에서 오른쪽으로 배치
2. row-reverse: 아이템을 가로 방향으로, 오른쪽에서 왼쪽으로 배치
3. column: 아이템을 세로 방향으로, 위에서 아래로 배치
4. column-reverse: 아이템을 세로 방향으로, 아래에서 위로 배치

![0826_CSS_Layout_2025-08-26-11-31-55](images/0826_CSS_Layout_2025-08-26-11-31-55.png)

### flex-wrap
1. wrap: 여러 줄에 걸쳐 배치될 수 있게 설정
2. nowrap(기본값): 줄바꿈을 하지 않음

![0826_CSS_Layout_2025-08-26-11-32-26](images/0826_CSS_Layout_2025-08-26-11-32-26.png)

### justify-content
1. flex-start(기본값): 주 축의 시작점으로 정렬
2. flex-end: 주 축의 끝점으로 정렬
3. center: 주 축의 중앙으로 정렬
4. space-between: 첫 아이템은 시작점, 마지막 아이템은 끝점에 붙이고 아이템들 사이의 간격을 균등하게 배분
5. space-around: 각 아이템의 둘레(around)에 균등한 간격으로 배분. (양 끝 아이템은 절반의 간격이 설정)
6. space-evenly: 모든 아이템들 사이와 양 끝의 간격을 모두 동일하게 배분

![0826_CSS_Layout_2025-08-26-11-34-10](images/0826_CSS_Layout_2025-08-26-11-34-10.png)

### align-content
1. flex-start: 여러 줄을 교차 축의 시작점에 맞춰 정렬
2. flex-end: 여러 줄을 교차 축의 끝점(보통 아래쪽)에 맞춰 정렬
3. center: 여러 줄을 컨테이너의 중앙으로 정렬
4. space-between: 첫 줄은 시작점에, 마지막 줄은 끝점에 붙이고, 그 사이 줄들의 간격을 균등하게 배분
5. space-around: 각 줄의 위아래(around)에 균등한 간격을 배분 (컨테이너의 시작과 끝에는 절반의 간격이 설정)
6. space-evenly: 모든 줄들 사이와 양 끝의 간격을 모두 동일하게 배분

![0826_CSS_Layout_2025-08-26-11-36-10](images/0826_CSS_Layout_2025-08-26-11-36-10.png)

### align-items
1. stretch(기본값): 아이템이 교차 축 방향으로 늘어나 컨테이너를 꽉 채우도록 정렬
2. flex-start: 아이템을 교차 축의 시작점(가로 방향일 경우 위쪽)에 맞춰 정렬
3. flex-end: 아이템을 교차 축의 끝점(가로 방향일 경우 아래쪽)에 맞춰 정렬
4. center: 아이템을 교차 축 높이를 꽉 채우도록 늘어남

![0826_CSS_Layout_2025-08-26-11-37-22](images/0826_CSS_Layout_2025-08-26-11-37-22.png)

### align-self
1. stretch: 해당 아이템만 교차 축 방향으로 늘어나 컨테이너를 꽉 채우도록 정렬
2. flex-start: 해당 아이템만 교차 축의 시작점(가로 방향일 경우 위쪽)에 정렬
3. flex-end: 해당 아이템만 교차 축의 끝점(가로 방향일 경우 아래쪽)에 정렬
4. center: 해당 아이템만 교차 축의 중앙에 정렬

### 실습
- CSS Box Model
    - 2640. 프로필 카드 만들기
    - 3206. 도서 관리 서비스 - boxmodel
- CSS Position
    - 3012. CSS Position 속성 살펴보기
    - 3207. 도서 관리 서비스 - position
- CSS Flexbox
    - 3011. FlexBox 기본 구성
    - 3208. 도서 관리 서비스 - flexbox


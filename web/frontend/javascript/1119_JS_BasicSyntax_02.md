# 객체

### Object
- Object: 키로 구분된 데이터 집합을 저장하는 자료형 (data collection)

![1119_JS_BasicSyntax_02_2025-11-19-09-12-42](images/1119_JS_BasicSyntax_02_2025-11-19-09-12-42.png)

## 구조 및 속성

### 객체 구조
- 중괄호('{}')를 이용해 작성
- 중괄호 안에는 key: value 쌍으로 구성된 속성(property)를 여러 개 작성 가능
- key는 문자형만 허용
- value는 모든 자료형 허용

![1119_JS_BasicSyntax_02_2025-11-19-09-04-49](images/1119_JS_BasicSyntax_02_2025-11-19-09-04-49.png)

### 속성 참조
- 점('.') 표기법 또는 대괄호('[]') 표기법으로 객체 속성에 접근
- key 이름에 띄어쓰기 같은 구분자가 있으면 대괄호 접근만 가능

![1119_JS_BasicSyntax_02_2025-11-19-09-05-29](images/1119_JS_BasicSyntax_02_2025-11-19-09-05-29.png)

### 'in' 연산자
- 속성이 객체에 존재하는지 여부를 확인
- 객체의 키나 배열의 인덱스 존재 여부를 확인하는 연산자

![1119_JS_BasicSyntax_02_2025-11-19-09-07-31](images/1119_JS_BasicSyntax_02_2025-11-19-09-07-31.png)

#### TIP
- 객체에서 값의 포함 여부를 확인하려면 'in' 연산자 대신 'hasOwnProperty()' 메서드를 사용하는 것이 올바름
- 프로토타입 체인을 따라 상속된 속성까지 확인하므로, 의도치 않게 true가 나올 수 있어 주의
  - 프로토타입: 객체들이 기능을 물려받는 원본, 즉 '부모' 역할을 하는 객체
  - 프로토타입 체인: 자신에게 없는 속성이나 기능을 부모, 조상 순으로 찾아가는 것

## 메서드

### Method
- Method: 객체 속성에 정의된 함수
  - object.method() 방식으로 호출
  - 메서드는 객체가 '행동'할 수 있게 함

![1119_JS_BasicSyntax_02_2025-11-19-09-12-25](images/1119_JS_BasicSyntax_02_2025-11-19-09-12-25.png)

![1119_JS_BasicSyntax_02_2025-11-19-09-09-49](images/1119_JS_BasicSyntax_02_2025-11-19-09-09-49.png)

### Method 기본 문법
- 메서드도 값이 함수인 속성

![1119_JS_BasicSyntax_02_2025-11-19-09-10-19](images/1119_JS_BasicSyntax_02_2025-11-19-09-10-19.png)

- 메서드와 일반 함수의 차이는?
  - 메서드는 자신이 속한 객체의 다른 속성들에 접근할 수 있음
  - 이를 위한 방법이 this

## this

### 'this' keyword
- Method: 객체 속성에 정의된 함수
  - '**this**' 키워드를 사용해 객체 자신의 속성이나 메서드에 접근하여 특정 작업을 수행할 수 있음
- this: 함수나 메서드를 호출한 객체를 가리키는 키워드
  > '**this**' 키워드를 사용해 객체에 대한 특정한 작업을 수행할 수 있음

![1119_JS_BasicSyntax_02_2025-11-19-09-12-09](images/1119_JS_BasicSyntax_02_2025-11-19-09-12-09.png)

### Method & this 사용 예시

![1119_JS_BasicSyntax_02_2025-11-19-09-14-13](images/1119_JS_BasicSyntax_02_2025-11-19-09-14-13.png)

### JavaScript에서 this는 함수를 "**호출하는 방법**" 에 따라 가리키는 대상이 달라짐

![1119_JS_BasicSyntax_02_2025-11-19-09-15-22](images/1119_JS_BasicSyntax_02_2025-11-19-09-15-22.png)

### 단순 호출 this
- 가리키는 대상 => 전역 객체

![1119_JS_BasicSyntax_02_2025-11-19-09-16-04](images/1119_JS_BasicSyntax_02_2025-11-19-09-16-04.png)

### 메서드 호출 시 this
- 가리키는 대상 => 메서드를 호출한 객체

![1119_JS_BasicSyntax_02_2025-11-19-09-16-26](images/1119_JS_BasicSyntax_02_2025-11-19-09-16-26.png)

### 중첩된 함수에서의 this 문제점
- forEach의 인자로 전달된 콜백 함수는 일반 함수로 호출되므로, this는 전역 객체를 가리킴

![1119_JS_BasicSyntax_02_2025-11-19-09-17-02](images/1119_JS_BasicSyntax_02_2025-11-19-09-17-02.png)

### 해결책
- **화살표 함수는 자신만의 this를 가지지 않음**
- 따라서 외부 함수(myFunc)에서의 this 값을 가져옴

![1119_JS_BasicSyntax_02_2025-11-19-09-20-37](images/1119_JS_BasicSyntax_02_2025-11-19-09-20-37.png)

### JavaScript 'this' 정리
- JavaScript의 함수는 호출될 때 this를 암묵적으로 전달 받음
- JavaScript에서 this는 함수가 "호출되는 방식"에 따라 결정되는 현재 객체를 나타냄
- Python의 self와 Java의 this가 선언 시점에 이미 값이 정해지는 것과 달리 JavaScript의 this는 **함수가 호출될 때 동적으로 결정**
- 장점
  - 함수(메서드)를 하나만 만들어 여러 객체가 공유하여 각자 자신의 데이터로 동작하게 할 수 있음
- 단점
  - 이런 유연함이 실수로 이어질 수 있다는 것

#### Tip
- 개발자는 this 의 동작 방식을 충분히 이해하고 장점을 취하면서 실수를 피하는 데에 집중해야 함
- this 가 헷갈릴 땐 '누가 점(.)을 찍어 호출했는가?' 에 집중할 것. 점 앞의 객체가 this임

## 추가 객체 문법

### 추가 객체 문법
1. 단축 속성
2. 단축 메서드
3. 계산된 속성 (computed property name)
4. 구조 분해 할당 (destructing assignment)
5. 객체와 전개 구문 (Spread Syntax)
6. Object keys() / values() / entries()
7. Optional chaining ('?.')

### 1. 단축 속성
- 키 이름과 값으로 쓰이는 변수의 이름이 같은 경우 단축 구문을 사용할 수 있음

![1119_JS_BasicSyntax_02_2025-11-19-09-27-40](images/1119_JS_BasicSyntax_02_2025-11-19-09-27-40.png)

### 2. 단축 메서드
- 메서드 선언 시 function 키워드 생략 가능

![1119_JS_BasicSyntax_02_2025-11-19-09-36-38](images/1119_JS_BasicSyntax_02_2025-11-19-09-36-38.png)

### 3. 계산된 속성 (computed property name)
- 키가 대괄호([])로 둘러싸여 있는 속성
> 고정된 값이 아닌 변수 값을 사용할 수 있음

![1119_JS_BasicSyntax_02_2025-11-19-09-37-31](images/1119_JS_BasicSyntax_02_2025-11-19-09-37-31.png)

#### TIP
- 대괄호 안의 표현식이 너무 복잡해지면, 어떤 키가 생성될 지 파악하기 어려워 가독성이 떨어질 수 있음
- 동적으로 키를 만들다 보면 의도치 않게 같은 이름의 키가 생성되어, 기존 값이 덮어써질 위험이 있음

### 4. 구조 분해 할당 (destructing assignment)
- 배열 또는 객체를 분해하여 객체 속성을 변수에 쉽게 할당할 수 있는 문법

![1119_JS_BasicSyntax_02_2025-11-19-09-38-43](images/1119_JS_BasicSyntax_02_2025-11-19-09-38-43.png)

- '함수의 매개변수'로 객체 구조 분해 할당 활용 가능

![1119_JS_BasicSyntax_02_2025-11-19-09-41-22](images/1119_JS_BasicSyntax_02_2025-11-19-09-41-22.png)

### 5. 객체와 전개 구문 (Spread Syntax, ...)
- "객체 복사"
  - 객체 내부에서 객체 전개
- 얕은 복사에 활용 가능
  - 얕은 복사: 겉(최상위 속성)만 복사하고, 속(중첩 객체)은 공유하는 복사

![1119_JS_BasicSyntax_02_2025-11-19-09-42-33](images/1119_JS_BasicSyntax_02_2025-11-19-09-42-33.png)

### 6. 유용한 객체 메서드
- Object.keys()
  - Object 의 Key 값들을 리스트로 반환
- Object.values()
  - Object 의 Value 값들을 리스트로 반환
- Object.entries()
  - Object 의 key 와 Value 값들을 한 쌍으로 묶은 리스트로 반환

![1119_JS_BasicSyntax_02_2025-11-19-09-44-16](images/1119_JS_BasicSyntax_02_2025-11-19-09-44-16.png)

### 7. Optional chaining ('**?.**')
- 속성이 없는 중첩 객체에 접근하려 할 때 에러 발생 없이 안전하게 접근하는 방법
- 만약 참조 대상이 null 또는 undefined라면 에러가 발생하는 것 대신 평가를 멈추고 undefined를 반환

![1119_JS_BasicSyntax_02_2025-11-19-09-45-36](images/1119_JS_BasicSyntax_02_2025-11-19-09-45-36.png)

### 7. Optional chaining ('**?.**') 장점
- 참조가 누락될 가능성이 있는 경우 연결된 속성으로 접근할 때 더 짧고 간단한 표현식을 작성할 수 있음
- 어떤 속성이 필요한 지에 대한 보증이 확실하지 않는 경우에 객체의 내용을 보다 편리하게 탐색할 수 있음
- 만약 Optional chaining을 사용하지 않는다면 다음과 같이 '&&' 연산자를 사용해야 함

![1119_JS_BasicSyntax_02_2025-11-19-09-47-00](images/1119_JS_BasicSyntax_02_2025-11-19-09-47-00.png)

### 7. Optional chaining ('**?.**') 주의사항
1. Optional chaining은 존재하지 않아도 괜찮은 대상에만 사용해야 함 (남용 X)
    - 왼쪽 평가대상이 없어도 괜찮은 경우에만 선택적으로 사용
    - 중첩 객체를 에러 없이 접근하는 것이 사용 목적이기 때문

    ![1119_JS_BasicSyntax_02_2025-11-19-09-49-42](images/1119_JS_BasicSyntax_02_2025-11-19-09-49-42.png)

2. Optional chaining 앞의 변수는 반드시 선언되어 있어야 함

    ![1119_JS_BasicSyntax_02_2025-11-19-09-50-11](images/1119_JS_BasicSyntax_02_2025-11-19-09-50-11.png)

### 7. Optional chaining ('**?.**') 정리
1. obj?.prop
    - obj가 존재하면 obj.prop을 반환하고, 그렇지 않으면 undefined를 반환
2. obj?.[prop]
    - obj가 존재하면 obj[prop]을 반환하고, 그렇지 않으면 undefined를 반환
3. obj?.method()
    - obj가 존재하면 obj.method()를 호출하고, 그렇지 않으면 undefined를 반환

#### TIP
- null과 undefined일 때만 동작
- 체인 중간이 null인 경우, 그 뒤의 코드는 실행되지 않음. 이를 '단락 평가'라 함.

## JSON

### JSON
- JSON: JavaScript Object Notation
  - Key-Value 형태로 이뤄진 자료 표기법
  - JavaScript의 Object와 유사한 구조를 가지고 있지만 JSON은 일정한 형식을 가진 "**문자열**"
  - JavaScript에서 JSON을 사용하기 위해서는 Object 자료형으로 변경해야 함
  - 특정 언어에 종속되지 않는 데이터 형식으로, API 통신 등에서 널리 사용

### Object => JSON
- JOSN.stringfy() 를 사용해 객체를 문자열로 변환

![1119_JS_BasicSyntax_02_2025-11-19-09-55-43](images/1119_JS_BasicSyntax_02_2025-11-19-09-55-43.png)

### JSON => Object
- JSON.parse() 를 사용해 문자열을 객체로 변환

![1119_JS_BasicSyntax_02_2025-11-19-09-56-16](images/1119_JS_BasicSyntax_02_2025-11-19-09-56-16.png)

# 배열

### 배열
- 배열(Array): 순서가 있는 데이터 집합을 저장하는 자료구조
  - 객체는 키(key)로 데이터를 관리하지만, 순서가 중요하지 않음
  - '첫 번째', '두 번째'처럼 순서가 중요한 데이터 묶음이 필요할 때 사용하는 것이 바로 "순서가 있는 컬렉션, 배열(Array)"
  - 하지만 배열의 인덱스는 숫자로만 이뤄져 있어, "키 자체가 데이터의 의미를 설명해주지 못하고", 특정 값을 찾기 위해서는 배열의 모든 요소를 "처음부터 순서대로 확인"해야 하는 단점이 있음

### 배열 구조
- 대괄호('[]')를 이용해 작성
- 요소의 자료형은 제약 없음
- length 속성을 사용해 배열에 담긴 요소 개수 확인 가능

![1119_JS_BasicSyntax_02_2025-11-19-10-00-51](images/1119_JS_BasicSyntax_02_2025-11-19-10-00-51.png)

## 배열 메서드

### 배열 주요 메서드
- push()
- pop()
- unshift()
- shift()

### push()
- 배열 끝에 요소를 추가
- 원본 배열을 직접 수정
- 반환 값: 추가된 후의 새로운 배열의 길이

![1119_JS_BasicSyntax_02_2025-11-19-10-01-41](images/1119_JS_BasicSyntax_02_2025-11-19-10-01-41.png)

### pop()
- 배열 끝 요소를 제거
- 원본 배열을 직접 수정
- 반환 값: 제거한 요소

![1119_JS_BasicSyntax_02_2025-11-19-10-02-03](images/1119_JS_BasicSyntax_02_2025-11-19-10-02-03.png)

### unshift()
- 배열 앞에 요소를 추가
- 원본 배열을 직접 수정
- 반환 값: 추가된 후의 새로운 배열 길이
- 배열의 모든 요소를 뒤로 한 칸씩 밀어야 하므로, 배열이 클 수록 성능이 저하 (**가급적 사용 X**)

![1119_JS_BasicSyntax_02_2025-11-19-10-02-57](images/1119_JS_BasicSyntax_02_2025-11-19-10-02-57.png)

### shift()
- 배열 앞 요소를 제거하고, 제거한 요소를 반환
- 원본 배열을 직접 수정
- 반환 값: 제거한 요소
- 배열의 모든 요소를 당겨와야 하므로, 배열이 클 수록 성능이 저하 (**가급적 사용 X**)

![1119_JS_BasicSyntax_02_2025-11-19-10-03-38](images/1119_JS_BasicSyntax_02_2025-11-19-10-03-38.png)

# Array helper method

### Array Helper Methods
- 배열 조작을 보다 쉽게 수행할 수 있는 특별한 메서드 모음
- ES6에 도입
- 배열의 각 요소를 **순회**하며 각 요소에 대해 함수(**콜백함수**)를 호출
- 대표 메서드
  - forEach(), map()
  - filter()
  - every()
  - some()
  - reduce()
  - 등등
- 메서드 호출 시 인자로 함수(**콜백함수**)를 받는 것이 특징

## 콜백 함수

### 콜백 함수
- 콜백 함수(Callback function): 다른 함수에 인자로 전달되는 함수
  - 외부 함수 내에서 호출되어 일종의 루틴이나 특정 작업을 진행
  - 특정 작업(1초 기다리기, ...)이 완료된 후, 시스템에 의해 나중에 호출(call back)되는 함수

### 콜백 함수 예시 1

![1119_JS_BasicSyntax_02_2025-11-19-10-12-27](images/1119_JS_BasicSyntax_02_2025-11-19-10-12-27.png)

### 콜백 함수 예시 2

![1119_JS_BasicSyntax_02_2025-11-19-10-12-39](images/1119_JS_BasicSyntax_02_2025-11-19-10-12-39.png)

### 주요 Array Helper Methods
- forEach
  - 배열 내의 모든 요소 각각에 대해 함수(콜백함수)를 호출
  - 반환 값 없음
- map
  - 배열 내의 모든 요소 각각에 대해 함수(콜백함수)를 호출
  - 함수 호출 결과를 모아 새로운 배열을 반환

## forEach

### forEach()
- 배열의 각 요소를 반복하며 모든 요소에 대해 함수(콜백함수)를 호출
- 구조

  ![1119_JS_BasicSyntax_02_2025-11-19-10-15-53](images/1119_JS_BasicSyntax_02_2025-11-19-10-15-53.png)

- 콜백함수는 3가지 매개변수로 구성
  - item: 처리할 배열의 요소
  - index: 처리할 배열 요소의 인덱스 (선택 인자)
  - array: forEach를 호출한 배열 (선택 인자)
- 반환 값
  - undefined

### forEach 예시
- 동일한 결과를 만들어 냄
- 간단한 콜백 함수의 경우, 화살표 함수를 사용하는 것이 가독성, 'this'를 다루는 방식의 차이가 있으므로 가능한 **화살표 함수** 사용이 권장

![1119_JS_BasicSyntax_02_2025-11-19-10-17-59](images/1119_JS_BasicSyntax_02_2025-11-19-10-17-59.png)

### forEach 활용
- forEach는 항상 undefined를 반환
- break 문으로 반복을 중단할 수 없음
- 간결한 코드를 위해서 필요한 매개변수만 활용

![1119_JS_BasicSyntax_02_2025-11-19-10-19-07](images/1119_JS_BasicSyntax_02_2025-11-19-10-19-07.png)  

## map

### map()
- 배열의 모든 요소에 대해 함수(콜백함수)를 호출하고, 반환된 호출 결과 값을 모아 **새로운 배열을 반환**
- 구조

  ![1119_JS_BasicSyntax_02_2025-11-19-10-20-38](images/1119_JS_BasicSyntax_02_2025-11-19-10-20-38.png)

- forEach의 매개 변수와 동일
- 반환 값
  - 배열의 각 요소에 대해 실행한 "callback의 결과를 모은 새로운 배열"
  - forEach 동작 원리와 같지만 forEach와 달리 **새로운 배열을 반환함**

### map 예시
- 배열을 순회하며 각 객체의 name 속성 값을 추출하기 (for ... of 와 비교)
- map()은 '배열 반환' 이라는 의도가 명확히 나타나, for 문보다 코드가 간결하고 직관적
- map()은 새로운 배열을 반환하므로, 다른 메서드를 체이닝할 수 있음
  - 체이닝: 함수의 반환 값에 꼬리를 물고 다음 함수를 바로 호출하는 기술

![1119_JS_BasicSyntax_02_2025-11-19-10-22-52](images/1119_JS_BasicSyntax_02_2025-11-19-10-22-52.png)

### map 활용
- 화살표 함수를 활용해 간결하게 활용할 수 있음
- 원본 배열(names)를 변경하지 않고, 항상 새로운 배열을 반환(불변성)

![1119_JS_BasicSyntax_02_2025-11-19-10-24-39](images/1119_JS_BasicSyntax_02_2025-11-19-10-24-39.png)

- 커스텀 콜백 함수 활용
  - 콜백 함수를 변수에 담아두면, map 외 다른 곳에서도 같은 로직을 할 수 있어 유용
- myCallbackFunc()가 아닌 **myCallbackFunc** 를 전달

![1119_JS_BasicSyntax_02_2025-11-19-10-25-42](images/1119_JS_BasicSyntax_02_2025-11-19-10-25-42.png)

### Javascript - map
- map 메서드에 callBackFunc 함수를 인자로 넘겨 numbers 배열의 각 요소를 callBackFunc 함수의 인자로 사용

![1119_JS_BasicSyntax_02_2025-11-19-10-26-34](images/1119_JS_BasicSyntax_02_2025-11-19-10-26-34.png)

### Python - map
- python의 map에 square 함수를 인자로 넘겨 numbers 배열의 각 요소를 square 함수의 인자로 사용

![1119_JS_BasicSyntax_02_2025-11-19-10-27-14](images/1119_JS_BasicSyntax_02_2025-11-19-10-27-14.png)

## 배열 순회 종합

### 배열 순회 정리

![1119_JS_BasicSyntax_02_2025-11-19-10-28-05](images/1119_JS_BasicSyntax_02_2025-11-19-10-28-05.png)

### 기타 Array Helper Methods
- [MDN 문서](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#array_methods_and_empty_slots)를 참고해 사용해보기

![1119_JS_BasicSyntax_02_2025-11-19-10-28-53](images/1119_JS_BasicSyntax_02_2025-11-19-10-28-53.png)

## 배열 with '전개 구문'

### 배열 with '전개 구문'
- '...' 은 배열의 괄호를 없애고 내용물만 꺼내기 때문에, 배열을 합치거나 중간에 삽입할 때 유용
- 전개 구문은 항상 새로운 배열을 만듦. 원본 배열은 전혀 변경되지 않음
- 배열 안의 객체는 데이터가 아닌 주소값만 복사됨. 복사본의 객체를 수정하면 원본도 바뀜

![1119_JS_BasicSyntax_02_2025-11-19-10-31-09](images/1119_JS_BasicSyntax_02_2025-11-19-10-31-09.png)

# 참고

## 클래스

### 클래스
- 클래스(class): 객체를 생성하기 위한 템플릿
  - 객체의 속성, 메서드를 정의하는 청사진 역할
  - '붕어빵'을 하나 만들 때마다 손으로 직접 모양을 빚는다고 상상
  - 100개를 만들려면 100번의 고된 수작업이 필요<br>
  -> 객체를 하나씩 선언하는 것
  - '붕어빵 틀' 역할을 하는 것이 바로 '클래스(class)'

### 클래스 기본 문법
1. class 키워드
    - 객체의 '설계도'인 클래스를 정의하기 위해 사용하는 예약어
    - 호이스팅 되지만, 선언 전에 접근하면 에러가 발생 (TDZ)
      - TDZ(Temporal Dead Zone): let, const 선언 전 변수 접근을 막는 일시적 사각 지대
2. 클래스 이름
    - 일반적으로 파스칼 케이스(PascalCase)로 작성
    - 함수처럼 이름을 생략한 '익명 클래스 표현식'으로 작성하는 것도 가능
3. 생성자 메서드(constructor())
    - new로 객체 생성 시 자동으로 호출되며, 속성 값의 초기 설정을 담당
    - 'constructor'라는 이름을 가진 메서드가 단 하나만 존재할 수 있음

![1119_JS_BasicSyntax_02_2025-11-19-10-34-47](images/1119_JS_BasicSyntax_02_2025-11-19-10-34-47.png)

### 클래스 도입
- ES6에서 도입
- 생성자 함수를 사용하던 기존의 객체 생성 방식을 더 명확하고 객체 지향적으로 표현하기 위해 도입
- 그래서 클래스는 내부적으로 생성자 함수를 기반으로 동작함

![1119_JS_BasicSyntax_02_2025-11-19-10-35-27](images/1119_JS_BasicSyntax_02_2025-11-19-10-35-27.png)

### 클래스 활용
- new 키워드는 새 객체를 만들고, constructor를 호출하여 초기 속성 값을 설정
- 메서드 안의 this는 메서드를 호출한 member3 자신을 가리킴

![1119_JS_BasicSyntax_02_2025-11-19-10-36-32](images/1119_JS_BasicSyntax_02_2025-11-19-10-36-32.png)

### new 연산자
- 'new' 연산자: 클래스나 생성자 함수를 사용하여 새로운 객체를 생성

  ![1119_JS_BasicSyntax_02_2025-11-19-10-37-21](images/1119_JS_BasicSyntax_02_2025-11-19-10-37-21.png)

  - 클래스의 constructor()는 new 연산자에 의해 자동으로 호출되며 특별한 절차 없이 객체를 초기화할 수 있음
  - new 없이 클래스를 호출하면 TypeError 발생
  
## 콜백 함수의 이점

### 콜백 함수 구조를 사용하는 이유
- 함수 유연성 측면  
  - 함수를 호출하는 코드에서 콜백 함수의 동작을 자유롭게 변경할 수 있음
  - map 함수는 동일하지만, 어떤 '콜백 함수'를 전달하느냐에 따라 결과가 달라짐

  ![1119_JS_BasicSyntax_02_2025-11-19-10-38-50](images/1119_JS_BasicSyntax_02_2025-11-19-10-38-50.png)

- 비동기적 측면
  - setTimeout 함수는 콜백 함수를 인자로 받아 일정 시간이 지난 후에 실행됨
  - 이 때, setTimeout 함수는 비동기적으로 콜백 함수를 실행하므로, 다른 코드의 실행을 방해하지 않음

  ![1119_JS_BasicSyntax_02_2025-11-19-10-41-24](images/1119_JS_BasicSyntax_02_2025-11-19-10-41-24.png)

## forEach에서 break 사용하기

### forEach에서 break 사용하기
- forEach에서는 break 키워드를 사용할 수 없음
- 대신 some과 every의 특징을 활용해 마치 break를 사용하는 것처럼 활용할 수 있음

![1119_JS_BasicSyntax_02_2025-11-19-10-42-21](images/1119_JS_BasicSyntax_02_2025-11-19-10-42-21.png)

### forEach에서 break 하는 대안
- some을 활용한 예시
  - 콜백 함수가 true를 반환하면 즉시 순회를 중단하는 특징을 활용

![1119_JS_BasicSyntax_02_2025-11-19-10-43-18](images/1119_JS_BasicSyntax_02_2025-11-19-10-43-18.png)

- every를 활용한 예시
  - 콜백 함수가 false를 반환하면 즉시 순회를 중단하는 특징을 활용

![1119_JS_BasicSyntax_02_2025-11-19-10-44-34](images/1119_JS_BasicSyntax_02_2025-11-19-10-44-34.png)

## 배열은 객체다

### 배열은 객체다
- 배열도 키와 속성들을 담고 있는 참조 타입의 객체
- 배열의 요소를 대괄호 접근법을 사용해 접근하는 건 객체 문법과 같음
  - 배열의 키는 숫자
- 숫자형 키를 사용해 객체의 기본 기능 외로 "순서가 있는 컬렉션"을 제어하는 특별한 메서드를 제공
- 배열은 인덱스를 키로 가지며 length 속성을 갖는 특수한 객체

![1119_JS_BasicSyntax_02_2025-11-19-10-45-35](images/1119_JS_BasicSyntax_02_2025-11-19-10-45-35.png)

### 실습
- 객체
  - 3080\. 함수와 객체 활용하기
  - 2972\. 객체와 메서드
  - 2973\. 객체 활용하기
- Array helper method
  - 3079\. 다양한 함수 표현
  - 2968\. 배열 활용하기
  - 2971\. 배열 순회2
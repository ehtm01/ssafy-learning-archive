# Article & User

## 모델 관계 설정

### Article - User 모델 관계 설정
- User 외래 키 정의

  ![1106_DB_ManyToOne_02_2025-11-06-08-49-44](images/1106_DB_ManyToOne_02_2025-11-06-08-49-44.png)

- User 모델을 직접 Import 하지 않는 이유
  - Article 클래스 생성 시점이 User 클래스 시점보다 빠른 경우 외래 키 설정에서 참고할 User 모델을 찾지 못 해 에러가 발생할 수 있음
  - models.py 에서는 안정적인 참조가 필요하기 때문에 settings.AUTH_USER_MODEL 의 값을 사용

### User 모델을 참조하는 2가지 방법
- settings.AUTH_USER_MODEL
  - settings.py 에서 정의된 AUTH_USER_MODEL 설정 값을 가져옴
  - 반환 값: 'accounts.User' (문자열)
  - models.py 에서 User 모델을 참조할 때 주로 사용
- get_user_model()
  - 현재 settings.py 에 정의되어 활성화된 User 모델을 가져옴
  - 반환 값 : User Object (객체)
  - **models.py를 제외한 다른 모든 위치**에서 사용
- settings.AUTH_USER_MODEL의 반환 값이 문자열이어도 괜찮은 이유
  - 모델의 경로 형태인 문자열이 ForeignKey의 참조 모델로 설정되면, Django 에서 내부적으로 해당 모델이 완전히 로딩된 후 모델 클래스를 가져와 처리하는 지연 평가(lazy evaluation) 방식으로 동작하기 때문

### Migration
- 기존에 테이블이 있는 상황에서 필드를 추가하려고 하기 때문에 발생하는 과정
- 기본적으로 모든 필드에는 NOT NULL 제약 조건이 설정되어 있어, 데이터 없이 새로운 필드를 추가할 수 없음
- '1'을 입력하고 Enter 진행 (다음 화면에서 직접 기본 값 입력)

  ![1106_DB_ManyToOne_02_2025-11-06-09-01-15](images/1106_DB_ManyToOne_02_2025-11-06-09-01-15.png)

- 추가하는 외래 키 필드에 어떤 데이터를 넣을 것인지 직접 입력해야 함
- 마찬가지로 '1'을 입력하고 Enter 진행
> 기존에 작성된 게시글이 있다면 모두 1번 회원이 작성한 것으로 처리됨

  ![1106_DB_ManyToOne_02_2025-11-06-09-02-37](images/1106_DB_ManyToOne_02_2025-11-06-09-02-37.png)

  - 1번 회원이 없는 경우 migrate 시 에러 발생할 수 있음을 유의

- migrations 파일 생성 후 migrate 진행

  `$ python manage.py migrate`

- articles_article 테이블에 user_id 필드 생성 확인

  ![1106_DB_ManyToOne_02_2025-11-06-09-06-03](images/1106_DB_ManyToOne_02_2025-11-06-09-06-03.png)

## 게시글 CREATE

### 게시글 CREATE 구현
- 새 게시글 작성 시 ArticleForm 출력 변화 확인
  - 새롭게 추가된 ForeignKey 필드인 User 필드 확인됨
- User 모델에 대한 사용자 입력 창이 나오지만 사용자가 입력하지 않아야 하는 입력
  - 다른 사람을 선택하게 되면 사칭에 대한 문제가 발생할 수 있음

    ![1106_DB_ManyToOne_02_2025-11-06-09-07-33](images/1106_DB_ManyToOne_02_2025-11-06-09-07-33.png)

- 기존 ArticleForm 에서 사용자가 입력할 수 있는 필드를 변경
  - 글 작성자는 사용자가 선택하지 않아도 되는 정보
- 사용자는 게시글 제목과 내용만 입력하도록 수정

  ![1106_DB_ManyToOne_02_2025-11-06-09-08-13](images/1106_DB_ManyToOne_02_2025-11-06-09-08-13.png)

- 게시글을 작성하면 아래와 같이 에러가 발생
  - NOT NULL constraint failed: articles_article.user_id
  > user_id 필드 데이터가 누락되어 NOT NULL 제약 조건에 위배

    ![1106_DB_ManyToOne_02_2025-11-06-09-08-58](images/1106_DB_ManyToOne_02_2025-11-06-09-08-58.png)

- 게시글 작성 시 작성자 정보가 함께 저장될 수 있도록 save의 commit 옵션 활용
  - 게시글 작성자는 현재 글을 작성하는 로그인 된 사용자(`request.user`) 정보를 저장

    ![1106_DB_ManyToOne_02_2025-11-06-09-09-41](images/1106_DB_ManyToOne_02_2025-11-06-09-09-41.png)

- 게시글 작성 후 데이터베이스 articles_article 테이블 확인

  ![1106_DB_ManyToOne_02_2025-11-06-09-10-03](images/1106_DB_ManyToOne_02_2025-11-06-09-10-03.png)

  - 로그인한 User에 따라 저장되는 User PK가 다를 수 있음을 유의

## 게시글 READ

### 게시글 READ 구현
- index 페이지에 게시글 작성자 정보 출력하도록 수정

  ![1106_DB_ManyToOne_02_2025-11-06-09-17-08](images/1106_DB_ManyToOne_02_2025-11-06-09-17-08.png)

- 각 게시글 상세 페이지에도 작성자 정보 출력하도록 수정

  ![1106_DB_ManyToOne_02_2025-11-06-09-19-05](images/1106_DB_ManyToOne_02_2025-11-06-09-19-05.png)

## 게시글 UPDATE

### 게시글 UPDATE 구현
- 게시글 수정 요청 사용자와 게시글 작성 사용자를 비교하여 본인의 게시글만 수정할 수 있도록 하기

  ![1106_DB_ManyToOne_02_2025-11-06-09-20-06](images/1106_DB_ManyToOne_02_2025-11-06-09-20-06.png)

- 해당 게시글의 작성자가 아니라면, 수정/삭제 버튼을 출력하지 않도록 하기

  ![1106_DB_ManyToOne_02_2025-11-06-09-21-29](images/1106_DB_ManyToOne_02_2025-11-06-09-21-29.png)

## 게시글 DELETE

### 게시글 DELETE 구현
- 삭제를 요청하려는 사람과 게시글을 작성한 사람을 비교하여 본인의 게시글만 삭제할 수 있도록 하기

  ![1106_DB_ManyToOne_02_2025-11-06-09-22-46](images/1106_DB_ManyToOne_02_2025-11-06-09-22-46.png)

- views.py 에서 또 사용자를 구분하여 처리하는 이유
  - 요청을 보내는 방법은 브라우저만 있는 것이 아니기 때문에 내부에서도 반드시 처리가 필요
  - requests 패키지 혹은 postman 어플을 이용한 요청은 브라우저를 통하지 않기 때문에 내부에서 사용자 구분을 해야함

# Comment & User

## 모델 관계 설정

### Comment - User 모델 관계 설정
- User 는 여러 개의 댓글을 작성
- Comment 는 한 명의 작성자가 작성
- Comment 모델 클래스에 User 필드를 참조하도록 외래 키(ForeignKey) 설정

  ![1106_DB_ManyToOne_02_2025-11-06-09-26-11](images/1106_DB_ManyToOne_02_2025-11-06-09-26-11.png)

### Migration
- 이전에 Article 와 User 모델 관계 설정 때와 동일한 상황
- 기존 Comment 테이블에 새로운 필드가 빈 값으로 추가될 수 없기 때문에 기본 값 설정 과정이 필요

  ![1106_DB_ManyToOne_02_2025-11-06-09-27-34](images/1106_DB_ManyToOne_02_2025-11-06-09-27-34.png)

- Migration 후 articles_comment 테이블에 user_id 필드 확인

  ![1106_DB_ManyToOne_02_2025-11-06-09-28-08](images/1106_DB_ManyToOne_02_2025-11-06-09-28-08.png)

## 댓글 CREATE

### 댓글 CREATE 구현
- 댓글 작성 시 이전에 게시글 작성할 때와 동일한 에러 발생
  - NOT NULL constraint failed: articles_comment.user_id
  > 댓글의 작성자를 저장하는 user_id 필드 데이터가 누락되었기 때문

    ![1106_DB_ManyToOne_02_2025-11-06-09-29-19](images/1106_DB_ManyToOne_02_2025-11-06-09-29-19.png)

- 댓글 작성 시 작성자 정보가 함께 저장될 수 있도록 작성

  ![1106_DB_ManyToOne_02_2025-11-06-09-29-38](images/1106_DB_ManyToOne_02_2025-11-06-09-29-38.png)

- 댓글 작성 후 articles_comment 테이블 확인

  ![1106_DB_ManyToOne_02_2025-11-06-09-30-46](images/1106_DB_ManyToOne_02_2025-11-06-09-30-46.png)

  - 로그인한 User에 따라 저장되는 User PK가 다를 수 있음을 유의

## 댓글 READ

### 댓글 READ 구현
- 댓글 출력 시 댓글 작성자와 함께 출력

  ![1106_DB_ManyToOne_02_2025-11-06-09-31-22](images/1106_DB_ManyToOne_02_2025-11-06-09-31-22.png)

## 댓글 DELETE

### 댓글 DELETE 구현
- 해당 댓글의 작성자가 아니라면, 댓글 삭제 버튼을 출력하지 않도록 함

  ![1106_DB_ManyToOne_02_2025-11-06-09-35-03](images/1106_DB_ManyToOne_02_2025-11-06-09-35-03.png)

- 댓글 삭제 요청 사용자와 댓글 작성 사용자를 비교하여 본인의 댓글만 삭제할 수 있도록 하기

  ![1106_DB_ManyToOne_02_2025-11-06-09-35-31](images/1106_DB_ManyToOne_02_2025-11-06-09-35-31.png)

# View decorators

### View decorator
- View decorator: View 함수의 동작을 수정하거나 추가 기능을 제공하는 데 사용되는 Python 데코레이터
  - 일종의 "사전 체크리스트"처럼 동작해서 사용자 접근을 보다 안전하고 체계적으로 관리할 수 있음
  - 뷰 함수 위에 붙여서 작동하며, 코드 흐름을 방해하지 않고 깔끔하게 조건을 설정할 수 있음
  - 자주 쓰이는 View decorator는 로그인 여부, 권한 검사, HTTP 요청 방식 제한 등을 다룸

### View decorators 종류
- Allowed HTTP methods
  - 뷰가 허용하는 HTTP 요청 방식(GET, POST 등)을 제한
- Conditional view processing
  - 클라이언트가 보낸 조건을 확인한 후, 조건에 따른 응답 처리
- GZip compression
  - 서버에서 응답 데이터를 압축해서 전송
- 추가 view decorators는 아래 공식 문서 참고
  - https://docs.djangoproject.com/en/5.2/topics/http/decorators/
  
## Allowed HTTP methods

### Allowed HTTP methods
- Allowed HTTP methods: 특정 HTTP method로만 View 함수에 접근할 수 있도록 제한하는 데코레이터
  - 웹 요청은 GET, POST 등 다양한 요청 방식(method)을 사용하며, 각 방식은 고유한 목적을 갖고 있음
  - 요청 방식을 제한하면 보안이 강화되고, 코드의 역할도 명확히 분리됨
  - 해당 데코레이터를 사용하면 View 로직을 보호하면서 사용자에게도 올바른 인터페이스를 제공할 수 있음

### 주요 Allowed HTTP methods
- `require_http_methods(["METHOD1", "METHOD2", ...])`
  - 지정된 HTTP method만 허용
- `require_safe()`
  - **GET**과 **HEAD** method만 허용
- `require_POST()`
  - **POST** method만 허용
- 허용되지 않은 method로 요청하는 경우 405 (Method Not Allowed) 오류 반환

### Allowed HTTP methods 안내
- `require_http_methods(request_method_list)`
  - 지정된 HTTP method만 허용
  - 인자는 list 이며, 해당 list의 요소는 요청이 허용될 HTTP method 를 **문자열(대문자)**로 작성
- list에 작성된 method 이외의 method로 요청하면 HttpResponseNotAllowed (405) 를 반환

  ![1106_DB_ManyToOne_02_2025-11-06-09-43-32](images/1106_DB_ManyToOne_02_2025-11-06-09-43-32.png)

- `require_safe()`
  - GET과 HEAD method만 허용
- GET과 HEAD method 이외의 method로 요청하면 HttpResponseNotAllowed (405) 를 반환

  ![1106_DB_ManyToOne_02_2025-11-06-09-44-39](images/1106_DB_ManyToOne_02_2025-11-06-09-44-39.png)

- require_GET 이 있지만 require_safe를 권장하는 이유
  - GET과 HEAD는 서버 상태를 변경하지 않고 조회를 수행하는 safe method로 정의되어 있음
  - HEAD 요청은 주로 브라우저가 리소스를 받지 않고 메타 데이터 정보를 조회할 때 사용
  - 즉, require_safe가 require_GET보다 더 포괄적이며 표준 HTTP 클라이언트와의 호환성이 높음
- `require_POST()`
  - POST method만 허용
- POST method 이외의 method로 요청하면 HttpResponseNotAllowed (405) 를 반환

  ![1106_DB_ManyToOne_02_2025-11-06-09-46-44](images/1106_DB_ManyToOne_02_2025-11-06-09-46-44.png)

# ERD

### ERD
- ERD(Entity-Relationship Diagram): DB의 구조를 시각적으로 표현하는 도구
  - Entity(개체), 속성, 그리고 엔티티 간의 관계를 그래픽 형태로 나타내어 시스템의 논리적 구조를 모델링하는 다이어그램
  - 각 박스는 테이블을 나타내고, 그 안의 필드는 속성(컬럼), 화살표나 선은 관계(FK, 연관)를 나타냄
  - 이를 통해 개발자와 디자이너가 데이터 흐름을 쉽게 이해하고, 안정적인 DB 구조를 설계할 수 있음

### ERD 예시

![1106_DB_ManyToOne_02_2025-11-06-09-48-46](images/1106_DB_ManyToOne_02_2025-11-06-09-48-46.png)

- https://www.lucidchart.com/pages/er-diagrams

## ERD 구성 요소

### ERD의 구성 요소
- 엔티티(Entity)
  - DB에 저장되는 객체나 개념
    - DB에서 주로 테이블로 표현됨
  - 예: '게시글', '댓글', '회원'
- 속성(Attribute)
  - 엔티티가 가지는 고유한 데이터 항목
    - 테이블의 컬럼으로 표현됨
  - 예: '게시글' 엔티티의 '제목', '내용', '작성일자', '생성일자'
- 관계(Relationship)
  - 엔티티 간의 연관성을 나타냄
    - 테이블 간의 연결된 선으로 표현됨
  - 예: 게시글을 '작성' 한 회원, 게시글에 '달린' 댓글

### 개체와 속성 표현 방법
- 개체: 회원(User)
- 속성: 회원번호(id), 이름(name), 주소(address) 등
  - 개체가 지닌 속성 및 속성의 데이터 타입

    ![1106_DB_ManyToOne_02_2025-11-06-10-00-29](images/1106_DB_ManyToOne_02_2025-11-06-10-00-29.png)

### 관계
- 관계: 회원과 댓글 간의 관계
  - 회원이 '작성'한 댓글

    ![1106_DB_ManyToOne_02_2025-11-06-10-00-57](images/1106_DB_ManyToOne_02_2025-11-06-10-00-57.png)

### Cardinality
- 한 엔티티와 다른 엔티티 간의 수적 관계를 나타내는 표현
- 일대일 (one-to-one, 1:1)
  - 한 엔티티의 레코드가 다른 엔티티의 하나의 레코드와만 연결되는 관계
    - 예: 한 '사람'은 하나의 '여권'만 소유하고, '여권'도 한 '사람'에게만 발급
- 다대일 (many-to-one, N:1)
  - 여러 레코드가 하나의 엔티티와 연결되며, 반대 방향에서는 하나만 연결되는 관계
    - 예: 여러 명의 '학생'이 하나의 '학교'에 소속됨
- 다대다 (many-to-many, M:N)
  - 양 쪽 모두 여러 레코드와 연결되는 관계
    - 예: '학생'은 여러 '과목'을 수강할 수 있고, '과목'도 여러 '학생'이 수강할 수 있음

### Cardinality 표현
- 선의 끝부분에 표시되며 일반적으로 숫자나 기호(Crow's foot)로 표현됨

  ![1106_DB_ManyToOne_02_2025-11-06-10-23-55](images/1106_DB_ManyToOne_02_2025-11-06-10-23-55.png)

### Cardinality 적용
- 회원은 여러 댓글을 작성한다.
- 각 댓글은 하나의 회원만 존재한다

  ![1106_DB_ManyToOne_02_2025-11-06-10-24-23](images/1106_DB_ManyToOne_02_2025-11-06-10-24-23.png)

### ERD의 중요성
- DB 설계의 핵심 도구
  - 엔티티(테이블), 속성(컬럼), 관계를 명확히 정의함으로써 논리적 데이터 구조를 시각적으로 표현함
  - 복잡한 비즈니스 로직을 단순하고 직관적인 다이어그램으로 정리됨
  - 중복 데이터를 제거하고 효율적인 저장 구조를 만들 수 있음
- 시각적 모델링으로 효과적인 의사소통 지원
  - 개발자, 기획자, 디자이너 등 다양한 직군이 ERD를 활용해 협업할 수 있음
  - 요구사항 분석 단계에서 누락된 기능이나 관계를 빠르게 파악 가능
  - 비전문가에게도 시스템 구조를 쉽게 설명할 수 있음
- 실제 시스템 개발 전 데이터 구조 최적화에 중요
  - 사전에 데이터 흐름과 연관 관계를 명확히 분석해 불필요한 관계나 비효율적인 설계를 방지함
  - 시스템 개발 전에 ERD를 작성함으로써 이후 DB 구축 단계에서 중대한 구조적 오류를 줄이는 데 효과적임
  - 변경이나 유지보수 시에도 ERD를 기반으로 안정적으로 수정할 수 있음

## ERD 제작 사이트

### 무료 ERD 제작 사이트
- Draw.io (diagrams.net)
  - 별도의 회원가입 없이 바로 사용 가능
  - 다양한 다이어그램 템플릿 제공
  - https://app.diagrams.net/
- ERDCloud
  - 실시간 협업 기능 지원
  - https://www.erdcloud.com/

# 참고

## 추가 기능 구현

### 인증된 사용자만 댓글 작성 및 삭제
- 로그인된 사용자만 댓글을 작성할 수 있도록 데코레이터 추가

  ![1106_DB_ManyToOne_02_2025-11-06-10-28-22](images/1106_DB_ManyToOne_02_2025-11-06-10-28-22.png)

### 실습
- Article & User / Comment & User
  - 3058. 할 일 목록 생성시 작성자 정보 추가하기
  - 3059. 내 할 일 목록만 모아보기
  - 1908. 리뷰 서비스 - 책과 리뷰와 유저
  - 1903. 편의점 프랜차이즈 시스템 - 모델 정의
  - 1905. 편의점 프랜차이즈 시스템 - 신규 매장과 신규 상품 등록
  - 1906. 편의점 프랜차이즈 시스템 - 회원 정보 수정과 상품 삭제
- 인증된 사용자만 서비스 이용
  - 3060. 1:N 과 로그인 기능을 활용한 코드 개선
  - 1909. 리뷰 서비스 - 로그인 여부에 따른 리뷰 생성과 삭제
  - 1904. 편의점 프랜차이즈 시스템 - auth 시스템
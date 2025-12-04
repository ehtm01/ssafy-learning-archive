# Many to one relationships

## 모델 관계

### 관계(relationship)의 정의
- 관계(relationship): DB 내 여러 테이블 간의 논리적인 연결 관계를 나타냄
  - DB에서 '강사' 테이블과 '학생' 테이블이 있을 때, "이삼성 강사가 김싸피 학생을 가르치고 있다."는 정보를 저장하려면 두 테이블 간의 관계(relationship)를 설정해야 함
  - 이런 관계를 표현하기 위해 한 테이블에 다른 테이블의 기본 키(Primary Key)를 저장하며, 이처럼 다른 테이블의 기본 키를 참조하는 속성을 외래 키(Foreign Key)라고 함
  - 외래 키는 두 테이블 간의 논리적인 연결 고리 역할을 하며 이를 통해 관계형 데이터베이스에서 연관된 데이터를 효율적으로 관리할 수 있음

### 관계의 종류
- 1:1 (One to One) 관계
  - 한 테이블의 레코드는 다른 테이블의 한 레코드와 연결됨
  - 예시: 한 사람당 하나의 주민등록번호
- N:1 (Many to One) 관계
  - 여러 개의 레코드가 하나의 레코드와 연결됨
  - 예시: 여러 교육생(N)을 한 강사(1)가 가르침
- N:M (Many to Many) 관계
  - 여러 레코드가 여러 레코드와 상호 연결됨
  - 보통 중간 테이블(예: 수강신청)을 사용해 구현됨
  - 예시: 여러 학생(N)이 여러 과목(M)을 수강함

![1105_DB_ManyToOne_01_2025-11-05-09-00-19](images/1105_DB_ManyToOne_01_2025-11-05-09-00-19.png)

### Many to one relationships
- Many to one relationships(N:1 or 1:N): 한 테이블의 0개 이상의 레코드가 다른 테이블의 레코드 한 개와 관련된 관계

### Many to one relationships 예시
- SSAFY Track : Student
  - SSAFY Track과 교육생의 관계?
- Account : Bank
  - 계좌와 은행의 관계?
- Baseball Team : Member
  - 야구 팀과 야구 선수의 관계?
- Order : Customer
  - 주문과 고객의 관계?
- Country : City
  - 국가와 도시의 관계?
- Movie : Actor
  - 영화와 배우의 관계?

- SSAFY Track(1) : Student(N)
  - 하나의 트랙에는 여러 명의 교육생이 포함됨
  - 한 명의 교육생은 트랙이 중복되어서는 안 됨
- Account(N) : Bank(1)
  - 하나의 계좌는 한 은행에만 소속되어 있음
  - 한 은행은 여러 개의 계좌를 가질 수 있음
- Baseball Team(1) : Member(N)
  - 한 팀에 여러 명의 선수가 소속됨
  - 한 선수가 다른 야구 팀에 소속될 수 없음
- Order(N) : Customer(1)
  - 한 명의 고객이 여러 주문 가능
  - 하나의 주문을 여러 명의 고객이 낼 수 없음
- Country(1) : City(N)
  - 하나의 국가는 여러 도시를 가짐
  - 한 도시가 중복된 국가에 포함되지 않음
- Movie(N) : Actor(M) => N:1 관계 아님
  - 영화에 여러 배우들이 출연 가능함
  - 배우도 여러 영화에 출연 가능함

### 댓글과 게시글의 관계
- Comment(N) : Article(1)
  - 하나의 게시글에는 여러 개의 댓글이 달림
  - 단, 게시글에 댓글이 없는 경우도 존재함
  - 댓글이 소속된 게시글이 없는 경우는 없음
  > 즉, 0개 이상의 댓글은 1개의 게시글에 작성될 수 있다.

### 테이블 관계 설정
- 관계 설정을 위한 Foreign Key(외래 키, FK)를 N:1에서 1을 담당하는 테이블에 위치하면 안 됨
  - Article Table에 Foreign Key 컬럼을 위치시키면 중복 데이터로 인해 낭비가 발생함

    ![1105_DB_ManyToOne_01_2025-11-05-09-09-41](images/1105_DB_ManyToOne_01_2025-11-05-09-09-41.png)
  
  - 댓글 생성마다 Comment의 정보와 함께 Article 정보(id, title, content, ...)가 매 번 중복 저장됨
- 관계 설정을 위한 Foreign Key(외래 키, FK)의 적절한 위치는 바로 N:1에서 N을 담당하는 테이블에 위치
  - Comment가 생성되면 Article의 정보만 저장하면 됨

    ![1105_DB_ManyToOne_01_2025-11-05-09-12-32](images/1105_DB_ManyToOne_01_2025-11-05-09-12-32.png)
  
  - 외래 키 컬럼에 저장되는 데이터는 참조하는 데이터를 대표하는 Primary Key(PK) 정보를 저장

## 댓글 모델 정의

### ForeignKey 필드
- ForeignKey(to, on_delete): 한 모델이 다른 모델을 참조하는 관계를 설정하는 필드
> N:1 관계 표현할 때 사용

> DB에서 외래 키로 구현됨
- to 속성
  - 참조하는 모델 class 이름 (N:1에서 N이 아닌 1의 class 정보)
- on_delete 속성
  - 외래 키가 참조하는 객체(1)가 사라졌을 때, 외래 키를 가진 객체(N)를 어떻게 처리할 지를 정의하는 설정 (<u>데이터 무결성</u>)
- to와 on_delete 속성은 ForeignKey 설정에 필수 요소

---
- 데이터 무결성: 데이터가 정확하고 일관되며, 신뢰할 수 있도록 유지되는 상태

### on_delete 속성 종류
- CASCADE
  - 참조된 객체(부모 객체)가 삭제될 때 이를 참조하는 모든 객체도 삭제되도록 지정
  - 예: 게시글이 삭제되면 해당 게시글의 모든 댓글을 삭제
- PROTECT
  - 삭제하려는 부모 객체에 자식 객체가 존재한다면 해당 부모 객체를 삭제하지 못 하도록 지정
  - 예: 게시글을 삭제할 때 해당 게시글에 댓글이 존재하면 게시글 삭제 불가
- SET_NULL
  - 부모 객체가 삭제되면, 해당 필드에 값이 **NULL이 저장**되도록 지정
  - 단, 해당 **ForeignKey** 필드 설정이 **null=True**가 설정되어야 함
- 기타 on_delete 설정 값 참고 페이지
  - https://docs.djangoproject.com/en/5.2/ref/models/fields/#arguments

### 댓글 모델 정의하기
- ForeignKey 클래스의 인스턴스 이름은 참조하는 모델 클래스 이름의 **단수형**으로 작성하는 것을 권장

  ![1105_DB_ManyToOne_01_2025-11-05-09-19-11](images/1105_DB_ManyToOne_01_2025-11-05-09-19-11.png)

> 단수형으로 이름을 권장하는 이유
- 단일 객체를 참조하므로 속성명을 단수형으로 작성하면 의미가 명확해짐
- 코드 작성시 문맥이 자연스러워짐

### Migration 이후 댓글 테이블 확인
- 만들어지는 필드 이름 규칙
  - '작성한 외래 키 필드명' + '_' + 'id'
- 댓글 테이블의 article_id 외래 키 필드 확인
  - <u>bigint 자료형</u> 확인
> 참조하는 클래스 이름의 소문자(단수형)로 작성하는 것이 권장되었던 이유

![1105_DB_ManyToOne_01_2025-11-05-09-21-37](images/1105_DB_ManyToOne_01_2025-11-05-09-21-37.png)

- 외래 키는 models.py의 클래스 내에 ForeignKey 필드를 작성하는 순서와 관계 없이 테이블의 마지막 필드로 생성됨

---
- bigint 자료형
  - 64비트 정수형으로 약 9경까지 저장할 수 있어 숫자의 고갈 걱정이 없어 Primary Key(PK)를 선언할 때 사용
  - 외래 키는 이러한 PK 정보를 저장하기 때문에 동일하게 해당 자료형을 사용

## 댓글 생성 연습

### 댓글 생성 연습 준비하기
- 연습을 위한 shell 환경에서 진행
- ipython 설치 필요 `$ pip install ipython`
- django shell 시작 후 댓글 작성을 위한 게시글 하나 작성

  ```py
  # django shell 실행 (-v 2 옵션은 선택)
  $ python manage.py shell
  8 objects imported automatically (use -v 2 for details).

  # 게시글 생성
  Article.objects.create(title='title', content='content')
  ```

### 댓글 생성 연습
- 댓글 생성 후 바로 저장 확인

  ```py
  # Comment 클래스의 인스턴스 comment 생성
  comment = Comment()

  # 인스턴스 변수 저장
  comment.content = 'first comment'

  # DB에 댓글 저장
  comment.save()

  # 에러 발생
  IntegrityError: NOT NULL constraint failed: articles_comment.article_id
  => articles_comment 테이블의 ForeignKeyField, article_id 값이 저장 시 누락되었기 때문
  ```

- 현재 어떤 게시글에 작성되는 댓글인지 저장될 댓글 데이터에 게시글 정보가 없는 상태
- 게시글 정보를 가져와 댓글 저장

  ```
  # 게시글 정보 조회하여 가져오기
  article = Article.objects.get(pk=1)
  
  # 외래 키 데이터 입력
  comment.article = article

  # 직접적으로 테이블의 필드에 pk를 넣어도 저장되지만 권장하지 않음
  # comment.article_id = article.pk

  # 댓글 저장 및 확인
  comment.save()
  ```

- article_id에 직접 pk를 넣는 것을 권장하지 않는 이유
  - 직접 객체를 할당하는 경우는 저장될 객체 타입을 에러 발생 유무를 통해 명확히 검증할 수 없음
  - 직접 pk를 입력하는 경우에는 숫자를 저장하기 때문에 잘못된 객체의 PK 값이 저장될 수 있음
  - 예: `comment.article_id = book.pk` => 잘못된 정보지만 에러 발생 안 함
- comment 인스턴스를 통한 article 값 참조하기

  ```py
  comment.pk
  # 출력: 1

  comment.content
  # 출력: 'first comment'

  # 클래스 변수명인 article로 조회 시 해당 참조하는 게시물 객체를 조회할 수 있음
  comment.article
  # 출력: <Article: Article object (1)>

  # 테이블 상의 article_id 값은 해당 게시글의 Primary Key(PK)값만 확인 가능
  comment.article_id
  # 출력: 1
  ```

- article_pk는 존자하지 않는 필드이기 때문에 사용 불가
- comment 를 통한 article 객체의 데이터 참조하기

  ```py
  # 1번 댓글이 작성된 게시글의 pk 조회
  comment.article.pk
  # 출력: 1

  # 1번 댓글이 작성된 게시글의 content 조회
  comment.article.content
  # 출력: 'content'
  ```

- 두 번째 댓글 생성 및 데이터 확인

  ```py
  commentary = Comment(content='second comment', article=article)
  commentary.save()

  commentary.pk
  # 출력: 2
  commentary
  # 출력: <Comment: Comment.object (2)>
  commentary.article.id
  # 출력: 1
  ```

  ![1105_DB_ManyToOne_01_2025-11-05-09-36-27](images/1105_DB_ManyToOne_01_2025-11-05-09-36-27.png)

# 관계 모델 참조

## 참조의 정의
- 참조: 직접 대상의 정보를 저장하고 필요할 때 활용하는 것
  - 참조는 마치 "내가 친구의 전화번호를 저장" 하는 것과 같다.
  - 내가 전화번호를 가지고 있어 언제든 친구에게 전화나 문자할 수 있음
  - 직전 실습에서 **댓글(Comment)에는 게시글(Article) 정보를 저장하는 ForeignKey 필드인 article이 존재**
  - 해당 필드를 통해 게시글 정보에 쉽게 접근 가능
  - **댓글(Comment)은 게시글(Article)을 참조**한다고 말함
    - 예: 댓글의 게시글 내용에 접근: `comment.article.content`

### 특정 게시글(Article)의 댓글(Comment) 정보 조회하기
- QuerySet API의 .all() 사용하기 => X
  - 특정 게시글(Article)의 댓글(Comment)들이 아닌 **모든 댓글 정보를 가져오게 됨**

    ```py
    # 특정 게시글의 댓글이 아닌 모든 댓글을 조회함
    comments = Comment.objects.all()
    ```
- QuerySet API의 .filter() 사용하기
  - 특정 게시글(Article) 정보를 조회 후 댓글(Comment)에서 filter를 활용해 댓글 조회 가능

    ```py
    # 특정 게시글 정보를 가져온 후 filter를 이용할 수 있음
    article = Articel.objects.get(pk=1)
    comments = Comment.objects.filter(article=article)
    ```

## 역참조

### 역참조의 정의
- 역참조: 누가 나를 참조하는지 거꾸로 조회하는 것
  - 역참조는 마치 "내 번호를 저장한 사람들이 누구인지 찾는 것" 과 비슷함
  - 직접적으로 정보를 가지고 있지 않고 반대로 확인해야 하기 때문에 **참조하는 것을 거꾸로 찾아야 하며 이를 역참조**라 부름
  - 게시글(Article) 입장에서는 연결된 댓글(Comment) 정보를 담는 필드가 존재하지 않음
  - 그래서 해당 글을 참조하고 있는 댓글(Comment)들을 역으로 찾아야 하며 Django에서는 이런 관계를 자동으로 추적해서 해당 게시글(Article)에 달린 댓글(Comment)를 쉽게 찾아올 수 있도록 **역참조 기능을 제공**

### 역참조 기본 구조

![1105_DB_ManyToOne_01_2025-11-05-09-54-45](images/1105_DB_ManyToOne_01_2025-11-05-09-54-45.png)

1. 모델 인스턴스
  - models.py 에 정의된 모델 클래스로 생성된 실제 데이터를 의미
    - 'article.title' 과 같이 속성에 접근 가능하며 속성을 수정할 수 있음
  - 역참조에서는 **참조 가능한 필드가 없는 모델 클래스의 인스턴스를 사용**하면 됨
    - Article(1) : Comment(N) => Article 에 참조 필드가 없어서 Article의 인스턴스를 사용
    > **특정 게시글**에 작성된 댓글 전체를 조회하는 요청

![1105_DB_ManyToOne_01_2025-11-05-10-06-34](images/1105_DB_ManyToOne_01_2025-11-05-10-06-34.png)

2. related manager (역참조 이름)
  - related manager 라고 부르며 N:1 혹은 N:M 관계에서 **역참조 시에 사용하는 매니저**를 의미
  - 'objects' 매니저를 통해 QuerySet API를 사용했던 것처럼 related manager를 통해 QuerySet API를 사용할 수 있게 됨
  > 특정 **게시글에 작성된 댓글** 전체를 조회하는 요청

![1105_DB_ManyToOne_01_2025-11-05-10-06-47](images/1105_DB_ManyToOne_01_2025-11-05-10-06-47.png)

3. QuerySet API
  - 데이터를 가져오기 위한 쿼리 결과 집합을 만드는 인터페이스
  - SQL 쿼리를 직접 쓰지 않고도 DB를 사용할 수 있음
  > 특정 게시글에 작성된 **댓글 전체를 조회**하는 요청

### related manager(역참조 이름) 이름 규칙
- **모델 클래스명 + _set** 이 기본값이며 Django에서 자동으로 생성해 줌
- 관계를 직접 정의하지 않은 모델에서 연결된 객체들을 조회할 수 있게 함
- 특정 댓글의 게시글 **참조** (Comment -> Article)
  - comment.article
- 특정 게시글의 댓글 목록 **역참조** (Article -> Comment)
  - article.comment_set.all()

### related manager 연습
- django shell 실행

  `$ python manage.py shell`

- 1번 게시글 조회

  ```py
  article = Article.objects.get(pk=1)
  ```

- 1번 게시글에 작성된 모든 댓글 조회하기 (역참조)

  ```py
  article. comment_set.all()

  <QuerySet [<Comment: Comment object (1)>, <Comment: Commnet object (2)>]>
  ```

- 1번 게시글에 작성된 모든 댓글 내용 출력하기

  ```py
  # 1번 게시글의 모든 댓글 정보들을 저장
  comments = article.comment_set.all()

  # 1번 게시글 댓글 정보들을 반복하여 개별 댓글 내용 출력
  for comment in comments:
      print(comment.content)
    
  ```출력
  first comment
  secont comment
  ```

# 댓글 구현

## 댓글 CREATE

### 댓글 CREATE 구현
- 사용자로부터 댓글 데이터를 입력받기 위한 CommentForm 정의

  ```py
  # articles/forms.py
  from .models import Article, Comment

  class CommentForm(forms.ModelForm):
      class Meta:
          model = Comment
          fields = '__all__'
  ```

- 댓글이 작성되는 곳은 게시글 상세(detail) 페이지 하단
- detail view 함수에서 CommentForm을 detail 페이지에서 사용할 수 있게 context로 전달

  ![1105_DB_ManyToOne_01_2025-11-05-10-15-01](images/1105_DB_ManyToOne_01_2025-11-05-10-15-01.png)

- detail view 함수에서 넘어오는 CommentForm을 사용하여 detail 페이지에 렌더링

  ![1105_DB_ManyToOne_01_2025-11-05-10-15-43](images/1105_DB_ManyToOne_01_2025-11-05-10-15-43.png)

- Comment 클래스의 외래 키 필드 article 또한 데이터 입력이 필요한 필드이기 때문에 출력되는 것
- 하지만, 외래 키 필드 데이터는 **사용자로부터 입력받는 값이 아닌 view 함수 내에서 다른 방법으로 전달받아 저장**되어야 함

  ![1105_DB_ManyToOne_01_2025-11-05-10-16-19](images/1105_DB_ManyToOne_01_2025-11-05-10-16-19.png)

- 게시글을 유저가 직접 선택한다면 발생하는 일
  - 댓글을 작성할 수 없도록 설정된 게시글을 선택해서 댓글을 추가할 수 있음
  - 댓글을 작성하는 게시글을 자세히 확인할 수 없어 엉뚱한 게시글에 댓글을 달 수 있음
- CommentForm의 출력 필드 조정하여 외래 키(Foreign Key) 필드가 출력되지 않도록 함

  ![1105_DB_ManyToOne_01_2025-11-05-10-18-15](images/1105_DB_ManyToOne_01_2025-11-05-10-18-15.png)

  - fields 설정을 tuple 로 진행 시 요소가 하나일 때 마지막 콤마(,) 를 반드시 작성
- 출력에서 제외된 외래 키 데이터는 어디서 받아와야 할까?
- detail 페이지의 URL에 게시글 정보가 존재
  - `path('<int:pk>/', views.detail, name='detail')`
  - 해당 게시글의 pk 값이 <u>variable routing</u>으로 전달되고 있음
- 댓글의 외래 키 데이터에 필요한 정보가 바로 게시글의 pk 값
  - 댓글 작성 시 해당 pk 값을 이용하여 게시글 데이터를 가져와 사용

---
- variable routing: 웹 주소 중 일부를 변수처럼 설정해 사용자의 입력 값에 따라 맞춤형 페이지를 보여주는 기능

---
- 댓글 저장 로직은 detail 함수가 아닌 개별 함수로 작성
  - 댓글 저장은 게시글 상세 보기와 전혀 다른 기능이기 때문 (<u>단일 책임 원칙</u>)
  - 댓글 저장 시 게시글 pk 정보를 URL 로 전달하여 사용

    ![1105_DB_ManyToOne_01_2025-11-05-10-23-22](images/1105_DB_ManyToOne_01_2025-11-05-10-23-22.png)

- comments_create 함수는 POST 작성만 진행
  - 댓글 작성 폼을 출력하는 GET 동작은 detail 함수에 이미 작성

    ![1105_DB_ManyToOne_01_2025-11-05-10-24-23](images/1105_DB_ManyToOne_01_2025-11-05-10-24-23.png)

- URL 로 전달받은 게시글의 pk를 이용해서 게시글 정보를 가져옴
- 댓글 생성 시 가져온 article 객체를 추가해야 함
- 가져온 article 객체는 댓글 생성 시 어떻게 저장하면 될까?
- save 메서드의 commit 인자

  ![1105_DB_ManyToOne_01_2025-11-05-10-27-05](images/1105_DB_ManyToOne_01_2025-11-05-10-27-05.png)

- 기본적으로 commit 속성은 True 기본 값
  - 설정 값이 True인 경우 인스턴스를 생성하고 반환한 다음 DB에도 저장 요청을 보냄
- commit이 False 인 경우 DB에 저장 요청을 보내지 않고 인스턴스만 반환
  - Create, but don't save the new instance.
- 댓글을 저장할 때 바로 DB에 저장 요청을 보내는 것이 아닌 게시글 정보를 추가한 후 저장 요청을 보내도록 로직을 구성하면 게시글 정보와 함께 댓글을 저장할 수 있게 됨

![1105_DB_ManyToOne_01_2025-11-05-10-29-31](images/1105_DB_ManyToOne_01_2025-11-05-10-29-31.png)

- 댓글 작성 후 DB에서 생성 확인
  - article_id 필드에 게시글 정보가 저장되어 있는 것을 확인

    ![1105_DB_ManyToOne_01_2025-11-05-10-29-59](images/1105_DB_ManyToOne_01_2025-11-05-10-29-59.png)

## 댓글 READ

### 댓글 READ 구현
- 댓글이 보이는 위치는 게시글 상세 페이지 하단 위치
  - detail view 함수에서 전체 댓글 데이터를 조회해서 detail.html 로 전달하여 댓글 데이터 조회

    ![1105_DB_ManyToOne_01_2025-11-05-10-30-44](images/1105_DB_ManyToOne_01_2025-11-05-10-30-44.png)

- 댓글 출력 확인

  ![1105_DB_ManyToOne_01_2025-11-05-10-31-08](images/1105_DB_ManyToOne_01_2025-11-05-10-31-08.png)

## 댓글 DELETE

### 댓글 DELETE 구현
- 개별 댓글마다 삭제할 수 있도록 기능을 추가
- 어떤 댓글을 삭제해야 하는지 삭제 대상 정보를 전달하기 위해 variable routing 이용

  ![1105_DB_ManyToOne_01_2025-11-05-10-31-56](images/1105_DB_ManyToOne_01_2025-11-05-10-31-56.png)

  - article_pk 정보는 URL 패턴을 일관되게 작성하기 위함 외에도 삭제 후 detail 페이지로 돌아갈 때 사용할 수 있는 정보이기 때문에 작성

- 댓글 삭제 view 함수 정의

  ![1105_DB_ManyToOne_01_2025-11-05-10-33-27](images/1105_DB_ManyToOne_01_2025-11-05-10-33-27.png)

- 댓글 삭제 버튼 추가
  - variable routing으로 전달되는 게시글 pk, 삭제될 댓글 pk 전달

    ![1105_DB_ManyToOne_01_2025-11-05-10-33-54](images/1105_DB_ManyToOne_01_2025-11-05-10-33-54.png)

- 댓글 삭제 버튼 출력 확인 및 삭제 테스트

  ![1105_DB_ManyToOne_01_2025-11-05-10-34-14](images/1105_DB_ManyToOne_01_2025-11-05-10-34-14.png)

# 참고

## 데이터 무결성

### 데이터 무결성이란
- DB에 저장된 데이터의 정확성, 일관성, 유효성을 유지하는 것
- DB에 저장된 데이터 값의 정확성을 보장하는 것
- 중요성
  - 데이터의 신뢰성 확보
  - 시스템 안정성
  - 보안 강화

## admin site 댓글 등록

### admin site에 댓글 등록하기
- 작성된 Comment 모델에 대해 Admin site 에서 관리할 수 있도록 아래와 같이 등록

  ![1105_DB_ManyToOne_01_2025-11-05-10-50-31](images/1105_DB_ManyToOne_01_2025-11-05-10-50-31.png)

## 댓글 추가 구현

### 1. 댓글이 없는 경우 대체 콘텐츠 출력
- DTL 의 `'for empty'` 태그 활용
  - `for` 문에 반복할 요소가 없는 경우 `empty` 태그가 실행됨

    ![1105_DB_ManyToOne_01_2025-11-05-10-51-23](images/1105_DB_ManyToOne_01_2025-11-05-10-51-23.png)

### 2. 댓글 개수 출력하기
- DTL filter 의 '`length`' 활용

  ```html
  <!-- views.py에서 전달받은 댓글로 길이 확인 -->
  {{ comments|length }}

  <!-- 역참조를 이용하여 댓글 길이 확인 -->
  {{ article.comment_set.all|length }}
  ```

- QuerySet APL 의 `count()` 메서드 활용

  ```html
  <!-- 역참조로 QuerySet API 이용 댓글 길이 확인 -->
  {{ article.comment_set.count }}
  ```

### 실습
- Many to one relationships
  - 1901. 도서 관리 서비스 만들기 - 1:N 관계 정의
  - 1896. 레스토랑 관리 서비스 - 모델 정의
  - 3055. 댓글 생성 기능 구현 준비
- 댓글 구현
  - 3056. 댓글 생성 기능 구현
  - 3057. 댓글 조회 및 삭제 기능 구현
  - 1899. 레스토랑 관리 서비스 - 메뉴 상세정보와 수정
  - 1900. 레스토랑 관리 서비스 - 이미지 추가와 코드 개선
- 관계 모델 참조
  - 1902. 도서 관리 서비스 - 1:N 관계 데이터 생성
  - 1898. 레스토랑 관리 서비스 - 메뉴
# Database 학습 요약

## 학습 개요
관계형 데이터베이스(RDBMS)와 Django ORM을 활용한 데이터베이스 설계 및 운영

---

## 1. SQL 기초

### 핵심 개념

**기본 쿼리**
- **SELECT**: 데이터 조회, WHERE 조건절
- **INSERT**: 데이터 삽입
- **UPDATE**: 데이터 수정
- **DELETE**: 데이터 삭제

**정렬 및 제한**
- **ORDER BY**: 정렬 (ASC/DESC)
- **LIMIT**: 결과 제한

**집계 함수**
- **COUNT**: 개수 세기
- **SUM**: 합계
- **AVG**: 평균
- **MAX/MIN**: 최대값/최소값

**그룹화**
- **GROUP BY**: 그룹화
- **HAVING**: 그룹 조건

**조인(JOIN)**
- **INNER JOIN**: 내부 조인
- **LEFT JOIN**: 왼쪽 외부 조인
- **RIGHT JOIN**: 오른쪽 외부 조인

**서브쿼리**
- SELECT 절의 서브쿼리
- WHERE 절의 서브쿼리
- FROM 절의 서브쿼리

### 학습 키워드
```
SQL | SELECT | INSERT | UPDATE | DELETE
JOIN | 집계함수 | GROUP BY | 서브쿼리
```

---

## 2. Django ORM

### 핵심 개념

**모델 정의**
- Model 클래스 상속
- 필드 타입 (CharField, IntegerField, DateField, etc.)
- 필드 옵션 (null, blank, default, unique, etc.)

**QuerySet API**
- **조회**: `all()`, `get()`, `filter()`, `exclude()`
- **생성**: `create()`, `save()`
- **수정**: `update()`, `save()`
- **삭제**: `delete()`

**필터링**
- `filter(field=value)`
- `filter(field__contains='text')`
- `filter(field__gt=value)` (Greater Than)
- `filter(field__lt=value)` (Less Than)

**정렬 및 제한**
- `order_by('field')`, `order_by('-field')`
- `[:10]` (슬라이싱)

**집계**
- `Count()`, `Sum()`, `Avg()`, `Max()`, `Min()`
- `aggregate()`, `annotate()`

### 학습 키워드
```
Django ORM | Model | QuerySet | CRUD
filter | aggregate | annotate
```

---

## 3. Many-to-One (1:N) 관계

### 핵심 개념

**ForeignKey**
- 외래 키(Foreign Key) 정의
- `models.ForeignKey(Model, on_delete=models.CASCADE)`
- `on_delete` 옵션: CASCADE, PROTECT, SET_NULL, etc.

**관계 접근**
- **정참조**: `comment.article` (N → 1)
- **역참조**: `article.comment_set.all()` (1 → N)
- `related_name` 설정

**관계 생성**
```python
# 댓글 생성
comment = Comment.objects.create(
    article=article,
    content='댓글 내용'
)
```

### 학습 키워드
```
1:N | ForeignKey | 정참조 | 역참조
related_name | on_delete
```

---

## 4. Many-to-Many (N:M) 관계

### 핵심 개념

**ManyToManyField**
- N:M 관계 정의
- `models.ManyToManyField(Model)`
- 중개 테이블 자동 생성

**관계 조작**
- **추가**: `add()`
- **제거**: `remove()`
- **조회**: `all()`, `filter()`
- **확인**: `exists()`

**실전 예제**
- 게시글 좋아요 기능
- 유저 팔로우 기능
- 태그 시스템

**중개 모델 (Through)**
- 추가 정보가 필요한 경우 중개 모델 사용
- `through` 옵션으로 커스텀 중개 모델 지정

### 학습 키워드
```
N:M | ManyToManyField | 중개테이블
add | remove | through
```

---

## 5. Django REST Framework with Database

### 핵심 개념

**Serializer와 관계**
- `PrimaryKeyRelatedField`: 기본키로 참조
- `StringRelatedField`: 문자열 표현
- `HyperlinkedRelatedField`: URL로 참조
- `SlugRelatedField`: 특정 필드로 참조

**Nested Serializer**
- 중첩된 직렬화
- `depth` 옵션
- 커스텀 nested serializer

**읽기/쓰기 분리**
- `read_only=True`
- `write_only=True`

### 학습 키워드
```
Serializer | RelatedField | Nested
depth | read_only | write_only
```

---

## 데이터베이스 설계 원칙

### 정규화
- 1차 정규화 (1NF)
- 2차 정규화 (2NF)
- 3차 정규화 (3NF)

### 관계 설계
- 1:1 (OneToOne)
- 1:N (ForeignKey)
- N:M (ManyToMany)

### 인덱스
- 인덱스의 필요성
- 인덱스 설계 고려사항

---

## 기술 스택

**DBMS**
- MySQL 8.x

**ORM**
- Django ORM

**API Framework**
- Django REST Framework

**도구**
- MySQL Workbench
- DB Browser for SQLite
- Postman (API 테스트)

---

## 학습 로드맵

```
1. SQL 기초
   ↓
2. Django ORM
   ↓
3. 1:N 관계
   ↓
4. N:M 관계
   ↓
5. DRF + Database
```

---

## 블로그 작성 아이디어

1. SQL vs Django ORM - 언제 무엇을 사용할까?
2. Django ORM 쿼리 최적화 완벽 가이드
3. 1:N과 N:M 관계 실전 예제로 이해하기
4. Django에서 N+1 쿼리 문제 해결하기
5. select_related vs prefetch_related 차이점
6. Django ORM으로 복잡한 쿼리 작성하기
7. 데이터베이스 정규화 이해하기
8. DRF Serializer에서 관계 데이터 다루기
9. Django에서 트랜잭션 처리하기
10. 데이터베이스 인덱싱 전략

---

## 성능 최적화 팁

**쿼리 최적화**
- `select_related()`: ForeignKey, OneToOne (JOIN 사용)
- `prefetch_related()`: ManyToMany, 역참조 (추가 쿼리)
- `only()`, `defer()`: 필요한 필드만 조회

**N+1 문제 해결**
```python
# Bad
articles = Article.objects.all()
for article in articles:
    print(article.user.username)  # N+1 발생

# Good
articles = Article.objects.select_related('user').all()
for article in articles:
    print(article.user.username)  # 1번의 쿼리
```

**벌크 연산**
- `bulk_create()`: 대량 생성
- `bulk_update()`: 대량 수정
- `update()`: 쿼리셋 일괄 수정

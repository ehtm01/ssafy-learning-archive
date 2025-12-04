# Database

SSAFY 1학기에서 학습한 데이터베이스 관련 내용을 정리한 폴더입니다.

## 목차

### [SQL 기초](./sql-basics)
관계형 데이터베이스와 SQL을 학습합니다.

**주요 내용:**
- SQL 기본 쿼리 (SELECT, INSERT, UPDATE, DELETE)
- WHERE, ORDER BY, LIMIT
- Aggregate Functions (COUNT, SUM, AVG, MAX, MIN)
- GROUP BY & HAVING
- JOIN (INNER, LEFT, RIGHT)
- Subquery

**학습 파일:**
- `1103_SQL_01.md` - SQL 기초 1
- `1104_SQL_02.md` - SQL 기초 2

---

### Django ORM & Relationships

**Many-to-One (1:N) 관계**
- 외래 키(Foreign Key) 이해
- Django에서의 1:N 관계 구현
- 역참조(Reverse Access)

**학습 파일:**
- `1105_DB_ManyToOne_01.md` - Many-to-One 관계 1
- `1106_DB_ManyToOne_02.md` - Many-to-One 관계 2

---

**Many-to-Many (N:M) 관계**
- ManyToManyField
- 중개 테이블 (Intermediate Table)
- 팔로우/좋아요 기능 구현

**학습 파일:**
- `1110_DB_ManyToMany_01.md` - Many-to-Many 관계 1
- `1111_DB_ManyToMany_02.md` - Many-to-Many 관계 2

---

### Django REST Framework with Database

**RESTful API와 데이터베이스 연동**
- Serializer로 모델 직렬화
- CRUD API 구현
- Related Field 처리

**학습 파일:**
- `1112_Django_DRF_01.md` - DRF 기초 1
- `1113_Django_DRF_02.md` - DRF 기초 2

---

### SQLD (SQL 개발자 자격증)
SQL 개발자 자격증 준비 내용

**학습 파일:**
- `SQLD.md` - SQLD 자격증 준비

---

## 프로젝트

- **PJT-06**: Django ORM 활용 프로젝트
- **PJT-07**: Django REST Framework API 개발

---

## 학습 순서 추천

1. **SQL 기초** - 데이터베이스 기본 개념 학습
2. **Many-to-One 관계** - Django에서 외래 키 다루기
3. **Many-to-Many 관계** - 복잡한 관계 모델링
4. **Django REST Framework** - API 개발과 DB 연동

---

## 실습 환경

- **DBMS**: MySQL
- **ORM**: Django ORM
- **API Framework**: Django REST Framework

---

## 추가 학습 자료

- [MySQL 공식 문서](https://dev.mysql.com/doc/)
- [Django ORM 문서](https://docs.djangoproject.com/en/stable/topics/db/)
- [DRF Serializer 문서](https://www.django-rest-framework.org/api-guide/serializers/)
- [SQL Tutorial (W3Schools)](https://www.w3schools.com/sql/)

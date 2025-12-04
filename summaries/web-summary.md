# Web Development 학습 요약

## 학습 개요
웹 개발의 Frontend와 Backend를 아우르는 Full Stack 웹 개발 학습

---

## Frontend

### 1. HTML/CSS

**핵심 개념**
- **HTML**: 시맨틱 태그, 폼(Form), 테이블
- **CSS**: 선택자, Box Model, Position, Display
- **레이아웃**: Flexbox, Grid Layout
- **Bootstrap**: 그리드 시스템, 컴포넌트, 유틸리티 클래스
- **반응형 웹**: 미디어 쿼리, 모바일 퍼스트

**학습 키워드**
```
시맨틱태그 | CSS선택자 | BoxModel | Flexbox | Grid
Bootstrap | 반응형웹 | 미디어쿼리
```

### 2. JavaScript

**핵심 개념**
- **기본 문법**: 변수(let/const/var), 데이터 타입, 연산자
- **함수**: 함수 선언, 화살표 함수, 콜백 함수
- **DOM 조작**: querySelector, createElement, 이벤트 리스너
- **이벤트 처리**: 이벤트 버블링, preventDefault, Event Delegation
- **비동기 처리**: Ajax, Fetch API, Promise, async/await
- **JSON**: 데이터 파싱 및 직렬화

**학습 키워드**
```
JavaScript | DOM | 이벤트처리 | 비동기
Fetch API | Promise | async/await | JSON
화살표함수 | 콜백함수
```

### 3. Vue.js

**핵심 개념**
- **Vue 기초**: Vue 인스턴스, 반응성(Reactivity)
- **디렉티브**: v-if, v-for, v-model, v-bind, v-on
- **컴포넌트**: 단일 파일 컴포넌트(SFC), 컴포넌트 등록
- **Props & Emit**: 부모-자식 컴포넌트 통신
- **데이터 흐름**: 단방향 데이터 흐름, 이벤트 버스
- **라우팅**: Vue Router
- **상태 관리**: Vuex (선택)

**학습 키워드**
```
Vue.js | 반응성 | 디렉티브 | SFC
컴포넌트 | Props | Emit | VueRouter
```

---

## Backend

### 1. Django

**핵심 개념**
- **Django 기초**: MTV 패턴(Model-Template-View)
- **URL 라우팅**: URLconf, path, 동적 라우팅
- **Template**: Template 문법, 템플릿 상속, 필터
- **Model**: Django ORM, 모델 정의, 필드 타입
- **ORM**: QuerySet, CRUD 연산, 필터링
- **Form**: ModelForm, 유효성 검사
- **Authentication**: 로그인/로그아웃, 회원가입, 사용자 인증
- **Static Files**: 정적 파일 관리, Media 파일

**학습 키워드**
```
Django | MTV패턴 | ORM | QuerySet
Template | Form | Authentication | 정적파일
```

### 2. Django REST Framework (DRF)

**핵심 개념**
- **RESTful API**: REST 원칙, HTTP 메서드(GET/POST/PUT/DELETE)
- **Serializer**: 직렬화/역직렬화, ModelSerializer
- **ViewSet**: APIView, ViewSet, Router
- **인증**: Token Authentication, Permission
- **관계 처리**: ForeignKey, ManyToMany Serializer
- **CRUD API**: 생성, 조회, 수정, 삭제 API 구현

**학습 키워드**
```
REST API | DRF | Serializer | ViewSet
Token 인증 | CRUD API | HTTP 메서드
```

---

## 통합 프로젝트 구조

```
Frontend (Vue.js)
    ↕ (REST API)
Backend (Django REST Framework)
    ↓
Database (MySQL)
```

---

## 학습 로드맵

### Frontend 경로
```
HTML/CSS → JavaScript → Vue.js
```

### Backend 경로
```
Django → Django REST Framework
```

### Full Stack 통합
```
Vue.js (Frontend) ←→ DRF (Backend API)
```

---

## 기술 스택

**Frontend**
- HTML5, CSS3
- JavaScript (ES6+)
- Vue.js 3
- Bootstrap 5

**Backend**
- Python 3.x
- Django 4.x
- Django REST Framework
- MySQL

**도구**
- VS Code
- Chrome DevTools
- Postman (API 테스트)
- Git/GitHub

---

## 블로그 작성 아이디어

### Frontend
1. CSS Flexbox와 Grid - 언제 무엇을 사용할까?
2. JavaScript 비동기 처리 완벽 가이드 (Callback → Promise → async/await)
3. Vue.js 컴포넌트 통신 패턴 정리
4. 반응형 웹 디자인 실전 가이드

### Backend
5. Django ORM 쿼리 최적화 팁
6. Django REST Framework로 RESTful API 설계하기
7. Token 기반 인증 시스템 구현하기
8. Django에서 N+1 쿼리 문제 해결하기

### Full Stack
9. Vue + Django로 Full Stack 프로젝트 구축하기
10. CORS 이해하고 해결하기
11. JWT 인증과 Refresh Token 전략

# 기술 블로그 작성 주제 목록

> 요약 문서를 바탕으로 공식 문서 및 공개 자료를 참고하여 작성할 블로그 포스트 목록입니다.

---

## 🐍 Python (6개 주제)

### 기초
1. **Python 자료구조 완벽 정리 (List, Dict, Set, Tuple)**
   - 각 자료구조의 특징과 사용 사례
   - 시간 복잡도 비교
   - 실전 예제

2. **얕은 복사 vs 깊은 복사 - 실전 예제로 이해하기**
   - 복사의 종류와 차이점
   - copy() vs deepcopy()
   - 실수하기 쉬운 케이스

3. **Python OOP 핵심 개념 정리**
   - 클래스와 인스턴스
   - 캡슐화, 상속, 다형성
   - 매직 메서드 활용

### 알고리즘
4. **알고리즘 문제 해결을 위한 Python 팁**
   - 유용한 내장 함수
   - 자주 사용하는 패턴
   - 시간 단축 기법

5. **DFS/BFS 구현 및 활용 사례**
   - DFS와 BFS의 차이
   - 재귀 vs 반복문
   - 실전 문제 해결

6. **Python으로 구현하는 주요 알고리즘 패턴**
   - 투 포인터
   - 슬라이딩 윈도우
   - 백트래킹

---

## 🌐 Web Development (11개 주제)

### Frontend (4개)

7. **CSS Flexbox와 Grid - 언제 무엇을 사용할까?**
   - Flexbox vs Grid 비교
   - 각각의 적합한 사용 사례
   - 실전 레이아웃 예제

8. **JavaScript 비동기 처리 완벽 가이드**
   - Callback → Promise → async/await 진화 과정
   - 비동기 처리의 필요성
   - 에러 핸들링

9. **Vue.js 컴포넌트 통신 패턴 정리**
   - Props & Emit
   - Provide/Inject
   - Event Bus vs Vuex

10. **반응형 웹 디자인 실전 가이드**
    - 미디어 쿼리 활용
    - 모바일 퍼스트 접근법
    - 실전 반응형 레이아웃

### Backend (4개)

11. **Django ORM 쿼리 최적화 팁**
    - select_related vs prefetch_related
    - only(), defer() 활용
    - 쿼리 개수 줄이기

12. **Django REST Framework로 RESTful API 설계하기**
    - REST 원칙
    - Serializer 설계
    - ViewSet과 Router

13. **Token 기반 인증 시스템 구현하기**
    - Token Authentication vs JWT
    - 인증 플로우
    - 보안 고려사항

14. **Django에서 N+1 쿼리 문제 해결하기**
    - N+1 문제란?
    - 발생 원인과 감지 방법
    - 해결 전략

### Full Stack (3개)

15. **Vue + Django로 Full Stack 프로젝트 구축하기**
    - 프로젝트 구조 설계
    - API 통신
    - 배포 전략

16. **CORS 이해하고 해결하기**
    - CORS란 무엇인가
    - 발생 원인
    - Django에서의 해결 방법

17. **JWT 인증과 Refresh Token 전략**
    - JWT 구조
    - Access Token vs Refresh Token
    - 보안 베스트 프랙티스

---

## 🗄️ Database (10개 주제)

### SQL & ORM (5개)

18. **SQL vs Django ORM - 언제 무엇을 사용할까?**
    - 각각의 장단점
    - 복잡한 쿼리 비교
    - 성능 고려사항

19. **Django ORM 쿼리 최적화 완벽 가이드**
    - 쿼리 분석 방법
    - 최적화 기법
    - 실전 사례

20. **1:N과 N:M 관계 실전 예제로 이해하기**
    - ForeignKey vs ManyToManyField
    - 역참조와 related_name
    - 중개 모델 활용

21. **select_related vs prefetch_related 차이점**
    - JOIN vs 추가 쿼리
    - 사용 시나리오
    - 성능 비교

22. **Django ORM으로 복잡한 쿼리 작성하기**
    - Q 객체 활용
    - annotate와 aggregate
    - Subquery 활용

### 설계 & 최적화 (5개)

23. **데이터베이스 정규화 이해하기**
    - 정규화의 필요성
    - 1NF, 2NF, 3NF
    - 실전 예제

24. **DRF Serializer에서 관계 데이터 다루기**
    - RelatedField 종류
    - Nested Serializer
    - read_only vs write_only

25. **Django에서 트랜잭션 처리하기**
    - 트랜잭션의 필요성
    - atomic 데코레이터
    - 롤백 처리

26. **데이터베이스 인덱싱 전략**
    - 인덱스란 무엇인가
    - 인덱스 생성 시점
    - 성능 개선 사례

27. **Django ORM 성능 측정과 개선**
    - django-debug-toolbar
    - 쿼리 프로파일링
    - 최적화 체크리스트

---

## 🤖 AI & Machine Learning (20개 주제)

### 기초 (3개)

28. **머신러닝 기초 개념 정리 (AI, ML, DL 차이)**
    - 인공지능의 범위
    - 머신러닝 vs 딥러닝
    - 학습 방법론 비교

29. **과적합(Overfitting) 이해하고 해결하기**
    - 과적합이란?
    - 발생 원인
    - 정규화 기법

30. **머신러닝 평가 지표 완벽 가이드**
    - Accuracy, Precision, Recall
    - F1-Score
    - 상황별 적절한 지표 선택

### NLP & Vision (4개)

31. **Word2Vec과 단어 임베딩 이해하기**
    - 단어를 벡터로 표현하는 이유
    - Word2Vec 원리
    - 실전 활용

32. **RNN, LSTM, GRU 차이점 정리**
    - 시퀀스 모델의 필요성
    - 각 모델의 특징
    - 장단점 비교

33. **CNN으로 이미지 분류 모델 만들기**
    - CNN의 기본 구조
    - 합성곱과 풀링
    - 전이 학습 활용

34. **전이 학습(Transfer Learning) 실전 가이드**
    - 전이 학습이란?
    - Fine-tuning 전략
    - 실전 예제

### LLM & Foundation Models (4개)

35. **Transformer 아키텍처 완벽 이해**
    - Attention 메커니즘
    - Encoder-Decoder 구조
    - 왜 Transformer가 혁신적인가

36. **GPT vs BERT - 무엇이 다를까?**
    - 아키텍처 비교
    - 학습 방법 차이
    - 사용 사례

37. **Prompt Engineering 실전 팁**
    - 프롬프트 작성 원칙
    - Few-shot Learning
    - Chain of Thought

38. **Fine-tuning vs LoRA - 언제 무엇을 사용할까?**
    - Full Fine-tuning의 한계
    - LoRA의 장점
    - 실전 적용 사례

### 실전 & 최적화 (5개)

39. **LangChain으로 RAG 챗봇 구축하기**
    - RAG 아키텍처
    - 벡터 데이터베이스 연동
    - 실전 구현

40. **벡터 데이터베이스 선택 가이드**
    - Pinecone, Chroma, FAISS 비교
    - 사용 시나리오
    - 성능 비교

41. **모델 양자화로 성능 최적화하기**
    - 양자화의 필요성
    - INT8, INT4 양자화
    - 정확도 vs 속도 트레이드오프

42. **AI 에이전트 구현 사례 분석**
    - AI 에이전트란?
    - ReAct 프레임워크
    - Multi-Agent 시스템

43. **LoRA와 QLoRA - 효율적인 Fine-tuning**
    - LoRA 원리
    - QLoRA의 개선점
    - 실전 적용 가이드

### 프로젝트 (4개)

44. **감성 분석 모델 만들기**
    - 데이터 전처리
    - 모델 선택
    - 실전 구현

45. **나만의 AI 챗봇 서비스 개발기**
    - 프로젝트 설계
    - LLM API 활용
    - 배포 전략

46. **Stable Diffusion 활용 프로젝트**
    - 이미지 생성 모델 이해
    - 프롬프트 엔지니어링
    - 실전 활용

47. **LLM을 활용한 문서 요약 서비스**
    - 요약 알고리즘
    - LangChain 활용
    - 서비스 구현

---

## 📊 주제별 통계

- **Python**: 6개
- **Web Development**: 11개
  - Frontend: 4개
  - Backend: 4개
  - Full Stack: 3개
- **Database**: 10개
- **AI/ML**: 20개
  - 기초: 3개
  - NLP & Vision: 4개
  - LLM & Foundation Models: 4개
  - 실전 & 최적화: 5개
  - 프로젝트: 4개

**총 47개 주제**

---

## 📅 작성 우선순위

### 우선순위 1 (기초 & 자주 묻는 질문)
- Python 자료구조 완벽 정리
- 얕은 복사 vs 깊은 복사
- JavaScript 비동기 처리 완벽 가이드
- Vue.js 컴포넌트 통신 패턴
- Django ORM 쿼리 최적화 팁
- 1:N과 N:M 관계 실전 예제
- select_related vs prefetch_related
- Transformer 아키텍처 완벽 이해

### 우선순위 2 (실전 활용)
- DFS/BFS 구현 및 활용
- Django REST Framework로 RESTful API 설계
- LangChain으로 RAG 챗봇 구축
- Prompt Engineering 실전 팁
- CORS 이해하고 해결하기

### 우선순위 3 (고급 & 최적화)
- Django에서 N+1 쿼리 해결
- Fine-tuning vs LoRA
- 모델 양자화로 성능 최적화
- AI 에이전트 구현 사례

---

## 💡 작성 시 유의사항

1. **공식 문서 참조**: 각 주제는 공식 문서를 기반으로 작성
2. **실전 예제**: 이론만이 아닌 실제 코드 예제 포함
3. **문제 해결**: 자주 발생하는 문제와 해결 방법 제시
4. **비교 분석**: 여러 방법을 비교하고 선택 가이드 제공
5. **시각화**: 다이어그램과 이미지를 활용하여 이해도 향상
6. **참고 자료**: 추가 학습을 위한 링크 제공

---

## 🔗 참고 자료

**공식 문서**
- [Python 공식 문서](https://docs.python.org/ko/3/)
- [Django 공식 문서](https://docs.djangoproject.com/)
- [Vue.js 공식 문서](https://vuejs.org/)
- [DRF 공식 문서](https://www.django-rest-framework.org/)
- [Hugging Face](https://huggingface.co/)
- [LangChain](https://python.langchain.com/)

**학습 자료**
- MDN Web Docs
- Real Python
- freeCodeCamp
- Papers with Code

---

> 이 목록은 지속적으로 업데이트되며, 작성 완료 시 체크 표시를 추가할 예정입니다.

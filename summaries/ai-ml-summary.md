# AI & Machine Learning 학습 요약

## 학습 개요
인공지능과 머신러닝의 기초부터 대규모 언어 모델(LLM), AI 에이전트까지 체계적으로 학습

---

## 1. 기계학습 기초

### 핵심 개념

**AI, ML, DL의 관계**
- **AI (Artificial Intelligence)**: 지능적 시스템 전체
- **ML (Machine Learning)**: 데이터로부터 학습하는 접근법
- **DL (Deep Learning)**: 신경망을 사용한 학습 방법

**데이터 구성 요소**
- **Feature (특성)**: 모델의 입력값, 예측의 근거
- **Label (라벨)**: 모델이 예측하려는 정답

**학습 방법론**
- **지도 학습 (Supervised Learning)**: 레이블이 있는 데이터로 학습
- **비지도 학습 (Unsupervised Learning)**: 레이블 없이 패턴 발견
- **강화 학습 (Reinforcement Learning)**: 보상을 통한 학습

**평가 지표**
- 정확도 (Accuracy)
- 정밀도 (Precision) / 재현율 (Recall)
- F1-Score
- Loss Function

**과적합과 정규화**
- **과적합 (Overfitting)**: 훈련 데이터에만 과도하게 맞춤
- **정규화 (Regularization)**: L1, L2, Dropout

### 학습 키워드
```
AI | ML | DL | 지도학습 | 비지도학습
Feature | Label | Overfitting | Regularization
```

---

## 2. 자연어 처리 (NLP)

### 핵심 개념

**텍스트 전처리**
- 토큰화 (Tokenization)
- 형태소 분석
- 불용어 제거 (Stopwords)
- 정규화 (Normalization)

**단어 표현**
- **Word2Vec**: 단어를 벡터로 표현
- **GloVe**: 글로벌 벡터 표현
- **임베딩 (Embedding)**: 단어의 의미를 수치화

**시퀀스 모델**
- **RNN (Recurrent Neural Network)**: 순환 신경망
- **LSTM (Long Short-Term Memory)**: 장기 기억 모델
- **GRU (Gated Recurrent Unit)**: 간소화된 LSTM

**응용 분야**
- 텍스트 분류
- 감성 분석
- 기계 번역
- 챗봇

### 학습 키워드
```
NLP | 토큰화 | Word2Vec | 임베딩
RNN | LSTM | GRU | 시퀀스모델
```

---

## 3. 컴퓨터 비전

### 핵심 개념

**CNN (Convolutional Neural Network)**
- 합성곱 연산 (Convolution)
- 풀링 (Pooling)
- 특징 추출 (Feature Extraction)

**주요 아키텍처**
- VGG
- ResNet
- Inception
- MobileNet

**응용 분야**
- 이미지 분류 (Image Classification)
- 객체 탐지 (Object Detection)
- 이미지 분할 (Segmentation)

**전이 학습 (Transfer Learning)**
- 사전 훈련된 모델 활용
- Fine-tuning

### 학습 키워드
```
CNN | 합성곱 | 풀링 | 이미지분류
전이학습 | Fine-tuning | ResNet
```

---

## 4. Foundation Models

### 핵심 개념

**Transformer 구조**
- Self-Attention 메커니즘
- Multi-Head Attention
- Positional Encoding
- Encoder-Decoder 구조

**대규모 언어 모델 (LLM)**
- **GPT (Generative Pre-trained Transformer)**: 생성 모델
- **BERT (Bidirectional Encoder Representations)**: 양방향 인코더
- **T5, BART**: 인코더-디코더 모델

**이미지 Foundation 모델**
- CLIP: 텍스트-이미지 연결
- Stable Diffusion: 이미지 생성
- DALL-E: 텍스트로 이미지 생성

**Fine-tuning 기법**
- Full Fine-tuning
- Parameter-Efficient Fine-tuning (PEFT)
- LoRA (Low-Rank Adaptation)

**Prompt Engineering**
- Zero-shot Learning
- Few-shot Learning
- In-context Learning
- Chain of Thought (CoT)

### 학습 키워드
```
Transformer | Attention | GPT | BERT
LLM | Fine-tuning | LoRA | Prompt Engineering
```

---

## 5. LangChain & AI Services

### 핵심 개념

**LangChain 기초**
- LLM 통합 프레임워크
- 프롬프트 템플릿
- 체인 (Chain) 구성
- 메모리 관리

**RAG (Retrieval-Augmented Generation)**
- 검색 기반 생성
- 벡터 데이터베이스
- 문서 임베딩
- 컨텍스트 주입

**AI 서비스 개발**
- 챗봇 구현
- 문서 Q&A 시스템
- 요약 서비스
- API 통합

**벡터 데이터베이스**
- Pinecone
- Chroma
- FAISS

### 학습 키워드
```
LangChain | RAG | 벡터DB | 임베딩
챗봇 | 문서QA | 프롬프트템플릿
```

---

## 6. 리소스 효율적 학습법

### 핵심 개념

**모델 경량화**
- **양자화 (Quantization)**: 모델 크기 축소
  - INT8, INT4 양자화
  - Post-Training Quantization
- **프루닝 (Pruning)**: 불필요한 가중치 제거
- **지식 증류 (Knowledge Distillation)**: 큰 모델 → 작은 모델

**효율적 학습 기법**
- **LoRA**: 적은 파라미터로 Fine-tuning
- **QLoRA**: 양자화 + LoRA
- **Adapter**: 추가 레이어로 학습

**배포 최적화**
- ONNX
- TensorRT
- TFLite

### 학습 키워드
```
양자화 | 프루닝 | 지식증류 | LoRA
모델경량화 | 효율적학습 | ONNX
```

---

## 7. AI Agent

### 핵심 개념

**AI 에이전트**
- 자율적 의사결정 시스템
- 목표 지향적 행동
- 환경과의 상호작용

**에이전트 구성 요소**
- **Perception**: 환경 인식
- **Planning**: 계획 수립
- **Action**: 행동 실행
- **Memory**: 기억 관리

**Multi-Agent System**
- 여러 에이전트 협업
- 역할 분담
- 의사소통 프로토콜

**에이전트 프레임워크**
- AutoGPT
- LangChain Agents
- ReAct (Reasoning + Acting)

**도구 활용 (Tool Use)**
- API 호출
- 검색 엔진 사용
- 코드 실행
- 외부 도구 통합

### 학습 키워드
```
AI Agent | 자율적의사결정 | Multi-Agent
ReAct | Tool Use | Planning
```

---

## 학습 로드맵

```
1단계: 기계학습 기초
   ↓
2단계: NLP & Computer Vision
   ↓
3단계: Foundation Models (Transformer, LLM)
   ↓
4단계: LangChain & RAG
   ↓
5단계: 효율적 학습법 & 최적화
   ↓
6단계: AI Agent 구현
```

---

## 기술 스택

**프레임워크**
- TensorFlow
- PyTorch
- Hugging Face Transformers
- LangChain

**도구**
- Google Colab
- Jupyter Notebook
- Weights & Biases (실험 관리)

**라이브러리**
- NumPy, Pandas
- Scikit-learn
- OpenCV (Computer Vision)
- NLTK, spaCy (NLP)

**클라우드 & API**
- OpenAI API
- Google Cloud AI
- AWS SageMaker

---

## 블로그 작성 아이디어

### 기초
1. 머신러닝 기초 개념 정리 (AI, ML, DL 차이)
2. 과적합(Overfitting) 이해하고 해결하기
3. 머신러닝 평가 지표 완벽 가이드

### NLP & Vision
4. Word2Vec과 단어 임베딩 이해하기
5. RNN, LSTM, GRU 차이점 정리
6. CNN으로 이미지 분류 모델 만들기
7. 전이 학습(Transfer Learning) 실전 가이드

### LLM & Foundation Models
8. Transformer 아키텍처 완벽 이해
9. GPT vs BERT - 무엇이 다를까?
10. Prompt Engineering 실전 팁
11. Fine-tuning vs LoRA - 언제 무엇을 사용할까?

### 실전 & 최적화
12. LangChain으로 RAG 챗봇 구축하기
13. 벡터 데이터베이스 선택 가이드
14. 모델 양자화로 성능 최적화하기
15. AI 에이전트 구현 사례 분석

### 프로젝트
16. 감성 분석 모델 만들기
17. 나만의 AI 챗봇 서비스 개발기
18. Stable Diffusion 활용 프로젝트
19. Multi-Agent 시스템 구축하기
20. LLM을 활용한 문서 요약 서비스

---

## 참고 자료

**공식 문서**
- [TensorFlow](https://www.tensorflow.org/)
- [PyTorch](https://pytorch.org/)
- [Hugging Face](https://huggingface.co/)
- [LangChain](https://python.langchain.com/)

**온라인 강의**
- Stanford CS229: Machine Learning
- Deep Learning Specialization (Coursera)
- Fast.ai

**논문**
- Attention Is All You Need (Transformer)
- BERT: Pre-training of Deep Bidirectional Transformers
- GPT-3: Language Models are Few-Shot Learners
- LoRA: Low-Rank Adaptation of Large Language Models

**커뮤니티**
- arXiv (논문 저장소)
- Papers with Code
- Hugging Face Community

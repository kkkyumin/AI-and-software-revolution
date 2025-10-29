# 🍽️ Food-101 AI Classifier
EfficientNet-B0 기반의 음식 이미지 분류 및 LaMini-GPT-774M 설명 웹앱

---

## 📌 프로젝트 개요
**Food-101 AI Classifier**는 사용자가 업로드한 음식 이미지를 분석하고,  
AI 언어 모델을 이용해 해당 음식의 특징과 문화적 배경을 자동으로 설명하는 웹 애플리케이션입니다.  
백엔드 서버 없이 완전 로컬 환경에서 실행되며, **ONNXRuntime** 및 **Transformers.js**를 활용합니다.

---

## ⚙️ 주요 기능

| 기능 | 설명 |
|------|------|
| 🍔 음식 이미지 분류 | EfficientNet-B0 ONNX 모델로 Food-101 음식 인식 |
| 🧠 AI 설명 생성 | LaMini-GPT-774M (Hugging Face Transformers.js) 기반 음식 설명 생성 |
| 🖼️ 이미지 미리보기 | 업로드 즉시 음식 사진 렌더링 |
| 💾 메모리 관리 | 로컬에서 모델 캐싱 및 경고 표시 기능 |
| 🌐 완전 프론트엔드 실행 | HTML, CSS, JS만으로 작동 (서버 불필요) |

---

## 🛠 기술 스택

| 구분 | 기술 |
|------|------|
| Frontend | HTML5, CSS3, JavaScript (Vanilla) |
| AI 모델 | EfficientNet-B0 (ONNX), LaMini-GPT-774M (Transformers.js) |
| 런타임 | ONNXRuntime Web |
| LLM 연결 | Hugging Face CDN (로컬 LLM 지원) |
| 배포 환경 | GitHub Pages, 로컬 브라우저 실행 |

---

## 🚀 실행 방법

### ✅ **1️⃣ GitHub Pages에서 바로 실행 (가장 간단한 방법)**
아래 주소로 접속하면 별도의 설치 없이 바로 실행됩니다.  
👉 **[https://kkkyumin.github.io/AI-and-software-revolution/](https://kkkyumin.github.io/AI-and-software-revolution/)**

---

### ✅ **2️⃣ 로컬 환경에서 실행**
> 로컬에서도 테스트 가능하지만, 반드시 “서버 환경(http://)”에서 실행해야 합니다.

1. 저장소를 클론하거나 다운로드:
   ```bash
   git clone https://github.com/kkkyumin/AI-and-software-revolution.git
   cd AI-and-software-revolution
   ```
2. 모델 파일(`model.onnx`)이 루트 경로에 존재하는지 확인합니다.  
   (없다면 GitHub에서 제공된 파일을 다운로드하여 `/AI-and-software-revolution` 폴더에 넣으세요.)
3. 아래 명령어로 간단한 로컬 서버를 실행합니다.
   ```bash
   python -m http.server 8000
   ```
4. 브라우저에서 아래 주소로 접속합니다:
   ```
   http://localhost:8000
   ```
5. 페이지가 열리면 음식 이미지를 업로드하고, 설명을 확인하세요.

---

### ✅ **3️⃣ 이미지 사용 방법**
- [Hugging Face Food-101 Dataset](https://huggingface.co/datasets/ethz/food101)  
  에서 제공하는 **Food-101 데이터셋 이미지**를 직접 활용할 수 있습니다.
- 또는 **구글 이미지 검색을 통해 다운로드한 음식 사진**을 업로드해도 인식이 가능합니다.  
  (예: “pizza”, “bibimbap”, “sushi” 등)

> 단, 입력 이미지는 **224×224 RGB 음식 사진**일수록 정확도가 높습니다.

---

## 🧠 모델 변환 과정

이 프로젝트의 ONNX 모델은  
[`dwililiya/food101-model-classification`](https://huggingface.co/dwililiya/food101-model-classification)의  
**PyTorch2ONNX.ipynb** 코드를 기반으로 변환하였습니다.

- 원본 PyTorch 모델: `best_model.pth`  
- 변환 코드: `PyTorch2ONNX.ipynb`  
- 결과: `model.onnx` (브라우저 실행용)

> 변환 과정에서는 `torch.onnx.export()` 함수를 사용하여 모델을 내보내고,  
> **ONNXRuntime-Web**에서 추론이 가능한 형식으로 최적화되었습니다.

---

## 🧾 데이터셋 출처

본 프로젝트는 **Food-101 Dataset (ETH Zurich)**을 기반으로 학습된 모델을 활용합니다.  
데이터셋은 Hugging Face Datasets에서 다운로드 가능합니다:  
👉 [https://huggingface.co/datasets/ethz/food101](https://huggingface.co/datasets/ethz/food101)

> ⚠️ Food-101 데이터셋은 101종의 음식 이미지(각 클래스당 1,000장)를 포함하며,  
> 본 프로젝트는 해당 공개 데이터셋을 전처리 및 학습용으로 사용하였습니다.

---

## 🧠 모델 정보

| 항목 | 내용 |
|------|------|
| 분류 모델 | EfficientNet-B0 (ONNX 버전) |
| LLM 모델 | LaMini-GPT-774M (HuggingFace/Xenova) |
| 데이터셋 | Food-101 (ETH Zurich) |
| 입력 크기 | 224×224 RGB |
| 출력 클래스 | 101가지 음식 (예: sushi, bibimbap, pizza 등) |

---

## 🎨 UI 디자인 톤

| 요소 | 색상 코드 | 의미 |
|------|-------------|------|
| 배경 | #FFF8F0 | 따뜻한 크림톤, 편안함 |
| 포인트 | #E63946 | 식욕 자극형 토마토 레드 |
| 텍스트 | #2E1F1F | 딥 브라운, 가독성 높음 |
| 서브 | #8B3A3A | 보조 강조 색상 |

---

## 🧩 디렉토리 구조
```
/AI-and-software-revolution
 ├── index.html
 ├── model.onnx
 ├── PyTorch2ONNX.ipynb
 └── README.md
```

---

## ⚠️ 주의사항
- 첫 실행 시 LLM(LaMini-GPT-774M) 다운로드에 **30~60초**가 소요될 수 있습니다.  
- ONNX 모델 및 LLM 로딩 시 **메모리 사용량이 많습니다.**
  - ➤ **한 번 사용 후 새로고침(Refresh)** 하는 것을 권장합니다.  
  - “🔴 Memory warning” 메시지가 표시될 경우 새로고침을 수행하세요.
- 인터넷 연결이 필요합니다 (모델은 Hugging Face CDN에서 불러옵니다).  
- 일부 모바일 브라우저(Safari 등)에서는 모델 로딩이 제한될 수 있습니다.

---

## 📦 라이선스
MIT License  
모델 및 데이터셋 저작권은 각각 아래에 귀속됩니다.

- Hugging Face – [dwililiya/food101-model-classification](https://huggingface.co/dwililiya/food101-model-classification)
- ETH Zurich – [Food-101 Dataset](https://huggingface.co/datasets/ethz/food101)

---

## ✨ 제작자
**AI Developer:** kkkyumin  
**Version:** 1.0.0  
**Last Updated:** 2025-10-29

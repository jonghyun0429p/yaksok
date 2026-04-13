# 💊 약속 (Yak-Sok) - 스마트 영양제 관리 및 분석 서비스

> **"당신의 건강한 습관을 위한 확실한 약속"**  
> AI 기반 영양제 병 인식부터 지능형 섭취 알림까지, 개인 맞춤형 영양 관리 솔루션입니다.

---

## 📖 프로젝트 소개 (Introduction)

**약속 (Yak-Sok)**은 사용자가 복잡한 영양제 섭취 일정을 손쉽게 관리하고, 과다 섭취 위험 없는 안전한 건강 생활을 영위할 수 있도록 돕는 웹/모바일 플랫폼입니다.  
최신 **YOLOv11** 기반의 객체 탐지 기술을 활용하여 영양제 병을 자동으로 인식하고, **OCR** 기술을 통해 성분 정보를 분석합니다. 또한, 사용자의 섭취 패턴을 학습하여 최적의 시간에 알림을 제공하는 **지능형 알림 시스템**을 탑재하고 있습니다.

---

## ✨ 주요 기능 (Key Features)

### 1. 🔔 지능형 알림 시스템 (Smart Notification)
**"내 상황에 맞춰 눈치껏 알려주는 똑똑한 영양비서"**
- **스마트 라우팅**: 앱 접속 중엔 조용한 **인앱 토스트**, 비접속 시엔 확실한 **FCM 푸시**로 전환해 알림 피로도를 줄입니다.
- **묶음 발송**: "비타민C 외 2건 섭취 시간입니다." 여러 건의 알림을 한 번에 깔끔하게 묶어 보냅니다.
- **상태 감지**: 화면 활성화 여부(Visible)를 파악해 최적의 알림 방식을 제공합니다.

### 2. 📊 개인 맞춤형 리포트 및 관리
**"단 1초 만에 확인하는 내 영양 밸런스!"**
- **과다 섭취 경고**: 섭취량을 분석하여 권장량 초과나 과다 섭취 위험을 미리 방지해 줍니다.
- **데이터 시각화**: 화려한 인터랙티브 그래프(Recharts)로 영양 상태를 한눈에 파악하세요.
- **초간편 기록**: 드래그 앤 드롭이나 원클릭만으로 오늘의 섭취를 쉽고 트렌디하게 기록할 수 있습니다.

### 3. 🔍 AI 기반 탑티어 영양제 탐지 (AI Vision)
**"귀찮은 영양제 등록? 카메라로 찰칵! 비추기만 하세요."**
- **압도적인 인식률**: 어두운 곳에서도 0.1초 만에 영양제만 정확히 짚어냅니다. (YOLOv11m, 99% 정확도)
- **오인식 철통 방어**: 비슷하게 생긴 텀블러나 컵(Hard Negative)은 완벽히 걸러냅니다.
- **숨은 성분 추출**: OCR 기능으로 라벨의 숨은 성분과 함량까지 자동으로 읽어냅니다.

---

## 🛠 기술 스택 (Tech Stack)

### **Backend**
- **Framework**: Spring Boot (Java)
- **Architecture**: RESTful API
- **Data Access**: JPA / Hibernate
- **Notification Logic**: SSE (Server-Sent Events) + FCM Token Management
- **Database**: MySQL/MariaDB (추정)

### **AI & Data Pipeline**
- **Model**: YOLOv11m (Medium)
- **Language**: Python 3.x
- **Framework**: PyTorch, Ultralytics YOLO
- **Serving**: FastAPI (AI 서버)
- **Preprocessing**: Albumentations (데이터 증강), OpenCV
- **Tools**: COCO Dataset Filtering, Custom Labeling Tools (`auto_label.py`, `review_labels.py`)

### **Frontend**
- **Framework**: Alert Next.js 16 (React 19, TypeScript)
- **Styling**: Tailwind CSS, Framer Motion (애니메이션)
- **PWA**: `@ducanh2912/next-pwa` (앱 수준의 사용자 경험 제공)
- **Notification**: Google Firebase (FCM)
- **Visualization**: Recharts (데이터 시각화)
- **State Management**: Context API & Custom Hooks
- **Network**: Axios

---

## 📂 프로젝트 구조 (Project Structure)

```
S14P11A505/
├── backend/            # Spring Boot 백엔드 소스 코드 (API, DB, 알림 로직)
│   └── yaksok/         # 메인 애플리케이션
├── frontend/           # Next.js 프론트엔드 소스 코드 (UI/UX, PWA)
├── fastapi/            # AI 모델 서빙 및 추론 API (Python)
├── DataPipeLine/       # AI 학습 데이터 구축 및 파이프라인
│   ├── Main_Pipeline/  # 전처리, 라벨링, 학습 스크립트
│   └── PROJECT_REPORT.md # 데이터 파이프라인 상세 리포트
└── README.md           # 프로젝트 메인 문서
```

---

## 🚀 시작하기 (Getting Started)

### Prerequisites
- Node.js > 20.x
- Java JDK 17+
- Python 3.8+
- Docker (Optional)

### Installation

1. **Frontend**
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

2. **Backend**
   ```bash
   cd backend/yaksok
   ./gradlew bootRun
   ```

3. **AI Server**
   ```bash
   cd fastapi
   pip install -r requirements.txt
   uvicorn main:app --reload
   ```

---

## 👨‍💻 팀원 및 기여 (Contributors)

- **Frontend** : 박창희(팀장), 이유정, 허승
- **Backend** : 박종현, 김태희
- **AI** : 박창희
- **Infrastructure** : 하윤철, 박종현
# Yaksok (약속) - Backend

> **당신의 건강한 일상을 지키는 스마트 복약 관리 솔루션, '약속'의 백엔드 저장소입니다.**

---

## 🚀 Service Overview
'약속'은 현대인의 복잡한 복약 일정을 체계적으로 관리하고, 의약품 및 영양제 성분 정보를 바탕으로 안전한 섭취 가이드를 제공하는 서비스입니다. 대량의 공공 데이터를 효율적으로 처리하고, 정교한 알림 시스템과 검색 로직을 통해 사용자 경험을 혁신합니다.

---

## ✨ Key Technical Highlights

### 🔒 Distributed Lock (Consistency)
- **MySQL-based ShedLock**
    - 별도의 Redis 의존성을 추가하는 대신 MySQL을 활용해 **인프라 복잡성**을 최소화했습니다.
    - 다중 인스턴스 환경에서도 배치 작업 및 알림 발송의 **데이터 정합성**을 원자적으로 보장합니다.

### 🛡 Security & Scalability
- **Stateless Auth Strategy**
    - OAuth 2.0와 JWT를 결합한 인증 체계를 구축하여 서버의 확장성을 확보했습니다.
    - Spring Security 필터 체인을 통해 유연하고 세밀한 **역할 기반 권한 관리**를 수행합니다.

### 🔔 Hybrid Notification Architecture
사용자 경험(UX)과 메시지 신뢰성을 모두 고려한 지능형 알림 아키텍처입니다.
- **Active-Passive Fallback**
    - 클라이언트 접속 상태를 실시간 감지하여, 활성 상태 시 **SSE**로 즉시 전달하고 부재 시 **FCM**으로 자동 전환합니다.
- **Intelligent Notification Bundling**
    - 단시간 내 발생하는 여러 알림을 사용자별로 묶어 발송하여 **네트워크 오버헤드**와 **사용자 피로도**를 동시에 낮췄습니다.

### 🧪 Supplement Data Engineering
데이터의 정확도와 분석 성능을 극대화하기 위해 다음의 엔지니어링을 적용했습니다.
- **AI-Driven Data Pipeline**
    - OCR 추출 결과의 노이즈를 LLM으로 실시간 필터링하고 구조화합니다.
    - 미등록 제품을 시스템이 스스로 학습하여 등록하는 **자가 증식형 시나리오**를 구현했습니다.
- **Dynamic Nutrient Aggregation**
    - 복잡한 사용자의 복용 데이터를 쿼리 레벨에서 실시간 집계하고, 식약처 상한치(UL)와 대조 분석합니다.
- **Unit Normalization Engine**
    - `IU`, `mcg` 등 파편화된 단위를 내부 연산 기준으로 **자동 표준화**하여 분석의 정밀도를 보장합니다.
- **Parallel Analysis Engine**
    - `CompletableFuture` 기반 비동기 처리를 통해 대용량 분석 시에도 지연 없는 응답 속도를 제공합니다.

### 🔍 Search & Integration Optimization
- **Similarity Match Search**
    - 단순 키워드 매칭을 넘어 문자열 유사도 알고리즘을 도입, 사용자의 검색 의도를 정확히 파악합니다.
- **Reactive External Integration**
    - WebClient를 활용한 Non-blocking 통신으로 외부 API 및 AI 서버와 효율적으로 연동합니다.

---

## 🏗 Technical Architecture

### Core Design Principles
- **Modularity**: 기능을 도메인별로 분리하여 응집도를 높이고 결합도를 낮춘 패키지 구조를 채택했습니다.
- **Scalability**: 데이터베이스 기반 분산 락과 무상태 인증을 통해 시스템의 수평적 확장성을 고려했습니다.
- **Reliability**: 전역 예외 처리(Global Exception Handling)와 하이브리드 알림 파이프라인으로 서비스 안정성을 확보했습니다.

---

## 🛠 Tech Stack

### Languages & Frameworks
- **Java 17**
- **Spring Boot 3.5.10-SNAPSHOT**
- **Spring Data JPA**
- **Spring Security / OAuth2 / JWT**

### Databases & Infrastructure
- **MySQL**: 관계형 데이터 관리 및 Distributed Lock 저장소
- **Redis**: 캐싱 레이어 활용

### Tools & Others
- **Gradle**: Build Tool
- **Swagger (OpenAPI 3.0)**: API Documentation
- **Firebase Admin SDK**: Push Notifications
- **ShedLock**: Distributed Scheduling Lock

---

## 📁 Directory Structure
```
yaksok
├── src/main/java/com/ssafy/yaksok
│   ├── analyze/       # 성분 및 제품 분석 로직
│   ├── auth/          # 인증 처리 및 토큰 관리
│   ├── disease/       # 질병 관련 도메인
│   ├── facade/        # 복잡한 서비스 로직의 통합 인터페이스
│   ├── global/        # 공통 설정 (Exception, Config, Util)
│   ├── ingredient/    # 성분 정보 관리
│   ├── intake/        # 복약 기록 및 섭취 관리
│   ├── notification/  # FCM 알림 및 스케줄링
│   ├── product/       # 의약품/영양제 제품 관리
│   ├── security/      # 보안 관련 필터 및 설정
│   └── user/          # 사용자 정보 및 프로필 관리
```

---

## 📜 API Documentation
- 애플리케이션 실행 후 아래 경로를 통해 API 명세서를 확인할 수 있습니다.
- `http://localhost:8080/swagger-ui/index.html`

---

## 👨‍💻 Backend Developers
| 박종현 | 하윤철 | 김태희 | 박창희 |
| :---: | :---: | :---: | :---: |
| Backend Lead | Backend Dev | Backend Dev | Backend Dev |
| [Profile](https://github.com) | [Profile](https://github.com) | [Profile](https://github.com) | [Profile](https://github.com) |

---
Copyright © 2024 Yaksok Team. All rights reserved.

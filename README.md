<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=4F8EF7&height=180&section=header&text=임성제&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Backend%20Developer&descAlignY=58&descSize=18&descColor=ffffff" />

<br>

### 트래픽 처리와 시스템 확장성을 고민하며
### 백엔드부터 클라우드 인프라까지 함께 만드는 개발자입니다.

<br>

### 📬 Contact
[![Gmail](https://img.shields.io/badge/seongje00416@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:seongje00416@gmail.com)

### 🐙 GitHub
[![Personal](https://img.shields.io/badge/seongje00416-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/seongje00416)
[![DalGurum](https://img.shields.io/badge/DalGurum-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/dalgurum)

### 🔗 Links
[![Blog](https://img.shields.io/badge/구름위키-FF5722?style=flat-square&logo=tistory&logoColor=white)](https://cloud-wiki.tistory.com)
[![Maven Central](https://img.shields.io/badge/MavenCentral-C71A36?style=flat-square&logo=apachemaven&logoColor=white)](https://central.sonatype.com/namespace/io.github.dalgurum)
</div>

---

## 🛠 Tech Stack

**Backend**

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring WebFlux](https://img.shields.io/badge/Spring_WebFlux-6DB33F?style=flat-square&logo=spring&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-4285F4?style=flat-square&logo=google&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)

**Cloud & Infra**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**Database**

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white)

---

## 🚀 Projects

### ⭐ [Now&Go](https://github.com/seongje00416/now-n-go-be) — 여행 올인원 플랫폼 `2026.01 ~ 2026.03`

> Redis SortedSet 기반 대기열 구현으로 동시 사용자 3,000명 환경에서 에러율 **80% → 0%** 개선

- Redis SortedSet 기반 좌석 선점 대기열 구현으로 DB Connection Pool 고갈 문제 해결
- CQRS 패턴 적용 — Read/Write 서비스 분리로 선택적 Scale-Out 가능한 구조 설계
- MSA 환경에서 분산 보상 트랜잭션 직접 구현으로 고아 데이터 **2개 → 0개**
- Terraform으로 EKS 프로덕션 환경 전체 IaC 구성, GitHub Actions + ArgoCD GitOps CI/CD 구축
- `Spring Boot` `Redis` `PostgreSQL` `AWS EKS` `Kubernetes` `ArgoCD` `Terraform`

<br>

### ⭐ [Fooding](https://github.com/seongje00416/fooding-backend) — 외식업 올인원 플랫폼 `2025.03 ~ 2026.01`

> Redis Cache 도입으로 평균 응답 시간 **43% 감소** (27.52ms → 15.65ms)

- Kafka 기반 웨이팅 예약 동시성 제어 — Redisson 분산락(1차) → Kafka FIFO 대기열(2차) 고도화로 중복 웨이팅 번호 **2개 → 0개**
- Redis 분산 캐시 + `@Cacheable(sync=true)` 적용으로 Cache Stampede 방지
- Spring MVC 환경의 쓰레드 고갈 문제 해결을 위해 WebFlux 기반 `fooding-realtime` 비동기 모듈 분리 개발
- `Spring Boot` `Spring WebFlux` `Redis` `Kafka` `MySQL` `MongoDB`

<br>

### Pool — 숏폼 기반 리퀘스트 매칭 플랫폼 `2025.03 ~ 진행 중`

> AI 기반 장애 분석 시스템 구축으로 트러블슈팅 시간 **2시간 → 20분** 단축

- Security FilterChain에 Claude API 연동 — 예외 발생 시 원인 분석 및 해결 방안을 Discord 웹훅으로 자동 전송
- gRPC + Protobuf 기반 채팅 서비스 구현 — JSON 대비 페이로드 **35% 감소** (126B → 82B), proto를 통한 코드 자동 생성으로 iOS/Android 타입 안전성 확보
- `Spring Boot` `gRPC` `AWS Lambda` `MySQL` `Claude API`

<br>

### 학식로그 — 학식 정보 전달 서비스 `2025.03 ~ 2025.06`

- 30명 규모 팀 PM — MSA 구조 채택 및 EKS 기반 Kubernetes 클러스터 구축
- GitHub Actions + ArgoCD CI/CD 파이프라인 완전 자동화로 개발팀 배포 러닝 커브 제거
- `AWS EKS` `Kubernetes` `ArgoCD` `GitHub Actions`

---

## 💼 Experience

| 기간 | 기관 | 역할 |
|------|------|------|
| 2026.06 ~ 2026.07 | (재)국제인재능력개발원 | 보조 강사 - AWS와 AI를 활용한 MSA 기반 웹서비스 개발 과정 |
| 2025.09 ~ 2026.03 | 메가존 클라우드 | KDT AI·클라우드 네이티브 개발자 양성과정 |
| 2024.03 ~ 2024.08 | 네이버 클라우드 | 인턴 — 기술 문의 대응 및 서비스 가이드 개선 |
| 2020.07 ~ 2020.10 | ㈜스프레틱스 | 서버 개발자 — 원격 교육 플랫폼 개발 및 인프라 관리 |

---

## 🏅 Certifications

| 자격증 | 발급처 |
|--------|--------|
| OPIc IM | ACTFL |
<!--
| 정보처리기사 | 한국산업인력공단 |
| AWS SAA | Amazon Web Services |
| SQLD | 한국데이터산업진흥원 |
-->


---

## 🎓 Education

**명지대학교** 융합소프트웨어학부 응용소프트웨어 전공 `2019.03 ~ 2025.08`

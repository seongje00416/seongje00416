<h1 align="center"> 🚀 신뢰를 최우선하는 엔지니어, 임성제입니다. 🚀 </h1>
<br/>
<h3 align="center"> To Improve Service Reliability... </h3>
<p align="center"> <strong>비동기 처리</strong>를 활용한 트래픽 분산 / 인메모리 저장소를 활용한 <strong>DB 부하</strong>를 고려한 설계 및 개발 </p>
<h3 align="center"> To Prove My Reliability... </h3>
<p align="center"> 작업을 최소 단위로 분할해 데일리 목표를 정해 완수하고 지속적인 소통을 통해 원활한 협업을 주도 </p>
<br/><br/>

## 📫 Contact & Channels
[<img src="https://img.shields.io/badge/LIM SEONGJE-%23181717.svg?style=for-the-badge&logo=github&logoColor=white"/>](https://github.com/seongje00416) [<img src="https://img.shields.io/badge/DalGurum-%23181717.svg?style=for-the-badge&logo=github&logoColor=white"/>](https://github.com/dalgurum)
[<img src="https://img.shields.io/badge/tistory-%23000000.svg?style=for-the-badge&logo=tistory&logoColor=white"/>](https://cloud-wiki.tistory.com)
[<img src="https://img.shields.io/badge/gmail-%23EA4335.svg?style=for-the-badge&logo=gmail&logoColor=white"/>](seongje00416@gmail.com)
[<img src="https://img.shields.io/badge/dalgurum-0e75b6.svg?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAES0lEQVR42u2WSW8bRxCFv+6e6Vm4S6ZkLVacBDDgQ/L/f0QucWDA..."/>](https://dalgurum.cloud/)

<br/><br/>

## 🛠️ Tech Stacks
<p align="left">
  <img src="https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/springboot-%236DB33F.svg?style=for-the-badge&logo=spring-boot&logoColor=white"/>
  <img src="https://img.shields.io/badge/redis-%23DC382D.svg?style=for-the-badge&logo=redis&logoColor=white"/>
  <img src="https://img.shields.io/badge/kafka-%23231F20.svg?style=for-the-badge&logo=apachekafka"/>
  <img src="https://img.shields.io/badge/mysql-%234479A1.svg?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/claude-%23D97757.svg?style=for-the-badge&logo=claude&logoColor=white"/>
  <img src="https://img.shields.io/badge/aws-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white"/>
  <img src="https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/kubernetes-%23326CE5.svg?style=for-the-badge&logo=kubernetes&logoColor=white"/>
</p><br/>

## 🎯 Core Experience
### 1. 조회 트래픽의 DB 인입 차단 설계
 
- **Issue:** 게시글 조회 요청에 DB 작업이 집중되어, 트래픽 증가 시 응답 지연과 커넥션 풀 고갈이 예상됨
- **Action:**
  - 동시에 요청되는 작업의 성격을 분리 — 조회수는 **Redis INCR 집계 후 배치 일괄 반영**, 수정 빈도가 낮은 상세 데이터는 **캐싱 + TTL**, 나머지만 DB 조회
  - 캐시 미스 시 **분산 락**으로 단 하나의 요청만 DB에 접근시키고 나머지는 대기 후 캐시 조회 (Cache Stampede 방어)
  - 대기 사용자의 체감 속도를 일부 내주고 DB 안정성을 확보하는 트레이드오프로 판단
- **Result:** 게시글 조회 **평균 응답 시간 44.4% 감소** (동시 사용자 5,000명 기준)
  <br/>동시 접속 15,000명 가정 시나리오에서 **커넥션 풀 고갈 없이 동작**
  <br/>※ 측정은 직접 개발한 API 엔드포인트 테스터를 통해 측정( [Dalgurum API Tester](https://github.com/dalgurum/dalgurum-api-performance-tester) )
### 2. 동시 요청 폭주 구간의 대기열 제어
 
- **Issue:** 예약 오픈 시점에 요청이 집중되며 DB 커넥션 풀이 고갈 우려 발생
- **Action:**
  - **Redis SortedSet** 기반 대기열을 앞단에 배치하고 **2초당 50명** 스로틀로 진입 제어
  - 대기열을 상품별로 분리하고 **분산 락(비관적 락)** 을 적용해 대기번호 발급과 예약 확정의 원자성 확보
- **Result:** **에러율 80% → 0%**
  <br/>동시 3,000명 시나리오에서 **대기번호 중복률 0%, 중복 예약률 0%**
### 3. 분산 환경에서의 데이터 정합성 보장
 
- **Issue:** 마이크로서비스 분리에 따라 서비스 간 트랜잭션 일관성이 깨질 우려
- **Action:**
  - **오케스트레이션 방식의 Saga 패턴**을 도입해 보상 트랜잭션을 설계하고 실패 시 롤백 프로세스를 자동화
  - 검증을 위해 **데이터 서비스 파드를 의도적으로 중지**시켜 장애 상황을 재현
  - 웨이팅 대기열은 Caffeine → Redis + 분산 락 → **Kafka(`store_id` 파티션 키)** 순으로 개선하며 순서 보장까지 확보
- **Result:** 작업 실패 상황에서도 **고아 데이터 잔존률 0%**
  <br/>대기열 **중복 발생률 2% → 0%**, **순서 불일치율 11% → 0%**
### 4. MSA 프로젝트의 배포 파이프라인 구축
 
- **Issue:** 6개 개발팀이 독립 개발하는 EKS 환경에서, 서비스별 매니페스트 작성·검증·배포에 **건당 2시간**이 소요되며 인프라팀에 반복 요청이 누적
- **Action:**
  - **GitHub Actions + Helm Chart + ArgoCD(GitOps)** 파이프라인을 구성해 `deploy` 브랜치 merge만으로 클러스터에 반영되는 구조 설계
  - 시크릿 하드코딩 여부, 환경 변수 선언, 엔드포인트 컨벤션을 **PR 단계에서 검증**하는 리뷰 기준 정의
  - 팀 전원이 MSA 인프라 경험이 없어, PM으로서 **주 1회 스터디를 직접 주도**하고 학습 내용을 문서로 축적
- **Result:** 배포 소요 **시간 소모 0분**, 인프라팀의 수동 배포 공수 제거
  <br/>6개 팀이 독립 개발해도 하나의 서비스로 동작하는 환경 확보, 팀원 전원이 K8s 기반 기본 트러블슈팅 가능 수준 도달
### 5. AI를 활용한 개발 환경 고도화
 
- **Issue:** 개발 과정에서 반복 작업과 시간이 오래 걸리는 작업이 자주 발생
- **Action:**
  - 반복되는 개발 병목은 도구로 해결 — Swagger 문서에서 시나리오를 추출해 **k6 스크립트를 자동 생성·실행**하는 부하 테스터 개발
  - 에러 로그를 분석해 팀 메신저로 원인과 해결책을 전달하는 **모니터링 에이전트**(동일 패턴 10분 내 재호출 차단으로 비용 통제) 개발
  - **n8n**을 활용한 코드 리뷰 자동화
- **Result:** 엔드포인트 1개 부하 테스트 **30분 → 5분**, 트러블슈팅 소요 **2시간 → 20분**

<br/>

## 💼 Projects
- [Constella](https://github.com/dalgurum/dalgurum-constella) — Kafka 기반 모더레이션 비동기 파이프라인 + Redis 분산 처리
- [Now&Go](https://github.com/seongje00416/now-n-go-be) — 64개 분산 마이크로서비스 + 분산 트랜잭션 + Redis ZSet 대기열
- [Fooding](https://github.com/seongje00416/fooding-backend) — WebFlux+SSE 실시간 알림 모듈 + 하네스 파이프라인
- [Dalgurum API Tester](https://github.com/dalgurum/dalgurum-api-performance-tester) — k6 + Claude 기반 자동 부하 테스트 실행기
- [Pool]() — AI 기반 트러블슈팅 파이프라인 + Spring Boot 기반 REST API
- [명식당](https://github.com/orgs/TP1-OuterMSA/repositories) — EKS 기반 MSA 인프라 +  CI/CD

<br/>

## ⚡ Development Activity
| 활동 | 역할 | 내용 | 링크 | 기간 |
| --- | --- | --- | --- | --- |
| Dalgurum 플랫폼 운영 | 개발 · 운영 | AI 에이전트 팀과 함께하는 개인 서비스 개발 플랫폼 운영 | [달구름]() | 2026.06 ~ |
| Igniter 협업 팀 합류 | 백엔드 개발 · AX 담당 | 개발 프로젝트를 진행하는 협업 팀 | [Igniter]() | 2025.03 ~ |
| Pool 팀 합류 | 서버 개발 | 서비스 런칭을 위한 프로젝트 팀 | - | 2025.04 ~ |
| 한이음 ICT 프로젝트 참여 | 서버 개발 · 인프라 구축 | 모바일-라즈베리파이 사이 통신을 위한 서버 개발 | - | 2022.03 ~ 2022.11 |

<br/>




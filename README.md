<h1 align="center"> 🚀 신뢰를 최우선하는 백엔드 개발자, 임성제입니다. 🚀 </h1>
<br/>
<h3 align="center"> To Improve Service Reliability... </h3>
<p align="center"> <strong>비동기 처리</strong>를 활용한 트래픽 분리 + 인메모리 저장소를 활용한 <strong>DB 부하</strong>를 고려한 설계 및 개발 </p>
<h3 align="center"> To Prove My Reliability... </h3>
<p align="center"> 작업을 최소 단위로 분할해 데일리 목표를 정해 완수하고 지속적인 소통을 통해 원활한 협업을 주도 </p>
<br/><br/><br/><br/>

## 🛠️ Tech Stacks & Ecosystem
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
### 1. Kafka 기반 비동기 모더레이션 파이프라인 구축
- **Issue:** 콘텐츠 검수 로직이 추가되면서 사용자 API 응답 속도가 급격히 지연되는 현상 발생
- **Action:** 
  - 검수 로직을 메인 트랜잭션에서 분리하고 **Apache Kafka**를 도입하여 비동기 이벤트 기반 구조로 전환
  - 컨슈머 그룹 및 파티션 설정을 최적화하여 이벤트 유실 방지 및 처리 속도 향상
- **Result:** 파이프라인 추가로 인한 콘텐츠 등록 작업의 **응답 시간 지연율을 3% 미만**으로 방어
### 2. 분산 환경에서의 데이터 정합성 보장
- **Issue:** 마이크로서비스 구조 분리에 따른 트랜잭션 일관성 깨짐 우려
- **Action:**
  - **오케스트레이터 방식의 Saga 패턴**을 도입하여 각 서비스 간 보상 트랜잭션을 설계하고 실패 시 롤백 프로세스 자동화
- **Result:** 작업 실패 상황에서도 **고아 데이터 잔존률 0%** 달성
### 3. Redis를 통한 DB 인입 트래픽 분산 처리
- **Issue:** 자주 발생하는 게시글 조회 과정에서 필요한 DB 작업이 많아 DB 트래픽 과부하 우려 및 조회 시간 지연
- **Action:** 
  - 조회수 Update 작업에 필요한 값을 Redis에 저장해두었다 배치 함수를 통해 일괄 처리
  - 수정이 자주 일어나지 않는 게시글 상세 데이터를 Redis에서 캐싱 처리
- **Result:** 게시글 조회에 대한 **응답 시간 44.4%** 감소

<br/>

## 💼 Projects
- [Constella](https://github.com/dalgurum/fooding) — Kafka 기반 모더레이션 비동기 파이프라인 + Redis 분산 처리
- [Now&Go](https://github.com/dalgurum/now-and-go) — 64개 분산 마이크로서비스 + 분산 트랜잭션 + Redis ZSet 대기열
- [Fooding](https://github.com/dalgurum/fooding) — WebFlux+SSE 실시간 알림 모듈 + 하네스 파이프라인
- [Dalgurum API Tester](https://github.com/dalgurum/fooding) — k6 + Claude 기반 자동 부하 테스트 실행기
- [Pool](https://github.com/dalgurum/pool) — AI 기반 트러블슈팅 파이프라인 + Spring Boot 기반 REST API
- [명식당](https://github.com/dalgurum/fooding) — EKS 기반 MSA 인프라 +  CI/CD

<br/>

## ⚡ Development Activity
| 활동 | 역할 | 내용 | 링크 | 기간 |
| --- | --- | --- | --- | --- |
| Dalgurum 플랫폼 운영 | 개발 · 운영 | AI 에이전트 팀과 함께하는 개인 서비스 개발 플랫폼 운영 | [달구름]() | 2026.06 ~ |
| Igniter 협업 팀 합류 | 백엔드 개발 · AX 담당 | 개발 프로젝트를 진행하는 협업 팀 | [Igniter]() | 2025.03 ~ |
| Pool 팀 합류 | 서버 개발 | 서비스 런칭을 위한 프로젝트 팀 | - | 2025.04 ~ |
| 한이음 ICT 프로젝트 참여 | 서버 개발 · 인프라 구축 | 모바일-라즈베리파이 사이 통신을 위한 서버 개발 | - | 2022.03 ~ 2022.11 |

<br/>

## 📫 Contact & Channels
[<img src="https://img.shields.io/badge/LIM SEONGJE-%23181717.svg?style=for-the-badge&logo=github&logoColor=white"/>](https://github.com/seongje00416) [<img src="https://img.shields.io/badge/DalGurum-%23181717.svg?style=for-the-badge&logo=github&logoColor=white"/>](https://github.com/dalgurum)
[<img src="https://img.shields.io/badge/tistory-%23000000.svg?style=for-the-badge&logo=tistory&logoColor=white"/>](https://cloud-wiki.tistory.com) [<img src="https://img.shields.io/badge/velog-%2320C997.svg?style=for-the-badge&logo=velog&logoColor=white"/>](https://velog.io/@seongje00416/posts)
[<img src="https://img.shields.io/badge/gmail-%23EA4335.svg?style=for-the-badge&logo=gmail&logoColor=white"/>](seongje00416@gmail.com)
[<img src="https://img.shields.io/badge/dalgurum-0e75b6.svg?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAES0lEQVR42u2WSW8bRxCFv+6e6Vm4S6ZkLVacBDDgQ/L/f0QucWDA..."/>](https://dalgurum.cloud/)



<div align="center">

<img width="150" alt="image-Photoroom (3)" src="https://github.com/user-attachments/assets/2d48bec2-a27d-4488-8382-0c5543adb7fa" />

# 티켓을 JAVA라

### 대규모 트래픽에서도 공정한 예매를 보장하는 티켓팅 플랫폼

**공정한 선착순 · 정확한 재고 · 빠른 검색 · 실시간 CS**

**TEAM HOT6**

[![API](https://img.shields.io/badge/API-Swagger-85EA2D?style=for-the-badge\&logo=swagger\&logoColor=black)](#)
[![Docs](https://img.shields.io/badge/Docs-Project-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/6team-Plus-project-sparta/docs)
[![GitHub](https://img.shields.io/badge/Repository-Ticket_JAVARA-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/6team-Plus-project-sparta/Ticket_JAVARA)
</div>

---

## 목차

* [프로젝트 정보](#프로젝트-정보)
* [Getting Started](#getting-started)
* [프로젝트 비전](#프로젝트-비전)
* [주요 기능](#주요-기능)
* [사용자 시나리오](#사용자-시나리오)
* [팀 구성](#팀-구성)
* [개발 기간](#개발-기간)
* [기술 스택](#기술-스택)
* [시스템 아키텍처](#시스템-아키텍처)
* [대표 문서](#대표-문서)
* [향후 업데이트 계획](#향후-업데이트-계획)
* [라이선스 및 문의](#라이선스-및-문의)

---

## 프로젝트 정보

| 항목            | 내용                                                          |
| ------------- | ----------------------------------------------------------- |
| **팀명**        | **HOT6**                                                    |
| **프로젝트명**     | **티켓을 JAVA라**                                               |
| **플랫폼명**      | **티켓을 JAVA라** — 공연·스포츠 티켓팅 플랫폼                             |
| **버전**        | v1.0.0 (MVP)                                                |
| **개발 기간**     | 3주 (설계 3일 · 개발 2주 · QA/배포 1주)                               |
| **팀 구성**      | 백엔드 개발자 5명                                                  |
| **프로덕션 URL**  | **Frontend**: 추후 연결<br>**Backend API**: 추후 연결               |
| **로컬 개발 URL** | **Backend**: [http://localhost:8080](http://localhost:8080) |

---

## Getting Started

### 백엔드 실행

```bash
./gradlew bootRun
# http://localhost:8080
```

### 문서

### 요구사항 및 기획

* [프로젝트 개요서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/1.%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EA%B0%9C%EC%9A%94%EC%84%9C.md)  
* [사용자 시나리오](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/2.%20%EC%82%AC%EC%9A%A9%EC%9E%90%20%EC%8B%9C%EB%82%98%EB%A6%AC%EC%98%A4.md)  
* [유스케이스 명세서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/3.%20%EC%9C%A0%EC%8A%A4%EC%BC%80%EC%9D%B4%EC%8A%A4%20%EB%AA%85%EC%84%B8%EC%84%9C.md)  
* [기능 명세서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/4.%20%EA%B8%B0%EB%8A%A5%20%EB%AA%85%EC%84%B8%EC%84%9C.md)  

---

## 프로젝트 비전

티켓팅 서비스의 핵심은 단순한 예매 기능이 아니라, **극단적 트래픽 집중 상황에서도 공정성과 정합성을 지키는 것**입니다.

인터파크, 멜론티켓, YES24 티켓 같은 기존 서비스에서는 오픈 직후 다음과 같은 문제가 반복적으로 발생합니다.

* 동일 좌석에 대한 **중복 예매**
* 선착순 쿠폰의 **수량 초과 발급**
* 인기 공연 검색 시 **느린 응답 속도**
* 오픈 직후 폭증하는 요청으로 인한 **서버 과부하**

티켓을 JAVA라는 이러한 문제를 해결하기 위해, 단순 CRUD 구현을 넘어서 **동시성 제어 · 캐시 전략 · 배포 자동화**를 핵심 주제로 삼았습니다.

### 우리가 해결하려는 문제

**1. 좌석 예매의 공정성**

* 좌석 선택 후 결제 단계에서 다른 사용자에게 좌석을 빼앗기는 문제
* 대량 동시 요청 상황에서 동일 좌석이 여러 번 판매되는 문제

**2. 쿠폰 발급의 정합성**

* 선착순 쿠폰이 실제 수량보다 더 많이 발급되는 Race Condition
* 예매 도중 쿠폰 사용 상태가 꼬이는 문제

**3. 검색 경험의 성능**

* 인기 이벤트 탐색 과정에서 반복되는 느린 조회
* 정렬·필터 조건이 많아질수록 악화되는 응답 속도

**4. 실제 운영 가능한 서비스 구조**

* 로컬에서만 동작하는 데모가 아니라, AWS 배포와 CI/CD까지 고려한 구조
* 문제 발생 시 빠르게 대응할 수 있는 실시간 CS 채팅 기능

### 핵심 가치 제안

| 가치            | 설명                                               |
| ------------- | ------------------------------------------------ |
| **공정한 선착순**   | Redis 분산락과 좌석 Hold로 중복 예매 없는 예매 플로우 보장           |
| **정확한 재고 관리** | 쿠폰 발급·사용 시 동시성 제어로 초과 발급 및 중복 사용 방지              |
| **빠른 검색 경험**  | Caffeine 로컬 캐시 + Redis 캐시 + 인기 검색어로 탐색 속도 개선     |
| **운영 가능한 구조** | Docker, AWS, GitHub Actions 기반으로 실제 배포 가능한 환경 구축 |
| **빠른 고객 대응**  | WebSocket 기반 실시간 CS 채팅과 FAQ 챗봇으로 문의 응답 속도 향상     |

> 티켓을 JAVA라는 “티켓팅 서비스에서 실제로 터지는 문제를 백엔드 관점에서 해결한다”는 목표로 시작한 프로젝트입니다.

---

## 주요 기능

### 1. 회원 관리

* 회원가입 / 로그인 / 로그아웃
* JWT 기반 인증 / 인가
* 내 정보 조회 / 수정
* 비밀번호 변경
* 내 예매 내역 목록 조회
* 내 예매 상세 조회
* 찜한 이벤트 등록 / 해제 / 조회
* 최근 본 이벤트 조회
* 회원 등급 관리 (BASIC ~ VIP)

### 2. 이벤트 관리

* 공연 / 스포츠 이벤트 등록
* 이벤트 목록 조회
* 이벤트 상세 조회
* 이벤트 수정 / 삭제
* 카테고리별 조회
* 이벤트명 / 장르 검색
* 검색 결과 페이징
* 구역 관리
* 좌석 생성 / 조회 / 상태 관리
* 인기 검색어 Top 10
* 검색 캐싱 (v1 → v2 Caffeine → v2 Redis)

### 3. 예매 관리

* 좌석 상태 조회
* 좌석 선택 및 임시 점유(Hold)
* 티켓 예매 요청
* 예매 확정
* 예매 취소
* Mock PG 결제 연동
* 결제 성공 / 실패 처리
* 좌석 동시성 제어
* 재고 정합성 보장

### 4. 프로모션 및 CS

* 선착순 쿠폰 발급
* 쿠폰 목록 조회
* 쿠폰 적용
* 쿠폰 사용 여부 관리
* 쿠폰 중복 사용 방지
* 쿠폰 재고 동시성 제어
* 등급별 쿠폰 발급 조건 관리
* 사용자 등급 기반 쿠폰 발급 제한
* 실시간 CS 채팅
* FAQ 기반 챗봇
* 고객 문의 등록 / 조회
* 관리자 답변 처리
* 문의 상태 관리 (대기 / 진행 / 완료)

### 5. 관리자 기능

* 관리자 로그인 및 권한 관리
* 관리자용 이벤트 등록 / 수정 / 삭제
* 관리자용 구역 / 좌석 관리
* 관리자용 예매 현황 조회
* 관리자용 쿠폰 발급 현황 조회
* 관리자용 CS 문의 관리 / 답변
* 쿠폰 생성 시 적용 등급 설정

---

## 사용자 시나리오

### 페르소나 설계 원칙

티켓을 JAVA라의 페르소나는 단순한 가상 사용자가 아니라, **우리가 왜 이 기능을 구현해야 하는지 설명해 주는 기준**입니다. 각 페르소나의 Pain Point는 그대로 우리 시스템의 기술 과제로 연결됩니다.

| 페르소나                | 핵심 연결 기능                    |
| ------------------- | --------------------------- |
| **박서준** — 티켓팅 전사    | 좌석 Hold, Redis 분산락, 어뷰징 방지  |
| **김하늘** — 탐색형 사용자   | 검색 캐싱, 인기 검색어, DB 인덱스 최적화   |
| **이도현** — 알뜰한 첫 직장인 | 쿠폰 발급 동시성, 쿠폰 사용 정합성, CS 채팅 |

### 1. 페르소나 — 박서준

| 항목 | 내용                                                 |
| -- | -------------------------------------------------- |
| 이름 | 박서준                                                |
| 나이 | 27세                                                |
| 직업 | 대기업 마케팅팀 사원                                        |
| 특징 | 인기 콘서트 티켓 오픈 시간에 맞춰 노트북과 스마트폰을 동시에 켜두는 전형적인 티켓팅 전사 |

**Goal**

> 원하는 좌석을 공정하게, 확실하게 확보하고 싶다.

**Pain Point**

* 좌석 선택 후 결제창까지 갔는데 이미 판매 완료 메시지가 뜨는 문제
* 동일 좌석에 여러 사용자가 몰릴 때 공정하게 선점되지 않는 문제
* 결제 도중 점유한 좌석이 풀려버리는 문제

#### 주요 사용 시나리오

**시나리오 1-1. 콘서트 티켓 오픈 직후 좌석 선점**

```text
1. 서준이는 이벤트 상세 페이지에서 대기한다.
2. 오픈과 동시에 원하는 좌석을 클릭한다.
3. 서버는 Redis 분산락을 획득한다.
4. Hold 키를 Redis에 저장하고 TTL 5분을 설정한다.
5. 사용자는 결제 단계로 진입한다.
6. 결제 완료 웹훅 수신 후 Hold 유효성을 검증한다.
7. 유효하면 booking을 CONFIRMED로 확정한다.
```

→ 기술 연결: Redis 분산락, Hold TTL, Mock PG 웹훅, 좌석 상태 머신

**시나리오 1-2. 동시 접속자와의 좌석 경쟁**

```text
1. 1,000명이 동시에 같은 좌석을 선택한다.
2. 분산락으로 단 1명만 Hold 획득에 성공한다.
3. 나머지 사용자는 즉시 실패 응답을 받고 다른 좌석을 선택한다.
```

→ 기술 연결: Fail Fast 전략, 직렬 처리, 중복 예매 방지

**시나리오 1-3. Hold 만료 후 좌석 자동 해제**

```text
1. 사용자가 좌석을 Hold한 뒤 결제를 진행하지 못한다.
2. Redis TTL이 만료되면 Hold 키가 자동 삭제된다.
3. 좌석은 다시 AVAILABLE 상태로 복귀한다.
4. 이후 결제 완료 웹훅이 와도 Hold가 만료되었다면 예매를 실패 처리한다.
```

→ 기술 연결: TTL 자동 만료, Race Condition 처리, 상태 전이 관리

---

### 2. 페르소나 — 김하늘

| 항목 | 내용                                                 |
| -- | -------------------------------------------------- |
| 이름 | 김하늘                                                |
| 나이 | 34세                                                |
| 직업 | IT기업 UX 디자이너                                       |
| 특징 | 특정 공연을 미리 정하기보다 장르·날짜·가격 조건으로 여러 공연을 탐색하며 비교하는 사용자 |

**Goal**

> 내 취향에 맞는 공연을 빠르게 찾고 비교하고 싶다.

**Pain Point**

* 검색 결과가 느려서 탐색 자체가 피로한 문제
* 인기 공연 트렌드를 한눈에 알기 어려운 문제
* 정렬과 필터 조합이 많을수록 응답 시간이 길어지는 문제

#### 주요 사용 시나리오

**시나리오 2-1. 장르별 공연 탐색 및 캐시 히트**

```text
1. 하늘이는 '뮤지컬'을 검색한다.
2. 첫 요청에서는 DB를 조회하고 결과를 캐시에 저장한다.
3. 같은 조건으로 다시 조회하면 캐시 히트가 발생한다.
4. 사용자는 DB 재조회 없이 빠르게 다음 페이지를 탐색한다.
```

→ 기술 연결: Caffeine @Cacheable, 캐시 키 설계, 검색 v2 API

**시나리오 2-2. 인기 검색어로 트렌드 파악**

```text
1. 사용자가 메인 화면에 진입한다.
2. Redis ZSet 기반 인기 검색어 Top 10을 조회한다.
3. 인기 검색어를 클릭하면 해당 키워드로 자동 검색한다.
4. 검색 시 ZINCRBY로 점수를 올려 실시간 랭킹을 갱신한다.
```

→ 기술 연결: Redis ZSet, 실시간 순위 반영, 인기 검색어 API

**시나리오 2-3. 복합 조건 검색과 인덱스 최적화**

```text
1. 사용자는 서울 / 이번 달 / 5만원 이하 / 뮤지컬로 검색한다.
2. 인덱스 미적용 시 Full Table Scan이 발생한다.
3. EXPLAIN 분석 후 복합 인덱스를 적용한다.
4. 응답 시간을 줄이고 탐색 이탈을 방지한다.
```

→ 기술 연결: EXPLAIN 분석, 복합 인덱스, v1-v2 성능 비교

---

### 3. 페르소나 — 이도현

| 항목 | 내용                                          |
| -- | ------------------------------------------- |
| 이름 | 이도현                                         |
| 나이 | 24세                                         |
| 직업 | 중소기업 경영지원팀 신입사원                             |
| 특징 | 할인 쿠폰과 프로모션에 민감하며, 문제가 생기면 바로 CS 문의를 넣는 사용자 |

**Goal**

> 쿠폰을 놓치지 않고 가장 저렴하게 티켓을 사고 싶다.

**Pain Point**

* 선착순 쿠폰이 수량보다 더 많이 발급되는 문제
* 예매 중 쿠폰 사용 상태가 꼬여 결제 실패로 이어지는 문제
* 문의를 넣어도 실시간으로 해결받기 어려운 문제

#### 주요 사용 시나리오

**시나리오 3-1. 선착순 할인 쿠폰 발급 경쟁**

```text
1. 500명이 동시에 100장 한정 쿠폰 발급을 요청한다.
2. Redis 분산락으로 잔여 수량을 확인하고 차감한다.
3. 100번째까지는 성공, 이후 요청은 소진 응답을 반환한다.
```

→ 기술 연결: coupon 락, 동시성 테스트, 재고 초과 발급 방지

**시나리오 3-2. 쿠폰 적용 + 티켓 예매 통합 플로우**

```text
1. 사용자가 좌석을 Hold한다.
2. 보유 쿠폰을 선택해 적용한다.
3. 결제 요청 시 Hold 유효성과 쿠폰 유효성을 함께 검증한다.
4. 웹훅 수신 후 booking 확정, coupon 상태 USED 처리, Hold 삭제를 같은 플로우에서 처리한다.
```

→ 기술 연결: 락 획득 순서 고정, 쿠폰 정합성, 웹훅 확정 처리

**시나리오 3-3. 예매 문제 발생 후 실시간 CS 채팅**

```text
1. 결제는 되었지만 예매 내역이 보이지 않는다.
2. 사용자는 문의하기 버튼으로 채팅방에 입장한다.
3. WebSocket(STOMP) 연결 후 관리자와 실시간으로 대화한다.
4. 관리자가 상태를 확인하고 수동 보정 후 결과를 즉시 안내한다.
```

→ 기술 연결: WebSocket, STOMP, 1:1 채팅, 빠른 장애 대응

---

## 팀 구성

| 역할                | 이름      | 주요 담당 기능                                                               |
| ----------------- | ------- | ---------------------------------------------------------------------- |
| **Infra**     | **정태규** | Docker 기반 개발·실행 환경 구성, AWS 인프라 구성, GitHub Actions CI/CD, DB 인덱스 최적화 지원 |
| **Booking**   | **이지민** | 좌석 상태 조회, 좌석 선택, 좌석 Hold, 티켓 예매/취소, Mock PG 결제 연동, 예매 동시성 제어           |
| **Event**     | **선경안** | 공연·스포츠 이벤트 CRUD, 이벤트 상세/검색, 구역·좌석 관리, 검색 캐싱, 인기 검색어                    |
| **Promotion** | **강태훈** | 선착순 쿠폰 발급/적용, 쿠폰 중복 사용 방지, 쿠폰 재고 동시성 제어, 실시간 CS 채팅, FAQ 챗봇             |
| **User**      | **임하은** | 회원가입/로그인, JWT 인증/인가, 내 정보 관리, 찜, 최근 본 내역, 내 예매 내역/상세 조회, 회원 등급 관리      |

### 팀 특징

**도메인 분리 기반 협업**

* User / Event / Booking / Promotion / Infra로 책임을 분리해 병렬 개발이 가능하도록 설계
* 예매와 쿠폰처럼 충돌 가능성이 높은 영역은 락 획득 순서와 책임 범위를 문서화해 구현 충돌을 줄임

**핵심 도전 과제 중심 프로젝트**

* Booking: 좌석 Hold와 분산락으로 중복 예매 방지
* Promotion: 쿠폰 발급/사용 정합성 보장
* Event: 검색 성능 개선과 인기 검색어 구현
* Infra: 실제 배포 가능한 개발/운영 환경 구축

**협업 포인트**

* Infra → Event: 인프라 안정화 후 인덱스 최적화 지원
* Booking → Promotion: 예매 플로우 내 쿠폰 적용 시 락 순서 및 확정 타이밍 협의

---

## 개발 기간

**3주 (설계 3일 · 개발 2주 · QA/배포 1주)**

| Sprint                   | 기간              | 주요 내용                                                                           |
| ------------------------ | --------------- | ------------------------------------------------------------------------------- |
| **Week 1. Planning**     | Day 1 ~ Day 7   | SA 문서 작성, ERD 확정, API 명세 작성, Docker 환경 구성, 회원·이벤트·예매 기본 CRUD 구현                 |
| **Week 2. Core Feature** | Day 8 ~ Day 14  | 좌석 Hold, Redis 분산락, 쿠폰 발급 동시성 제어, 검색 v1/v2(Caffeine), 인기 검색어, Mock PG 웹훅, CS 채팅 |
| **Week 3. QA & Deploy**  | Day 15 ~ Day 21 | Redis 캐시 전환, DB 인덱스 최적화, 성능 테스트, AWS 배포, GitHub Actions CI/CD, QA 및 발표 준비       |

---

## 기술 스택

### 백엔드

| 구분                    | 기술                                                                                                                                                                                                                                           |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **언어**                | ![Java](https://img.shields.io/badge/Java-17-007396?style=for-the-badge\&logo=openjdk\&logoColor=white)                                                                                                                                      |
| **프레임워크**             | ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=for-the-badge\&logo=springboot\&logoColor=white)                                                                                                                  |
| **ORM**               | ![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-59666C?style=for-the-badge\&logo=hibernate\&logoColor=white) ![QueryDSL](https://img.shields.io/badge/QueryDSL-5.x-0078D4?style=for-the-badge)                           |
| **인증**                | ![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=for-the-badge\&logo=springsecurity\&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge\&logo=jsonwebtokens\&logoColor=white) |
| **로컬 캐시**             | ![Caffeine](https://img.shields.io/badge/Caffeine-00897B?style=for-the-badge)                                                                                                                                                                |
| **분산락 / Redis 클라이언트** | ![Lettuce](https://img.shields.io/badge/Lettuce-DC382D?style=for-the-badge\&logo=redis\&logoColor=white) ![Redisson](https://img.shields.io/badge/Redisson-Challenge-red?style=for-the-badge)                                                |
| **실시간 통신**            | ![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=for-the-badge) ![STOMP](https://img.shields.io/badge/STOMP-6DB33F?style=for-the-badge)                                                                                      |

### 데이터베이스

| 구분             | 기술                                                                                                     |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| **RDBMS**      | ![MySQL](https://img.shields.io/badge/MySQL-8-4479A1?style=for-the-badge\&logo=mysql\&logoColor=white) |
| **캐시 / 락 저장소** | ![Redis](https://img.shields.io/badge/Redis-7-DC382D?style=for-the-badge\&logo=redis\&logoColor=white) |

### 인프라 및 배포

| 구분         | 기술                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **컨테이너**   | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge\&logo=docker\&logoColor=white) ![Docker Compose](https://img.shields.io/badge/Docker%20Compose-2496ED?style=for-the-badge\&logo=docker\&logoColor=white)                                                                                                                                                                                                                       |
| **클라우드**   | ![AWS EC2](https://img.shields.io/badge/AWS-EC2-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white) ![RDS](https://img.shields.io/badge/AWS-RDS-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white) ![ElastiCache](https://img.shields.io/badge/AWS-ElastiCache-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white) ![ECR](https://img.shields.io/badge/AWS-ECR-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white) |
| **CI/CD**  | ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge\&logo=githubactions\&logoColor=white)                                                                                                                                                                                                                                                                                                                        |
| **시크릿 관리** | ![GitHub Secrets](https://img.shields.io/badge/GitHub%20Secrets-181717?style=for-the-badge\&logo=github\&logoColor=white) ![AWS Parameter Store](https://img.shields.io/badge/AWS-Parameter%20Store-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white)                                                                                                                                                                                        |

### 협업 도구

| 구분          | 기술                                                                                                                                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **버전 관리**   | ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge\&logo=git\&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge\&logo=github\&logoColor=white) |
| **API 문서화** | ![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge\&logo=swagger\&logoColor=black)                                                                                             |
| **테스트**     | ![JUnit5](https://img.shields.io/badge/JUnit5-25A162?style=for-the-badge\&logo=junit5\&logoColor=white) ![Mockito](https://img.shields.io/badge/Mockito-000000?style=for-the-badge)                    |

---

## 시스템 아키텍처

### 전체 구조 (프로덕션 기준)

```text
[사용자]
   ↓ HTTPS
[Nginx / Reverse Proxy]
   ↓
[Spring Boot Application]
   ├─ User Domain
   ├─ Event Domain
   ├─ Booking Domain
   ├─ Promotion Domain
   ├─ Admin Domain
   │
   ├─ Redis
   │   ├─ 좌석 Hold TTL
   │   ├─ 분산락
   │   ├─ 인기 검색어 ZSet
   │   └─ 검색 캐시
   │
   └─ MySQL
       ├─ 사용자 / 이벤트 / 좌석
       ├─ 예매 / 쿠폰
       └─ 관리자 / 문의
```

### 핵심 비즈니스 로직 — 좌석 예매 플로우

```text
[AVAILABLE] ── 좌석 선택 ──▶ [ON_HOLD] ── 결제 완료 ──▶ [CONFIRMED]
                                │
                           TTL 만료(5분)
                                │
                                ▼
                           [AVAILABLE]
```

| 상태          | 설명                | 저장소   |
| ----------- | ----------------- | ----- |
| `AVAILABLE` | 예매 가능             | MySQL |
| `ON_HOLD`   | 임시 점유 상태 (TTL 5분) | Redis |
| `CONFIRMED` | 결제 완료 후 예매 확정     | MySQL |
| `CANCELLED` | 예매 취소             | MySQL |

### 전체 예매 플로우 (Happy Path)

```text
1. 사용자 → 좌석 선택 요청
2. 서버 → Redis 분산락 획득
3. 서버 → Hold 키 저장 (TTL 5분)
4. 서버 → Hold 성공 응답 (holdToken 발급)
5. 사용자 → 쿠폰 적용(선택) + 결제 요청
6. 서버 → Mock PG 결제 요청
7. Mock PG → 결제 완료 웹훅 전송
8. 서버 → Hold 유효성 검증
9. 서버 → 쿠폰 사용 처리 + booking INSERT(CONFIRMED)
10. 서버 → Redis Hold 키 삭제
11. 서버 → 예매 확정 응답
```

### 락 획득 순서 (데드락 방지)

```text
① 좌석 Hold 락
② 쿠폰 사용 락
③ DB 트랜잭션
```

> 항상 같은 순서로 락을 획득하여 예매와 쿠폰 적용이 동시에 일어날 때도 데드락을 방지합니다.

### 캐싱 전략 — 3단계 진화 흐름

```text
[1단계] v1 API — 캐시 없음
   ↓
[2단계] v2 API — Caffeine 로컬 캐시 적용
   ↓
[3단계] v2 업그레이드 — Redis Cache-Aside 패턴 적용
```

### CI/CD 파이프라인

```text
개발자 Push
   ↓
GitHub Actions
   ├─ Build
   ├─ Test
   ├─ Docker Image Build
   ├─ ECR Push
   └─ EC2 Deploy
```

---

## 대표 문서

### 요구사항 및 기획

* [프로젝트 개요서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/1.%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EA%B0%9C%EC%9A%94%EC%84%9C.md) - 서비스 목적, 핵심 문제 정의, 시스템 설계 방향 정리
* [사용자 시나리오](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/2.%20%EC%82%AC%EC%9A%A9%EC%9E%90%20%EC%8B%9C%EB%82%98%EB%A6%AC%EC%98%A4.md) - 페르소나 기반 사용자 흐름 및 기능 필요성 정의
* [유스케이스 명세서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/3.%20%EC%9C%A0%EC%8A%A4%EC%BC%80%EC%9D%B4%EC%8A%A4%20%EB%AA%85%EC%84%B8%EC%84%9C.md) - 기능별 정상/예외 흐름 및 시스템 동작 정의
*  [기능 명세서](https://github.com/6team-Plus-project-sparta/docs/blob/main/v2/4.%20%EA%B8%B0%EB%8A%A5%20%EB%AA%85%EC%84%B8%EC%84%9C.md) - API 및 기능 단위 상세 스펙 정의

### 설계 및 아키텍처

* [시스템 아키텍처](./docs/design/architecture/README.md) — 전체 구조, 예매 플로우, 락 전략 정리
* [데이터베이스 설계](./docs/design/database/README.md) — ERD 및 핵심 테이블 구조
* [API 설계](./docs/design/api/README.md) — 도메인별 API 명세 정리
* [동시성 제어 설계서](./docs/design/concurrency/README.md) — 좌석 / 쿠폰 동시성 시나리오 및 테스트 전략

### 운영 및 배포

* [배포 가이드](./docs/processes/deployment/README.md) — AWS, Docker, GitHub Actions 배포 절차
* [성능 테스트 리포트](./docs/performance/README.md) — v1 / v2(Caffeine) / v2(Redis) 성능 비교
* [트러블슈팅](./docs/troubleshooting/README.md) — Redis 도입, 락 해제, TTL 만료 등 이슈 해결 기록

---

## 향후 업데이트 계획

### Phase 1 — 기능 안정화

* 예매 취소 정책 세분화
* 관리자 통계 페이지 추가
* FAQ 챗봇 응답 정확도 개선

### Phase 2 — 성능 고도화

* Caffeine 캐시를 Redis Cache-Aside로 고도화
* Redisson 전환 및 AOP 리팩토링
* DB 복합 인덱스 최적화 심화

### Phase 3 — 서비스 확장

* 등급별 혜택 정책 고도화
* 추천 이벤트 기능
* 모바일 환경 대응

---

## 라이선스 및 문의

Copyright (c) 2026 HOT6 Team. All Rights Reserved.

### 팀

* 정태규 — Infra
* 이지민 — Booking
* 선경안 — Event
* 강태훈 — Promotion
* 임하은 — User

### 문의

* **GitHub**: HOT6 Organization
* **Docs**: 프로젝트 문서 레포 연결 예정
* **API Docs**: Swagger 연결 예정

---

**작성자:** HOT6 Team


# 🎵 PLAY_GROUND

> **음악을 좋아하는 사람들이 모여 음악을 공유하고, 이야기하며 소통할 수 있는 커뮤니티 플랫폼**

**PLAY_GROUND**는 음악이라는 공통 관심사를 중심으로
사용자들이 자유롭게 콘텐츠를 공유하고 서로 소통할 수 있도록 제작한 **음악 커뮤니티 웹 서비스**입니다.

회원가입부터 게시글 작성, 댓글, 좋아요, 사용자 차단 등의 커뮤니티 기능을 제공하며,
관리자를 위한 게시판·카테고리 관리와 신고 처리 등의 운영 기능까지 구현했습니다.

단순한 게시판 구현을 넘어 **사용자 서비스와 관리자 시스템을 함께 설계하고 개발하는 것을 목표**로 진행한 팀 프로젝트입니다.

<br>

## 🎧 Project

### 🎼 "좋아하는 음악을 공유하고, 음악으로 소통하다."

음악을 듣는 것에서 그치지 않고,

**좋아하는 음악을 발견하고 → 공유하고 → 이야기를 나누고 → 새로운 음악을 발견하는**

선순환적인 커뮤니티 경험을 제공하는 것을 목표로 했습니다.

사용자는 다양한 게시판에서 자유롭게 음악과 관련된 콘텐츠를 공유할 수 있으며,
게시글과 댓글을 통해 다른 사용자들과 의견을 나눌 수 있습니다.

또한 관리자는 서비스 운영에 필요한 게시판 및 카테고리 관리,
신고 처리와 회원 관리 기능을 통해 안정적인 커뮤니티 운영이 가능하도록 구성했습니다.

---

## ✨ 주요 기능

### 👤 회원 & 계정 관리

* 회원가입 / 로그인
* 세션 기반 사용자 인증
* 아이디 찾기
* 비밀번호 찾기 및 재설정
* 회원정보 수정
* 회원 탈퇴
* 사용자 차단 및 차단 목록 관리

### 📝 커뮤니티

* 카테고리별 게시판
* 게시글 CRUD
* 댓글 작성 및 관리
* 게시글 좋아요
* 통합 검색
* 내가 작성한 게시글 조회
* 내가 작성한 댓글 조회
* 좋아요한 게시글 조회

### 🔎 검색

* 전체 게시판 통합 검색
* 게시글 및 콘텐츠 검색
* 검색 결과 페이징

### 🛡️ 관리자

* 카테고리 생성 / 수정 / 삭제
* 게시판 생성 / 수정 / 삭제
* 게시판 관리
* 신고 접수 및 처리
* 운영자 권한 관리
* 문제 회원 강제 탈퇴

---

## 🏗️ Architecture

```text
┌─────────────────────────────────────────────┐
│                  Client                     │
│          HTML / CSS / JavaScript            │
└──────────────────────┬──────────────────────┘
                       │
                 HTTP / AJAX
                       │
┌──────────────────────▼──────────────────────┐
│                 Controller                  │
│          Servlet / Request 처리             │
└──────────────────────┬──────────────────────┘
                       │
┌──────────────────────▼──────────────────────┐
│                  Service                    │
│             Business Logic                  │
└──────────────────────┬──────────────────────┘
                       │
┌──────────────────────▼──────────────────────┐
│                    DAO                       │
│             MyBatis Mapper                  │
└──────────────────────┬──────────────────────┘
                       │
┌──────────────────────▼──────────────────────┐
│                   MySQL                     │
│                music Database               │
└─────────────────────────────────────────────┘
```

MVC 패턴을 기반으로 **Controller → Service → DAO → MyBatis Mapper**의 계층형 구조로 설계하여 각 계층의 역할을 분리했습니다.

---

## 🛠️ Tech Stack

### Backend

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge\&logo=openjdk\&logoColor=white)
![Servlet](https://img.shields.io/badge/Jakarta%20Servlet-6DB33F?style=for-the-badge)
![JSP](https://img.shields.io/badge/JSP-323330?style=for-the-badge)
![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge)

### Frontend

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge\&logo=html5\&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge\&logo=css3\&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge\&logo=javascript\&logoColor=black)

### Database & Server

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge\&logo=mysql\&logoColor=white)
![Apache Tomcat](https://img.shields.io/badge/Apache%20Tomcat-F8DC75?style=for-the-badge\&logo=apachetomcat\&logoColor=black)

### Communication

* JSON
* AJAX
* Fetch API

---

## 📂 Project Structure

```text
src/main
├── java/kr/kh/app
│   ├── config/          # 프로젝트 및 DB 설정
│   ├── controller/      # HTTP 요청 및 응답 처리
│   ├── dao/             # MyBatis Mapper 인터페이스
│   ├── filter/          # 요청 필터
│   ├── model/           # VO / DTO
│   ├── pagination/      # 페이징 및 검색 처리
│   ├── service/         # 비즈니스 로직
│   └── utils/            # 공통 유틸리티
│
└── webapp
    ├── WEB-INF
    │   └── views/       # JSP View
    │
    ├── css/             # 스타일시트
    ├── images/          # 이미지 리소스
    └── resources/       # 정적 리소스
```

---

## 🔄 주요 사용자 흐름

```text
회원가입
   ↓
로그인
   ↓
게시판 선택
   ↓
게시글 조회 / 검색
   ↓
게시글 작성 ──────→ 댓글 작성
   │
   └──────────────→ 좋아요
                         ↓
                    마이페이지
```

관리자의 경우 별도의 관리자 페이지를 통해

```text
관리자 로그인
     ↓
관리자 페이지
     ├── 카테고리 관리
     ├── 게시판 관리
     ├── 신고 관리
     ├── 운영자 관리
     └── 회원 관리
```

와 같은 서비스 운영이 가능하도록 구현했습니다.

---

## 🗄️ Persistence Layer

MyBatis를 활용하여 데이터 접근 계층을 분리하고,
기능별 Mapper XML을 구성하여 SQL의 유지보수성을 높였습니다.

```text
UserMapper.xml
 └─ 회원 인증 / 마이페이지 / 차단 / 탈퇴

PostMapper.xml
 └─ 게시글 CRUD / 좋아요 / 통합검색

BoardMapper.xml
 └─ 게시판 조회 / 게시판 관리

CategoryMapper.xml
 └─ 카테고리 CRUD

ReportMapper.xml
 └─ 신고 접수 / 신고 처리

CommonMapper.xml
 └─ 공통 데이터 처리
```

---

## 💡 프로젝트를 통해

이번 프로젝트에서는 단순히 기능을 구현하는 것뿐만 아니라,

* MVC 기반 웹 애플리케이션 구조 이해
* Servlet/JSP 기반 웹 서비스 개발
* Service / DAO 계층 분리
* MyBatis를 활용한 데이터 접근
* 사용자 인증 및 세션 관리
* 게시판 CRUD 구현
* AJAX / Fetch API를 활용한 비동기 통신
* 검색 및 페이징 처리
* 관리자 시스템 설계
* 팀원 간 Git을 활용한 협업

등 **실제 웹 서비스 개발 과정에서 필요한 전반적인 개발 경험**을 쌓는 것을 목표로 했습니다.

---

## 👥 Team Project

**PLAY_GROUND**는 팀원들과 함께 기획부터 설계, 개발까지 진행한 프로젝트입니다.

각자의 담당 기능을 개발하면서 Git을 활용한 소스 코드 관리와
팀원 간의 코드 공유 및 협업 과정을 경험했습니다.

> **"음악을 좋아하는 사람들이 더 쉽게 만나고, 이야기하고, 공유할 수 있는 공간"**

이라는 목표를 가지고 팀원들과 함께 완성한 프로젝트입니다.

---

## 🚀 Getting Started

### 1. Clone

```bash
git clone https://github.com/seungjoo555/PLAY_GROUND.git
```

### 2. Database

MySQL에서 `music` 데이터베이스를 생성한 후
프로젝트의 MyBatis 설정 파일에서 DB 접속 정보를 설정합니다.

### 3. Run

Eclipse 또는 IntelliJ에 프로젝트를 Import한 후
Apache Tomcat을 연결하여 애플리케이션을 실행합니다.

---

## 🔗 Repository

[![GitHub](https://img.shields.io/badge/GitHub-PLAY__GROUND-181717?style=for-the-badge\&logo=github)](https://github.com/seungjoo555/PLAY_GROUND)

---

<p align="center">
  🎵 <b>PLAY_GROUND</b> 🎵
  <br>
  <sub>Music · Community · Communication</sub>
</p>

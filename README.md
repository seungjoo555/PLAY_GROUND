# 🎮 PLAY_GROUND

> **Java Servlet/JSP & MyBatis 기반의 사용자 커뮤니티 및 관리자 종합 운영 플랫폼**

---

## 📌 Project Overview

**PLAY_GROUND**는 Java Servlet과 MyBatis Persistence Framework를 활용하여 구축된 웹 커뮤니티 서비스입니다.  
MVC 패턴 및 계층형 아키텍처(Servlet Controller - Service - DAO - Mapper XML)를 준수하여 설계되었으며, 일반 사용자의 커뮤니티 활동(게시글/댓글 작성, 좋아요, 유저 차단)부터 관리자의 서비스 운영 기능(동적 카테고리/게시판 관리, 신고 처리, 불량 회원 강제 탈퇴)까지 체계적으로 구현되어 있습니다.

---

## 🛠 Tech Stack

### Backend & Database
- **Language**: Java
- **Web Framework / API**: Jakarta Servlet, JSP
- **Persistence Framework**: MyBatis 3.x
- **Database**: MySQL (`music` DB)
- **WAS / Server**: Apache Tomcat

### Frontend & Communication
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Data Exchange**: JSON, AJAX / Fetch API

---

## 📂 Project Structure (`src/main`)

```text
src/main
├── java/kr/kh/app
│   ├── controller/      # HTTP 요청 처리 및 View/JSON 응답 Servlet
│   ├── dao/             # MyBatis Mapper 인터페이스
│   │   ├── BoardDAO.java
│   │   ├── CategoryDAO.java
│   │   ├── CommonDAO.java
│   │   ├── PostDAO.java
│   │   ├── ReportDAO.java
│   │   └── UserDAO.java
│   ├── model/vo/        # 데이터베이스 엔티티 (VO / DTO)
│   ├── service/         # 비즈니스 로직 처리 Service 계층
│   └── pagination/      # 페이징 및 검색 처리 유틸리티
│
└── webapp
    ├── WEB-INF
    │   ├── classes/
    │   │   └── mybatis-config.xml  # DB 접속 정보 및 Mapper XML 등록
    │   └── views/                  # JSP 뷰 파일
    └── resources/                  # 정적 리소스 (CSS, JS, Images)

🔑 Key Features
👤 1. 회원 및 계정 관리 (Auth & User System)
회원가입 및 세션 로그인: 세션(Session) 기반 사용자 인증 상태 관리

계정 찾기 & 재설정: 아이디 찾기(/findId), 비밀번호 찾기(/findPw), 비밀번호 재설정(/newPw)

계정 관리: 회원정보 수정, 회원 탈퇴(/deleteid), 차단 사용자 목록 관리(blocklist)

📝 2. 게시판 및 커뮤니티 (Board & Content)
게시판 CRUD: 카테고리별 게시글 목록 조회, 상세 보기, 게시글 작성/수정/삭제

통합 검색: 전체 게시판 대상 키워드 검색 (/totalSearchList)

활동 관리: 내가 쓴 글, 작성한 댓글, '좋아요' 누른 게시글 모아보기

🛡️ 3. 관리자 시스템 (Admin Portal)
동적 카테고리/게시판 관리: 신규 카테고리 및 게시판 생성, 수정, 삭제

신고 처리 모니터링: 신고 접수 목록 조회 및 상세 내역 검토 (/admin/boardReportList)

운영자 및 회원 제어: 운영자 권한 관리 및 서비스 정책 위반 회원 강제 탈퇴 (/admin/forceout)

🗺️ Information Architecture (URL Structure)

/ (Main Page)
├── Auth
│   ├── /login
│   ├── /signup
│   ├── /findId
│   ├── /findPw
│   └── /newPw
│
├── Board (/board)
│   ├── /list?게시판번호
│   ├── /post/insert
│   ├── /post/detail?게시글번호
│   ├── /post/update?게시글번호
│   └── /totalSearchList
│
├── MyPage (/mypage)
│   ├── /postlist (내가 쓴 글)
│   ├── /commentlist (내가 쓴 댓글)
│   ├── /likelist (좋아요 누른 글)
│   ├── /signupdate (회원정보 수정)
│   ├── /blocklist (차단 사용자 목록)
│   └── /deleteid (회원 탈퇴)
│
└── Admin (/admin)
    ├── /categoryinsert, /categoryupdate (카테고리 관리)
    ├── /boardinsert, /boardupdate (게시판 관리)
    ├── /boardReport, /boardReportList (신고 관리)
    ├── /adminmanager (운영자 관리)
    └── /forceout (회원 강제 탈퇴)

⚙️ Persistence Layer (MyBatis Configuration)
mybatis-config.xml 설정을 통해 DB 커넥션 풀(POOLED)을 관리하며, 기능별로 분리된 6개의 Mapper XML을 사용하여 SQL을 유지보수합니다.

UserMapper.xml: 회원 인증, 마이페이지, 차단 및 탈퇴

PostMapper.xml: 게시글 CRUD, 좋아요, 통합 검색

BoardMapper.xml: 게시판 정보 및 관리자용 게시판 설정

CategoryMapper.xml: 카테고리 CRUD

ReportMapper.xml: 신고 내역 접수 및 처리

CommonMapper.xml: 공통 유틸리티 및 데이터 처리

🚀 Getting Started
Prerequisites
Java 11 이상 (또는 JDK 17)

Apache Tomcat 9.0 / 10.0

MySQL 8.0 이상

Installation
1. Repository Clone

git clone [https://github.com/seungjoo555/PLAY_GROUND.git](https://github.com/seungjoo555/PLAY_GROUND.git)

2. Database Configuration

MySQL에서 music 데이터베이스 생성

mybatis-config.xml 내 데이터베이스 접속 주소, ID/PW 설정

3. Run Application

IDE(Eclipse/IntelliJ)에 Apache Tomcat Server 연동 후 프로젝트 실행

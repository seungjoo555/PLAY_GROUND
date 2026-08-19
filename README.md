# 🎮 PLAY_GROUND

> **사용자 커뮤니티 활동부터 카테고리·신고·회원 관리까지 체계적으로 설계한 Servlet/JSP 기반의 커뮤니티 웹 서비스**

---

## 🛠 Tech Stack

### Environment & Language
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=java&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

### Backend & Frontend
![Servlet](https://img.shields.io/badge/Jakarta_Servlet-007396?style=flat-square&logo=java&logoColor=white)
![JSP](https://img.shields.io/badge/JSP-007396?style=flat-square&logo=java&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?style=flat-square&logo=json&logoColor=white)

### Server & Database
![Apache Tomcat](https://img.shields.io/badge/Apache_Tomcat-F8DC75?style=flat-square&logo=apache-tomcat&logoColor=black)
<!-- 사용하신 DB 라이브러리에 맞게 변경하세요 (예: MySQL, Oracle, MyBatis 등) -->
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

---

## 🔑 Key Features

### 👤 회원 관리 및 계정 보안 (Auth & Account)
* **인증 및 계정 관리**: 회원가입, 로그인/로그아웃, 아이디 및 비밀번호 찾기, 비밀번호 재설정(`newPw`)
* **계정 제어**: 회원정보 수정, 회원 탈퇴(`deleteid`) 및 사용자 차단 목록 관리

### 📝 게시판 및 콘텐츠 CRUD (Board & Content)
* **게시물 관리**: 카테고리별 게시글 목록 조회, 상세 페이지, 게시글 작성/수정/삭제
* **통합 검색**: 전체 게시판 대상 키워드 통합 검색 (`totalSearchList`)

### 📌 마이페이지 및 사용자 활동 (My Page)
* **활동 이력 조회**: 내가 작성한 글(`postlist`), 내가 쓴 댓글(`commentlist`), 좋아요 누른 글(`likelist`) 모아보기
* **관계 관리**: 차단 사용자 목록 조회 및 관리(`blocklist`)

### 🛡️ 관리자 시스템 (Admin Portal)
* **카테고리 & 게시판 관리**: 게시판 카테고리 및 신규 게시판 생성/수정/삭제
* **신고 모니터링**: 신고된 게시물 접수 목록 조회(`boardReportList`) 및 상세 내역 검토
* **운영 제어**: 운영자 권한 관리 및 서비스 정책 위반 회원 강제 탈퇴(`forceout`)

---

## ⚙️ Backend Architecture & Key Implementations

* **세션 기반 인증 및 권한 처리**
  * HTTP Session을 활용한 로그인 상태 유지 및 사용자 접근 권한 관리
  * 일반 사용자 영역과 관리자 포털(`/admin/*`) 간 접근 제어 로직 구현
* **데이터 모델링 및 DAO/Service 구조 설계**
  * 게시글, 댓글, 좋아요, 차단, 신고 등 복잡한 도메인 간의 관계를 고려한 DB Schema 설계
  * Servlet-Service-DAO 계층 분리를 통한 비즈니스 로직 및 데이터 처리 분리
* **동적 카테고리 및 관리 기능 구현**
  * 고정된 게시판이 아닌 관리자 페이지에서 동적으로 카테고리 및 게시판을 생성·수정할 수 있는 구조 설계
* **REST/JSON 기반 데이터 처리**
  * 비동기 요청 처리 및 프론트엔드-백엔드 간 JSON 포맷을 활용한 효율적인 데이터 통신

---

## 🗺️ Information Architecture (URL Structure)

```text
/ (Main Page)
├── /login, /signup, /findId, /findPw, /newPw (Auth)
├── /board (Board)
│   ├── /list?게시판번호
│   ├── /post/insert, /post/detail, /post/update
│   └── /totalSearchList
├── /mypage (My Page)
│   ├── /postlist, /commentlist, /likelist
│   ├── /signupdate, /blocklist, /deleteid
└── /admin (Admin)
    ├── /categoryinsert, /categoryupdate
    ├── /boardinsert, /boardupdate
    ├── /boardReport, /boardReportList
    └── /adminmanager, /forceout

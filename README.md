# Spring Boot Sample Project

Spring Boot 기반의 웹 애플리케이션 보일러플레이트 프로젝트입니다.

# 프로젝트 개요

이 프로젝트는 현대적인 웹 애플리케이션 개발에 필요한 다양한 기능들을 포함하고 있으며, 실제 프로덕션 환경에서 활용할 수 있는 베스트 프랙티스를 제시하고자 합니다.

# 시작하기

## 사전 요구사항

- Java 17 이상
- Gradle 8.x
- Docker Desktop
- Redis 7.x
- MySQL 8.x

## 설치 방법

```bash
# 프로젝트 클론
git clone https://github.com/Jinyshin/spring-boot-boilerplate.git

# 프로젝트 디렉토리로 이동
cd spring-boot-boilerplate

# 프로젝트 빌드 (의존성 다운로드 및 빌드)
./gradlew build

# 테스트 건너뛰고 빌드하기
./gradlew build -x test

# 애플리케이션 실행
./gradlew bootRun
```

### Docker를 이용한 실행

```bash
# Docker 이미지 빌드
docker build -t spring-boot-boilerplate .

# Docker 컨테이너 실행
docker-compose up -d
```

## 활용할 기술 스택

### Backend

- Spring Boot 3.3.6
  - Spring Web
  - Spring Security + JWT
  - Spring Data JPA
  - Querydsl
  - Spring Batch
  - Spring Actuator

### Database

- MySQL 8.x: 주 데이터베이스
- H2: 테스트용 인메모리 데이터베이스
- Redis: 캐싱 및 세션 관리

### Infrastructure

- Docker
- AWS S3
- GitHub Actions (CI/CD)

### Testing & Documentation

- JUnit 5
- Mockito
- Swagger (OpenAPI 3.0)

## 구현 현황

- [x] 프로젝트 기본 설정
- [ ] 사용자 인증/인가 시스템
- [ ] 게시판 기능
- [ ] 파일 관리 시스템
- [ ] 캐시 관리
- [ ] 배치 작업
- [ ] 시스템 모니터링

## 주요 기능

### 사용자 인증/인가

- JWT 기반 인증
  - Access Token / Refresh Token 관리
  - Token 만료 처리
- OAuth2.0 소셜 로그인 (Google, Kakao, Naver)
- 역할 기반 접근 제어(RBAC)
  - 사용자 역할별 권한 관리
  - API 엔드포인트별 접근 제어

### 게시판

- 게시글/댓글 CRUD
  - 페이징 처리
  - 소프트 삭제
- 파일 첨부
- 게시글 검색 및 필터링
  - 제목, 내용, 작성자 검색
  - 카테고리별 필터링
  - 날짜별 필터링

### 캐시 관리

- Redis를 활용한 세션 관리
  - 사용자 세션 정보 저장
  - 세션 만료 처리
- 게시글 조회수 캐싱
- API 응답 캐싱
  - 자주 요청되는 데이터 캐싱
  - 캐시 읽기, 쓰기 전략 적용

### 배치 작업

- 통계 데이터 집계

### 시스템 모니터링

- Spring Actuator를 통한 시스템 상태 모니터링

### 파일 관리

- S3 파일 업로드/다운로드
- 파일 포맷 검증

## 프로젝트 구조

```
src
├── main
│   ├── java
│   │   └── springboot
│   │       └── boilerplate
│   │           ├── common       # 공통 유틸리티
│   │           ├── config       # 설정 클래스
│   │           ├── controller   # API 엔드포인트 계층
│   │           ├── domain       # 도메인 모델
│   │           ├── dto          # Data Transfer Objects
│   │           │   ├── request
│   │           │   ├── response
│   │           │   └── mapper
│   │           ├── exception    # 커스텀 예외
│   │           ├── repository   # 데이터 접근 계층
│   │           ├── security     # 보안 관련 클래스
│   │           │   ├── jwt
│   │           │   ├── oauth
│   │           │   └── config
│   │           └── service      # 비즈니스 로직 계층
│   └── resources
│       ├── application.yml
│       ├── application-dev.yml
│       └── application-prod.yml
└── test                         # 테스트 코드
```

## 코드 작성 원칙

- 어떤 코드와 기능을 추가하고자 할 때, 그 이유를 확실히 이해하고 작성한다.
- 최대한 많은 레퍼런스를 참고하여 Best practice 코드를 작성한다.
- Google Java Style Guide를 기반으로 코드를 작성한다.
- 새로운 기능은 `feature/new-feature` 브랜치를 만들고 개발한다.
- PR은 대략적으로 새로운 기능 코드 100줄, 테스트 코드 400줄 단위로 한다.
- 테스트 코드 작성
  - 단위 테스트 필수
  - 통합 테스트 권장
  - 최종적으로 테스트 커버리지 80% 이상을 목표로 한다.

## 문서화

- API 문서: Swagger UI (`/swagger-ui.html`)
- 프로젝트 문서: [작업 문서](https://jinyshin.notion.site/Spring-Boot-Boilerplate-1414cff7232680af8033ddf44b2c773c?pvs=4)

## 개발 환경 설정

### 로컬 개발 환경

1. JDK 17 설치
2. IDE 설정 (IntelliJ IDEA 권장)
3. Lombok 플러그인 설치
4. Docker Desktop 설치
5. application-dev.yml 설정

### 환경변수 설정

```
MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DATABASE=sampledb
MYSQL_USERNAME=root
MYSQL_PASSWORD=password

REDIS_HOST=localhost
REDIS_PORT=6379

JWT_SECRET=your-jwt-secret-key
```

## Contribution

### 기여 방법

1. 이 저장소를 포크합니다.
2. 새로운 브랜치를 생성합니다. (`git checkout -b feature/new-feature`)
3. 변경사항을 커밋합니다. (`git commit -m 'Add some new feature'`)
4. 브랜치에 푸시합니다. (`git push origin feature/new-feature`)
5. Pull Request를 생성합니다.

### Pull Request 가이드라인

- PR을 제출하기 전에 관련 Issue를 먼저 등록해 주세요.
- PR 제목은 명확하게 작성해 주세요.
- 변경사항에 대한 상세한 설명을 포함해 주세요.
- 테스트 코드를 포함해 주세요.

## LICENSE

이 프로젝트는 MIT 라이센스를 따릅니다. 자세한 내용은 [LICENSE](./LICENSE) 파일을 참조하세요.

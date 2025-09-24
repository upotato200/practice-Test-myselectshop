# MySelectShop
![2025-09-24 14-25-29 (1)](https://github.com/user-attachments/assets/aec1abc2-cf5c-4d97-b418-23b0c6f51a62)

Spring Boot 기반의 관심 상품 관리 및 가격 비교 애플리케이션

## 개요

MySelectShop은 사용자가 관심 있는 상품을 등록하고 관리할 수 있으며, 네이버 쇼핑 API를 통해 가격 정보를 자동으로 업데이트하는 웹 애플리케이션입니다.

## 주요 기능

### 사용자 관리
- 회원가입 및 로그인
- 카카오 소셜 로그인 지원
- JWT 기반 인증 시스템
- 사용자 권한 관리 (USER/ADMIN)

### 상품 관리
- 관심 상품 등록
- 상품 정보 조회 및 수정
- 최저가격 설정 및 관리
- 페이지네이션 지원

### 폴더 기능
- 상품 분류를 위한 폴더 생성
- 폴더별 상품 관리
- 폴더에 상품 추가/조회

### 가격 모니터링
- 네이버 쇼핑 API 연동
- 자동 가격 업데이트
- 최저가격 알림 기능

### API 사용량 추적
- API 호출 시간 측정
- AOP를 통한 성능 모니터링

## 기술 스택

- **Backend**: Spring Boot 3.1.5, Spring Security, Spring Data JPA
- **Database**: MySQL
- **Authentication**: JWT, OAuth2 (Kakao)
- **External API**: Naver Shopping API
- **View**: Thymeleaf
- **Build Tool**: Gradle
- **Java Version**: 17

## 의존성

```gradle
- Spring Boot Starter Web
- Spring Boot Starter Data JPA
- Spring Boot Starter Security
- Spring Boot Starter Thymeleaf
- Spring Boot Starter Validation
- MySQL Connector
- JWT (jjwt)
- Lombok
- JSON Library
```

## 데이터베이스 설정

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/shop
spring.datasource.username=root
spring.datasource.password=root1234
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.show_sql=true
spring.jpa.properties.hibernate.format_sql=true
```

## 주요 엔티티

### User
- 사용자 정보 관리
- 카카오 ID 연동 지원
- 권한 관리 (USER/ADMIN)

### Product
- 상품 정보 저장
- 사용자별 관심 상품 관리
- 가격 정보 추적

### Folder
- 상품 분류 관리
- 사용자별 폴더 소유

### ProductFolder
- 상품과 폴더 간의 다대다 관계 관리

## API 엔드포인트

### 상품 관련
- `POST /api/products` - 상품 등록
- `GET /api/products` - 상품 목록 조회
- `PUT /api/products/{id}` - 상품 정보 수정
- `POST /api/products/{productId}/folder` - 폴더에 상품 추가

### 폴더 관련
- `GET /api/folders` - 폴더 목록 조회
- `POST /api/folders` - 폴더 생성
- `GET /folders/{folderId}/products` - 폴더별 상품 조회

### 사용자 관련
- 로그인/로그아웃
- 회원가입
- 카카오 로그인

## 실행 방법

1. MySQL 데이터베이스 설정
2. application.properties 파일 설정
3. 프로젝트 빌드 및 실행

```bash
./gradlew build
./gradlew bootRun
```

## 보안 기능

- JWT 토큰 기반 인증
- Spring Security를 통한 보안 설정
- 카카오 OAuth2 연동
- 사용자 권한별 접근 제어

## 모니터링

- AOP를 통한 API 사용 시간 추적
- 성능 모니터링 및 로깅
- 스케줄링 지원 (@EnableScheduling)

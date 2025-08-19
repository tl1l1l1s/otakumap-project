# 🗾 오타쿠맵 (OtakuMap)

## 프로젝트 소개
- 오타쿠맵은 애니메이션 성지순례를 위한 **위치 기반 여행 정보 공유 플랫폼**입니다.
- 팬들이 애니메이션 촬영지와 관련 이벤트 정보를 쉽게 찾고 리뷰를 공유할 수 있습니다.
- 팬들 간의 정보 공유와 커뮤니티 형성을 통해 더 풍부한 성지순례 경험을 만들어갑니다.


### 시연 영상

[![Video Label](https://img.youtube.com/vi/vrL2PCog6r4/0.jpg)](https://www.youtube.com/watch?v=vrL2PCog6r4)


## 주요 기능

### 인증 시스템
- JWT 토큰 기반 인증
- 소셜 로그인 (카카오, 구글, 네이버)

### 지도 및 검색
- 위치 기반 장소/이벤트 조회
- **통합 키워드 검색**
- 애니메이션별 성지 필터링

### 후기 시스템
- 장소/이벤트 상세 후기 작성
- **한줄 리뷰 및 평점**
- 유료/무료 후기 설정
- **후기 구매 시스템**

### 루트 관리
- 개인 맞춤 여행 루트 생성
- 루트 공유 및 커스터마이징
- 즐겨찾기 기능

### 포인트 & 결제
- Iamport 연동
- **포인트 충전/사용 내역**
- **후기 판매 수익 관리**

### 알림 서비스
- 이벤트 시작 알림
- 루트 저장 알림
- 후기 구매 알림

## 기술 스택

### Backend
- Java 17
- Spring Boot 3.x
- Spring Security (OAuth2)
- Spring Data JPA
- QueryDSL
- MySQL 8.0
- Redis

### Infrastructure & DevOps
- AWS S3 (이미지 저장)
- Iamport (결제 시스템)
- Docker
- GitHub Actions

### 주요 라이브러리
- JWT 토큰 인증
- Swagger

## 프로젝트 구조
```
src/main/java/com/otakumap/
├── domain/
│   ├── animation/          # 애니메이션
│   ├── auth/               # 인증/인가
│   ├── event/              # 이벤트
│   ├── event_like/         # 이벤트 좋아요
│   ├── event_location/     # 이벤트 위치
│   ├── event_review/       # 이벤트 후기
│   ├── event_short_review/ # 이벤트 한 줄 리뷰
│   ├── hash_tag/           # 해시태그
│   ├── image/              # 이미지
│   ├── map/                # 지도
│   ├── notification/       # 알림
│   ├── order/              # 주문
│   ├── payment/            # 결제
│   ├── place/              # 명소
│   ├── place_animation/    # 명소-애니메이션 연결
│   ├── place_like/         # 명소 좋아요
│   ├── place_review/       # 명소 후기
│   ├── place_short_review/ # 명소 한 줄 리뷰
│   ├── point/              # 포인트
│   ├── reviews/            # 통합 후기
│   ├── route/              # 루트
│   ├── route_item/         # 루트 아이템
│   ├── route_like/         # 루트 좋아요
│   ├── search/             # 검색
│   ├── transaction/        # 거래 내역
│   └── user/               # 회원
├── global/
│   ├── apiPayload/         # 공통 API 응답 처리
│   ├── common/             # 공통 엔티티
│   ├── config/             # 설정
│   ├── util/               # 유틸리티
│   └── validation/         # 유효성 검사
└── OtakumapApplication.java
```

## 시스템 아키텍처
```
[Client] ↔ [Spring Boot API Server]
                    ↕
                [MySQL Database]
                    ↕
                 [Redis Cache]
                    ↕
             [AWS S3] / [Iamport API]
```

## ERD
<img width="4020" height="2392" alt="OtakuMap ERD" src="https://github.com/user-attachments/assets/8267d734-862b-4eed-a159-56c2315dee63" />

## API 문서

<img width="892" height="703" alt="Screenshot 2025-08-19 at 22 24 23" src="https://github.com/user-attachments/assets/08bdba24-df43-4cd7-8828-b086298bb89b" />

[API 명세서](https://noturss.notion.site/OTAKU-MAP-API-254837611aad80c7a61ee2a55790f246?pvs=143)

## 브랜치 전략

### Git Flow 전략
- `main`: 운영 배포 브랜치
- `dev`: 개발 통합 브랜치  
- `feature/#이슈번호`: 기능 개발 브랜치
- `fix/#이슈번호`: 수정 브랜치
- `ci/#이슈번호`: 배포 관련 브랜치

### 커밋 컨벤션
```
Feat: 새로운 기능 추가
Fix: 버그 수정
!BREAKING CHANGE: 커다란 API 변경의 경우
!HOTFIX: 급하게 치명적인 버그를 고쳐야하는 경우
Style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
Refactor: 프로덕션 코드 리팩토링
Comment: 필요한 주석 추가 및 변경
Docs: 문서 수정
Test: 테스트 코드, 리펙토링 테스트 코드 추가, Production Code(실제로 사용하는 코드) 변경 없음
Chore: 빌드 업무 수정, 패키지 매니저 수정, 패키지 관리자 구성 등 업데이트, Production Code 변경 없음
Rename: 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우
Remove: 파일을 삭제하는 작업만 수행한 경우
```


# Port DOX

## Purpose

- `port/`는 외부 client, frontend UI, public API 경계에서 사용하는 Protocol Buffers 계약을 소유한다.
- ConnectRPC 서비스와 화면 지향 request/response, public/owner view model을 관리한다.

## Ownership

- 이 문서는 `port/` 전체와 하위 도메인 `AGENTS.md`가 없는 새 port 도메인 폴더를 소유한다.
- 기존 도메인 폴더는 각 도메인의 `AGENTS.md`가 소유한다.
- 루트 문서는 `buf` 설정, 생성 정책, 저장소 공통 DOX 계약을 계속 소유한다.

## Local Contracts

- `port` proto는 client/API 경계의 shape를 소유하며 필요한 경우 `core` 타입을 조합한다.
- `package` 이름은 `port.<domain>.v<version>` 형식을 유지한다.
- `port` 타입은 다른 `port` 도메인을 import할 수 있지만 순환 import를 만들지 않는다.
- studio profile, crew, plan, studio service 계약은 `studio/` 타입을 재사용한다.
- backend 내부 이벤트나 순수 shared model은 기본적으로 `core/`에 둔다.
- ConnectRPC 서비스 파일은 `*_connect.proto`, 화면/전송 모델 파일은 `*_model.proto` 이름을 사용한다.

## Work Guidance

- 새 port 도메인을 추가하면 해당 폴더에 `AGENTS.md`를 만들고 이 문서의 Child DOX Index를 갱신한다.
- public/owner/admin view를 나눌 때 루트의 필드 번호 대역 분리 원칙을 유지한다.
- request/response 메시지는 서비스 method와 가까운 `*_connect.proto`에 둔다.

## Verification

- port proto 변경 후 `buf lint`를 실행한다.
- 공개 API 호환성 영향이 있으면 `buf breaking`을 실행한다.

## Child DOX Index

- `auth/AGENTS.md`: client 인증 session, login, logout, studio switching 서비스 계약.
- `comment/AGENTS.md`: comment view model.
- `post/AGENTS.md`: post, summary, branch, content file view model.
- `search/AGENTS.md`: search query/result model.

# Core Auth DOX

## Purpose

- `core/auth/`는 계정 인증 도메인의 공유 model과 내부 AccountService 계약을 소유한다.

## Ownership

- 이 문서는 `core/auth/` 전체와 `core/auth/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.auth.v1` 형식을 유지한다.
- `auth_model.proto`는 계정 상태와 계정 식별 정보를 소유한다.
- `auth_connect.proto`는 backend 내부 계정 조회와 연결 서비스 조회 계약을 소유한다.
- 권한/role 정보가 필요하면 `core/rbac` 타입을 import해 재사용한다.

## Work Guidance

- 외부 session/login/logout request shape는 `port/auth`에 둔다.
- 계정 상태 enum 변경은 연결된 서비스별 상태 해석에 미치는 영향을 함께 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

# Port Auth DOX

## Purpose

- `port/auth/`는 client 인증, session 확인, logout, current studio 전환 API 계약을 소유한다.

## Ownership

- 이 문서는 `port/auth/` 전체와 `port/auth/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `port.auth.v1` 형식을 유지한다.
- `auth_connect.proto`는 AuthService와 관련 request/response 메시지를 소유한다.
- 계정 상태, plan, studio view는 core 및 port의 기존 타입을 조합해 사용한다.

## Work Guidance

- 인증 provider callback, session, studio switching처럼 client workflow에 직접 필요한 shape만 이 패키지에 둔다.
- backend 내부 계정 조회 계약은 `core/auth`에 둔다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

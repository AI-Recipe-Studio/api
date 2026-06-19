# Core RBAC DOX

## Purpose

- `core/rbac/`는 scope, permission, role 기반 접근 제어 model을 소유한다.

## Ownership

- 이 문서는 `core/rbac/` 전체와 `core/rbac/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.rbac.v1` 형식을 유지한다.
- role, permission, service scope의 공유 의미는 이 도메인에서 정의한다.
- 계정이나 studio 도메인은 권한 의미를 중복 정의하지 않고 이 패키지를 import한다.

## Work Guidance

- permission enum 변경은 기존 role 구성과 서비스별 scope 해석에 미치는 영향을 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

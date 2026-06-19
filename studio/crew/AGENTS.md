# Studio Crew DOX

## Purpose

- `studio/crew/`는 studio 구성원, 권한 조회, crew 이탈 API 계약을 소유한다.

## Ownership

- 이 문서는 `studio/crew/` 전체와 `studio/crew/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `studio.crew.v1` 형식을 유지한다.
- `crew_model.proto`는 CrewInfo를 관리한다.
- `crew_connect.proto`는 CrewService와 관련 request/response를 관리한다.
- 계정 정보는 `core/auth`, role 정보는 `core/rbac` 타입을 재사용한다.

## Work Guidance

- crew 권한 의미를 이 패키지에서 중복 정의하지 않는다.
- crew service request/response는 `crew_connect.proto`에 둔다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

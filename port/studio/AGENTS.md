# Port Studio DOX

## Purpose

- `port/studio/`는 외부 client용 studio view model, StudioService, CrewService 계약을 소유한다.

## Ownership

- 이 문서는 `port/studio/` 전체와 `port/studio/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `port.studio.v1` 형식을 유지한다.
- `studio_model.proto`는 public/owner studio view, studio list, subscribe info, collection model을 소유한다.
- `studio_connect.proto`는 studio 생성, 조회, 수정, 삭제 API 계약을 소유한다.
- `crew_connect.proto`는 crew 조회, 내 role 조회, studio leave API 계약을 소유한다.
- post 목록이나 collection 구성에는 `port/post` 타입을 재사용한다.

## Work Guidance

- public/owner field를 나눌 때 루트의 필드 번호 대역 분리 원칙을 유지한다.
- crew 권한 의미는 `core/rbac`, 내부 crew model은 `core/studio` 타입을 우선 재사용한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

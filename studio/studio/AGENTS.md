# Studio Service DOX

## Purpose

- `studio/studio/`는 studio 핵심 모델과 StudioService API 계약을 소유한다.

## Ownership

- 이 문서는 `studio/studio/` 전체와 `studio/studio/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `studio.studio.v1` 형식을 유지한다.
- `studio_model.proto`는 studio 내부 식별자와 기본 metadata를 관리한다.
- `studio_connect.proto`는 studio 생성, 조회, 수정, 삭제 API 계약을 관리한다.
- 표시용 public/owner profile은 `studio/service_profile` 타입을 재사용한다.

## Work Guidance

- StudioService request/response는 service method와 가까운 `studio_connect.proto`에 둔다.
- profile 표시 필드가 필요하면 이 패키지에 중복 정의하지 않고 `studio/service_profile`을 사용한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

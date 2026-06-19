# Core Storage DOX

## Purpose

- `core/storage/`는 파일 타입과 저장 파일 metadata model을 소유한다.

## Ownership

- 이 문서는 `core/storage/` 전체와 `core/storage/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.storage.v1` 형식을 유지한다.
- 파일의 저장소 식별자, 타입, 접근에 필요한 공통 metadata는 이 패키지에서 관리한다.
- post, violation 등 소비 도메인은 파일 구조를 중복 정의하지 않고 이 타입을 재사용한다.

## Work Guidance

- 새 파일 타입 추가 시 기존 소비 도메인의 처리 가능 여부를 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

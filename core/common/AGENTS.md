# Core Common DOX

## Purpose

- `core/common/`은 여러 도메인이 공유하는 일반 상태 enum과 공통 model을 소유한다.

## Ownership

- 이 문서는 `core/common/` 전체와 `core/common/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.common.v1` 형식을 유지한다.
- 공통 enum은 특정 도메인이나 화면에만 필요한 의미를 담지 않는다.
- 여러 도메인의 import 기반이 되므로 다른 도메인으로의 불필요한 import를 피한다.

## Work Guidance

- 새 공통 타입은 둘 이상의 도메인에서 안정적으로 공유될 때만 추가한다.
- 도메인 전용 상태는 해당 도메인 패키지에 둔다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

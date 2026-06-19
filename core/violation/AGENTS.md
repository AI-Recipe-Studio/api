# Core Violation DOX

## Purpose

- `core/violation/`은 콘텐츠 및 계정 위반, 조치, 대상, appeal 관련 공유 model을 소유한다.

## Ownership

- 이 문서는 `core/violation/` 전체와 `core/violation/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.violation.v1` 형식을 유지한다.
- 위반 코드, 조치 유형, 대상 유형, appeal 상태는 이 도메인에서 관리한다.
- 증빙 파일이나 관련 파일 metadata는 `core/storage` 타입을 재사용한다.

## Work Guidance

- 위반 code/action enum 변경은 정책 집행 로직과 기존 저장 데이터의 해석을 고려한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

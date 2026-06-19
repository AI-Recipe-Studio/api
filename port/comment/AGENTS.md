# Port Comment DOX

## Purpose

- `port/comment/`는 외부 client가 소비하는 comment view model을 소유한다.

## Ownership

- 이 문서는 `port/comment/` 전체와 `port/comment/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `port.comment.v1` 형식을 유지한다.
- comment 표시와 상태에 필요한 client-facing field를 관리한다.
- 공통 콘텐츠 상태는 `core/common` 타입을 재사용한다.

## Work Guidance

- comment 서비스 RPC가 추가되면 `*_connect.proto` 파일을 만들고 이 문서를 갱신한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

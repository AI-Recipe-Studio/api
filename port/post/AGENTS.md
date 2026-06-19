# Port Post DOX

## Purpose

- `port/post/`는 외부 client가 소비하는 post, content file, summary, branch model을 소유한다.

## Ownership

- 이 문서는 `port/post/` 전체와 `port/post/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `port.post.v1` 형식을 유지한다.
- public/owner post view, list, summary, branch tree 관련 shape를 관리한다.
- storage, common, violation 의미는 core 타입을 재사용한다.

## Work Guidance

- public/owner field를 나눌 때 루트의 필드 번호 대역 분리 원칙을 유지한다.
- branch 관련 메시지는 tree 구조와 interactive 정보를 분리해 유지한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

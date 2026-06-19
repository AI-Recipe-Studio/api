# Port Search DOX

## Purpose

- `port/search/`는 외부 client 검색 query와 검색 result model을 소유한다.

## Ownership

- 이 문서는 `port/search/` 전체와 `port/search/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `port.search.v1` 형식을 유지한다.
- 검색 대상, 우선순위, query, result shape는 이 패키지에서 관리한다.
- 검색 결과에 포함되는 post/studio 표시 정보는 `port/post`, `studio/service_profile` 타입을 재사용한다.

## Work Guidance

- 새 검색 대상 추가 시 `SearchType`, result payload, 우선순위 처리 필요성을 함께 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

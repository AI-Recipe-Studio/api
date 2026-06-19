# Studio Service Profile DOX

## Purpose

- `studio/service_profile/`은 외부 서비스와 client가 소비하는 studio public/owner profile 및 collection 표시 모델을 소유한다.

## Ownership

- 이 문서는 `studio/service_profile/` 전체와 `studio/service_profile/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `studio.service_profile.v1` 형식을 유지한다.
- public/owner studio view, studio list, subscribe info, collection model을 관리한다.
- post 목록이나 collection 구성에는 `port/post` 타입을 재사용한다.

## Work Guidance

- public/owner field를 나눌 때 루트의 필드 번호 대역 분리 원칙을 유지한다.
- service profile은 표시 shape를 소유하지만 port 전용 workflow request/response는 소유하지 않는다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

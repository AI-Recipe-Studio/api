# Studio Billing DOX

## Purpose

- `studio/billing/`은 studio billing 계약을 위한 future boundary이다.

## Ownership

- 이 문서는 `studio/billing/` 전체를 소유한다.
- 현재 proto 패키지는 없다.

## Local Contracts

- billing proto를 추가할 때 package 이름은 `studio.billing.v<version>` 형식을 사용한다.
- plan과 credit의 상태 모델은 `studio/plan`을 우선 재사용한다.
- 결제 gateway와 결제 상태는 `core/payment` 타입을 재사용한다.

## Work Guidance

- 실제 billing 계약이 생길 때 `v1/`과 proto 파일을 만들고 이 문서를 갱신한다.

## Verification

- proto 추가 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

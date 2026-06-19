# Core Payment DOX

## Purpose

- `core/payment/`는 결제 gateway와 결제 상태의 공유 model을 소유한다.

## Ownership

- 이 문서는 `core/payment/` 전체와 `core/payment/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.payment.v1` 형식을 유지한다.
- 결제 gateway 식별, 결제 상태, gateway 표시 정보는 이 도메인에서 관리한다.
- plan이나 credit 정책 자체는 `studio/plan`의 plan model에서 관리한다.

## Work Guidance

- gateway enum 추가 시 downstream 결제 처리와 표시 이름 필요성을 함께 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

# Studio Plan DOX

## Purpose

- `studio/plan/`은 studio plan, plan type, credit, credit history 모델을 소유한다.

## Ownership

- 이 문서는 `studio/plan/` 전체와 `studio/plan/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `studio.plan.v1` 형식을 유지한다.
- 결제 gateway와 결제 상태는 `core/payment` 타입을 재사용한다.
- billing 실행 계약은 future `studio/billing` 경계에서 관리한다.

## Work Guidance

- plan이나 credit enum 변경은 결제 모델과 소비 API(`port/auth`, `studio/studio`) 영향을 확인한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

# Core Studio DOX

## Purpose

- `core/studio/`는 studio 핵심 model, crew 관계, plan과 credit model을 소유한다.

## Ownership

- 이 문서는 `core/studio/` 전체와 `core/studio/v1/` 패키지를 소유한다.

## Local Contracts

- `package` 이름은 `core.studio.v1` 형식을 유지한다.
- `studio_model.proto`는 service 내부에서 공유되는 Studio와 CrewInfo를 소유한다.
- `plan_model.proto`는 plan, plan type, credit, credit history를 소유한다.
- 화면별 public/owner studio view는 `port/studio`에서 관리한다.

## Work Guidance

- plan이나 credit enum 변경은 결제 모델(`core/payment`)과 소비 API(`port/auth`, `port/studio`) 영향을 확인한다.
- crew role 정보는 `core/rbac` 타입을 재사용한다.

## Verification

- 변경 후 `buf lint`를 실행한다.

## Child DOX Index

- 하위 DOX 문서 없음.

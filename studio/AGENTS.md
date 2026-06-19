# Studio DOX

## Purpose

- `studio/`는 studio 중심 멀티테넌트 도메인 계약을 소유한다.
- studio 핵심 모델, crew, plan, service profile, future billing 경계를 관리한다.

## Ownership

- 이 문서는 `studio/` 전체와 하위 도메인 `AGENTS.md`가 없는 새 studio 도메인 폴더를 소유한다.
- 기존 하위 도메인 폴더는 각 도메인의 `AGENTS.md`가 소유한다.
- 루트 문서는 `buf` 설정, 생성 정책, 저장소 공통 DOX 계약을 계속 소유한다.

## Local Contracts

- `package` 이름은 `studio.<domain>.v<version>` 형식을 유지한다.
- `studio/`는 port, craft, shop 등 여러 서비스 경계에서 재사용 가능한 studio 계약을 제공한다.
- service profile처럼 client 표시 shape가 필요해도 studio 도메인 자체에 속하면 `studio/`에 둔다.
- `studio/` 타입은 필요한 `core/` 타입을 import할 수 있다.
- `studio/` 타입은 port 전용 workflow에 종속되지 않는다.

## Work Guidance

- 새 studio 하위 도메인을 추가하면 해당 폴더에 `AGENTS.md`를 만들고 이 문서의 Child DOX Index를 갱신한다.
- 메시지 필드 번호와 enum 번호는 재사용하지 않는다.
- billing은 아직 proto 계약을 만들지 않은 future boundary로 유지한다.

## Verification

- studio proto 변경 후 `buf lint`를 실행한다.
- 공개되었거나 소비자가 있는 메시지/enum/service 변경은 `buf breaking`을 실행한다.

## Child DOX Index

- `billing/AGENTS.md`: future billing 경계.
- `crew/AGENTS.md`: studio crew model과 CrewService 계약.
- `plan/AGENTS.md`: studio plan, credit, credit history 모델.
- `service_profile/AGENTS.md`: public/owner studio profile과 collection 표시 모델.
- `studio/AGENTS.md`: studio 핵심 모델과 StudioService 계약.

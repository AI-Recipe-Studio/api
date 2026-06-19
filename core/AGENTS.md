# Core DOX

## Purpose

- `core/`는 여러 서비스와 외부 경계에서 재사용되는 핵심 도메인 Protocol Buffers 계약을 소유한다.
- 공통 domain model, 내부 RPC 서비스 계약, 권한/인증/스튜디오/결제/스토리지/위반 도메인의 공유 타입을 제공한다.

## Ownership

- 이 문서는 `core/` 전체와 하위 도메인 `AGENTS.md`가 없는 새 core 도메인 폴더를 소유한다.
- 기존 도메인 폴더는 각 도메인의 `AGENTS.md`가 소유한다.
- 루트 문서는 `buf` 설정, 생성 정책, 저장소 공통 DOX 계약을 계속 소유한다.

## Local Contracts

- `core` proto는 UI 화면 요구사항보다 서비스 간 공유 의미와 도메인 정합성을 우선한다.
- `package` 이름은 `core.<domain>.v<version>` 형식을 유지한다.
- 외부 client 전용 request/response shape가 필요하면 기본적으로 `port/`에 둔다.
- core 타입은 port 타입을 import하지 않는다.
- core domain 간 import는 순환을 만들지 않는다.
- 공통 상태 enum이나 cross-domain type은 특정 화면 편의를 위해 확장하지 않는다.

## Work Guidance

- 새 core 도메인을 추가하면 해당 폴더에 `AGENTS.md`를 만들고 이 문서의 Child DOX Index를 갱신한다.
- 새 버전 폴더를 만들 때 기존 버전과 호환성, package 이름, import 경로를 함께 확인한다.
- 필드 번호를 재사용하지 않고, 의미가 제거된 필드는 reserved 처리를 우선 검토한다.

## Verification

- core proto 변경 후 `buf lint`를 실행한다.
- 공개되었거나 소비자가 있는 메시지/enum/service 변경은 `buf breaking`을 실행한다.

## Child DOX Index

- `auth/AGENTS.md`: 계정 인증 모델과 내부 AccountService 계약.
- `common/AGENTS.md`: 여러 도메인이 공유하는 공통 상태 enum.
- `payment/AGENTS.md`: 결제 게이트웨이와 결제 상태 모델.
- `rbac/AGENTS.md`: role, permission, scope 모델.
- `storage/AGENTS.md`: 파일 타입과 저장 파일 모델.
- `studio/AGENTS.md`: studio 핵심 모델, crew 모델, plan/credit 모델.
- `violation/AGENTS.md`: 위반 코드, 조치, 대상, appeal 모델.

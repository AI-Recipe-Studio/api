# DOX framework

- DOX는 이 저장소의 `AGENTS.md` 계층이며, 모든 작업자는 적용 범위의 문서를 작업 계약으로 따라야 한다.
- 작업 산출물, 원천 자료, 지침, 기록, 자산, 지속 문서는 가장 가까운 `AGENTS.md`와 그 상위 문서만으로 이해 가능해야 한다.

## Core Contract

- `AGENTS.md`는 해당 하위 트리에 대한 구속력 있는 작업 계약이다.
- 더 가까운 하위 문서가 로컬 세부 규칙을 정하지만, 하위 문서는 이 루트 DOX 계약을 약화할 수 없다.
- 이 저장소는 Protocol Buffers API 명세 저장소이며, `buf` 기반 lint, breaking check, code generation 설정을 루트가 소유한다.

## Read Before Editing

1. 루트 `AGENTS.md`를 읽는다.
2. 수정할 파일 또는 폴더를 식별한다.
3. 저장소 루트에서 대상 경로까지 내려가며 모든 `AGENTS.md`를 읽는다.
4. 부모 `AGENTS.md`의 Child DOX Index에 대상 경로를 포함하는 하위 문서가 있으면 그 문서를 읽고 계속 내려간다.
5. 가장 가까운 `AGENTS.md`를 로컬 계약으로 사용하고, 상위 문서는 저장소 공통 규칙으로 사용한다.
6. 기억에 의존하지 말고 현재 세션에서 적용 DOX 체인을 다시 읽은 뒤 편집한다.

## Update After Editing

- 의미 있는 변경 후에는 완료 전 DOX pass를 수행한다.
- 목적, 범위, 소유권, 책임, 지속 구조, 계약, workflow, 입출력, 권한, 제약, 부작용, 산출물, 사용자 선호가 바뀌면 가장 가까운 소유 `AGENTS.md`를 갱신한다.
- `AGENTS.md` 생성, 삭제, 이동, 이름 변경, Child DOX Index 변경은 해당 부모 문서도 갱신한다.
- 부모 수준 구조, 소유권, workflow, child index가 바뀌면 부모 문서를 갱신하고, 부모 변경이 로컬 규칙에 영향을 주면 자식 문서도 갱신한다.
- 오래되었거나 모순되는 내용은 즉시 제거한다.
- 작은 구현 수정이 계약을 바꾸지 않는 경우 문서를 그대로 둘 수 있지만, DOX pass는 수행하고 closeout에 이유를 보고한다.

## Hierarchy

- 루트 `AGENTS.md`는 저장소 전체 규칙, 사용자 선호, 루트 설정 파일, top-level Child DOX Index를 소유한다.
- `core/AGENTS.md`는 재사용 가능한 핵심 도메인 모델과 내부 서비스 계약을 소유한다.
- `port/AGENTS.md`는 외부 클라이언트/프론트엔드 경계의 ConnectRPC 및 화면 지향 모델을 소유한다.
- 도메인별 `AGENTS.md`는 해당 도메인의 `v1` 패키지와 이후 버전 폴더를 소유한다.

## Child Doc Shape

- 폴더가 고유한 목적, 규칙, 책임, workflow, 자료, 품질 기준을 가진 지속 경계가 되면 child `AGENTS.md`를 만든다.
- 기본 섹션 순서는 다음을 따른다.
    - Purpose
    - Ownership
    - Local Contracts
    - Work Guidance
    - Verification
    - Child DOX Index
- 구체적인 기준이 아직 없으면 `Work Guidance` 또는 `Verification`을 비워둘 수 있다.

## Style

- 모든 `AGENTS.md` 문서의 기본 언어는 한국어다.
- 사용자에게 명시 요청을 받지 않는 한 `AGENTS.md` 내용을 영어로 작성하지 않는다.
- 코드, 파일명, 경로, API 이름, 환경 변수, CLI 명령 같은 기술 식별자는 원문을 유지한다.
- 문서는 간결하고 현재 상태에 맞게 운영 가능해야 한다.
- 안정적인 계약을 기록하고 작업 일지는 남기지 않는다.
- 넓은 규칙은 부모 문서에, 구체적 세부 사항은 자식 문서에 둔다.
- 명확한 이름을 가진 직접적인 bullet을 선호한다.
- 반복 규칙, 오래된 경고, 명백한 설명, 잘못 배치된 세부 내용은 제거한다.

## Repository Contracts

- `buf.yaml`, `buf.gen.yaml`, `buf.lock`, `go.mod`, `go.sum`, `README.md`, `LICENSE`는 루트가 소유한다.
- `buf.yaml`은 `STANDARD` lint와 `FILE` breaking 정책을 사용한다.
- `buf.gen.yaml`은 `gen/` 출력, `paths=source_relative`, `go_package_prefix=github.com/ai-recipe-studio/api/gen` 계약을 유지한다.
- 생성 산출물인 `gen/`은 현재 저장소에 없으며, 생성 설정 변경 없이 임의로 추가하지 않는다.
- Protocol Buffers 패키지는 디렉터리 경로와 일치하는 `package` 이름을 유지한다.
- 기존 설계 원칙상 내부 DB 식별자는 `UUIDv7` 사용을 전제로 하며, 공통 필드 `1 ~ 50`, 소유자/관리자 전용 필드 `51 ~` 대역 분리를 깨지 않는다.

## Verification

- proto 변경 후 관련 범위에서 `buf lint`를 실행한다.
- 호환성 영향이 있는 proto 변경은 `buf breaking`을 기존 기준과 비교해 실행한다.
- 생성 설정 또는 import/module 변경 후에는 필요 시 `buf generate`로 코드 생성 경로를 확인한다.

## Closeout

1. 변경 경로의 DOX 체인을 다시 확인한다.
2. 가장 가까운 소유 문서와 영향받은 부모/자식 문서를 갱신한다.
3. 영향받은 Child DOX Index를 새로 고친다.
4. 오래되었거나 모순되는 문구를 제거한다.
5. 관련 기존 검증을 실행한다.
6. 의도적으로 바꾸지 않은 문서가 있으면 이유를 보고한다.

## User Preferences

- Python등 스크립트는 꼭 필요한 경우가 아니라면 사용하지 않는다. 어떤 작업에서도 Python등 스크립트를 생성, 실행, 의존하지 않도록 해야 하며 불가피하게 사용해야한다면 prompt로 물어본 후 허가가
  나면 사용한다.

## Child DOX Index

- `core/AGENTS.md`: 재사용 가능한 핵심 도메인 모델, 내부 서비스 계약, 공통 enum/message의 DOX 루트.
- `port/AGENTS.md`: 외부 클라이언트/프론트엔드용 ConnectRPC 서비스와 화면 지향 모델의 DOX 루트.

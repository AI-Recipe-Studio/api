# issue #19: Studio top-level 도메인 분리 계획

## Summary

- core/studio와 port/studio를 제거하고, top-level studio/ 도메인으로 승격한다.
- 새 패키지는 studio.studio.v1, studio.crew.v1, studio.plan.v1, studio.service_profile.v1로 분리한다.
- studio/billing은 future boundary로 AGENTS.md만 생성하고, 빈 proto는 만들지 않는다.
- Python은 사용하지 않는다.

## Key Changes

- core/studio/v1/studio_model.proto의 Studio는 studio/studio/v1/studio_model.proto로 이동하고 package를 studio.studio.v1로 변경한다.
- core/studio/v1/plan_model.proto는 studio/plan/v1/plan_model.proto로 이동하고 package를 studio.plan.v1로 변경한다.
- 기존 core.studio.v1.CrewInfo는 studio/crew/v1/crew_model.proto로 분리하고 package를 studio.crew.v1로 변경한다.
- port/studio/v1/crew_connect.proto는 studio/crew/v1/crew_connect.proto로 이동하고 CrewInfo 참조를 studio.crew.v1.CrewInfo로 바꾼다.
- port/studio/v1/studio_connect.proto는 studio/studio/v1/studio_connect.proto로 이동하고 package를 studio.studio.v1로 변경한다.
- 기존 port/studio/v1/studio_model.proto의 화면/프로필 타입은 studio/service_profile/v1/service_profile_model.proto로 분리한다:
    - StudioStatusType, StudioTapType, StudioExternalLink
    - PublicStudio, OwnerStudio, Studio, StudioList
    - SubscribeInfo, Collection, CollectionList

- StudioService 응답/요청에서 profile view 타입은 studio.service_profile.v1을 import해 사용한다.
- port/auth/v1/auth_connect.proto는 core/studio와 port/studio import를 제거하고 studio/plan 및 studio/service_profile을 참조한다.
- port/search/v1/search_model.proto는 port/studio import를 제거하고 studio/service_profile을 참조한다.
- core/studio/와 port/studio/ 하위 proto 및 DOX는 제거하고, core/AGENTS.md, port/AGENTS.md, 루트 AGENTS.md의 Child DOX Index를 갱신한다.
- 새 DOX 문서는 studio/AGENTS.md, studio/studio/AGENTS.md, studio/crew/AGENTS.md, studio/plan/AGENTS.md,
  studio/service_profile/AGENTS.md, studio/billing/AGENTS.md를 만든다.
- README.md의 directory layout과 Studio 설명은 새 studio/* 구조에 맞게 갱신한다.

## Public API / Interface Changes

- 제거되는 proto import 경로:
    - core/studio/v1/studio_model.proto
    - core/studio/v1/plan_model.proto
    - port/studio/v1/studio_model.proto
    - port/studio/v1/studio_connect.proto
    - port/studio/v1/crew_connect.proto

- 새 proto import 경로:
    - studio/studio/v1/studio_model.proto
    - studio/studio/v1/studio_connect.proto
    - studio/crew/v1/crew_model.proto
    - studio/crew/v1/crew_connect.proto
    - studio/plan/v1/plan_model.proto
    - studio/service_profile/v1/service_profile_model.proto

- 메시지 필드 번호와 enum 번호는 유지한다. 이름 변경은 package/import 경로 변경에 필요한 범위로 제한한다.

## Test Plan

- rg "core/studio|port/studio|core\\.studio|port\\.studio"로 이전 경로와 package 참조가 남지 않았는지 확인한다.
- buf lint를 실행한다.
- 호환성 변경이므로 buf breaking을 실행한다. 기준 remote가 없으면 실패 사유를 기록한다.
- issue 체크리스트에 맞춰 buf generate를 실행해 codegen 성공 여부를 확인한다. 생성된 gen/은 현재 저장소에 추적되지 않는 산출물이므로, 커밋 대상에는 포함하지 않는다.
- git status --short로 의도한 proto, DOX, README 변경만 남았는지 확인한다.

## Assumptions

- 사용자가 선택한 대로 service_profile은 실제 proto 패키지로 분리한다.
- 사용자가 선택한 대로 billing은 이번 issue에서 future DOX boundary만 만들고 proto package는 만들지 않는다.
- 기존 메시지/enum 의미와 필드 번호는 유지하며, 이번 작업은 도메인 경계와 import/package 재배치에 집중한다.
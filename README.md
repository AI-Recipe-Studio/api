# AI Recipe Studio - API Definitions

AI Recipe Studio 플렛폼을 구성하는 마이크로서비스 간 통신 인터페이스 명세(Protocol Buffers) 저장소입니다.
이 저장소는 **Buf CLI**를 활용하여 **외부 통신용 ConnectRPC** 와 **내부 이벤트 스트림 처리용** 스키마를 단일 아키텍처 가이드라인에 따라 관리합니다.

---

## 개요

우리 플랫폼은 시스템의 결합도를 낮추고 성능을 극대화하기 위해 통신 목적에 따라 인터페이스 객체를 철저히 분리하여 사용합니다.

1. **Common Model**: 순수 핵심 데이터 도메인 모델로 하위 통신을 위한 기본 베이스로 사용된다.
2. **ConnectRPC (외부 통신):** 프론트엔드 UI 및 클라이언트와의 동기식(`Req/Resp`) 통신에 사용된다. 화면 종속적이고 정제된 데이터를 처리한다.
3. **Pub/Sub Event (내부 전파):** 상태 변경 정보를 다른 마이크로서비스(인코더, 검색 엔진 등)에 비동기 전파할 때 사용하며, 메시지는 `*Event` 접미사를 강제한다.
4. **Request-Reply (내부 RPC):** 백엔드 서비스 간에 동기식 조회가 필요할 때 사용하며, 위 객체들과의 오염을 막기 위해 `*EventRequest / *EventReply`
   접미사를 강제한다.

---

## 디렉터리 구조 및 파일 명 (Directory Layout And File Names)

도메인별 버전 관리(`v1`, `v2`) 체계를 따르며, 하나의 도메인 패키지 안에서 목적별로 proto 파일을 나누어 관리한다.

```text
...
studio/                 # 스튜디오(채널) 플랫폼
├── studio/             # 스튜디오(채널) 관리 도메인
│   └── v1/
│       ├── studio_model.proto   # 순수 핵심 데이터 도메인 모델 (Enum, 구조체)
│       ├── studio_connect.proto  # 외부 Client 통신용 ConnectRPC 서비스 및 객체
│       └── studio_event.proto    # 내부 NATS 통신용 (PubSub Event & Request-Reply)
├── plan/               # 플랜 도메인
└── crew/               # 크루원 도메인
...
```

---

## 🛠️ 핵심 스키마 설계 원칙 (Design Guidelines)

### 1. ID 설계 규칙 (Video & Entity IDs)

* **DB 저장 시:** 성능 최적화 및 정렬을 위해 내부적으로 **`UUIDv7`**을 PK로 사용합니다.

### 2. 필드 번호 대역 분리 (Forward Compatibility)

소유자/관리자 전용 스키마(`OwnerStudioInfo`)는 공통 스키마(`PublicStudioInfo`)의 필드 번호 정합성을 깨뜨리지 않기 위해 번호 대역을 격리합니다.

* **`1 ~ 50` 번:** 전 유저 공통 필드 영역
* **`51 ~ ` 번:** 소유자 및 관리자 전용 필드 영역 (예: 비즈니스 이메일, 정산 데이터 등)

---

## 🚀 빌드 및 코드 생성 (Code Generation)

본 프로젝트는 프로토콜 버퍼 빌드 툴로 `buf`를 사용합니다. `managed: true` 설정이 활성화되어 있어 Go 패키지 접두사가 자동으로 주입됩니다.

### 사전 요구사항

* [Buf CLI](https://buf.build/docs/installation) 설치 필요

### lint 명령어

```bash
buf lint
```

### 생성 명령어

프로젝트 루트 디렉터리에서 아래 명령어를 실행하면 `gen/` 폴더 하위에 **Go(ConnectRPC)** 파일과 **TypeScript(ES)** 파일이 소스 상대 경로(`source_relative`)에 맞춰
자동 생성됩니다.

```bash
buf generate
```
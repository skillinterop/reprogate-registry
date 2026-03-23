# reprogate-registry

ReproGate 워크플로우, 규칙, 프리셋 패키지를 관리하는 상호운용 생태계 레지스트리입니다.

## 개요

이 저장소는 ReproGate 패키지(워크플로우, 규칙, 프리셋)를 저장하는 **리프 레지스트리**입니다. ReproGate 런타임이 아니며, ReproGate 시스템에서 사용할 수 있는 정의를 저장합니다. `skill-registry` 및 `cao-profile-registry`와 동일한 레벨의 피어 레지스트리입니다. 래퍼 도구는 이 레지스트리의 `manifest.json`을 참조하여 게이트를 검색하고 설치합니다.

## 디렉터리 구조

```
reprogate-registry/
├── manifest.json              # 모든 게이트 항목이 포함된 레지스트리 매니페스트
├── schemas/
│   └── manifest.schema.json   # 매니페스트 검증용 JSON 스키마
├── gates/
│   └── <gate-name>/
│       ├── GATE.md            # 게이트 문서
│       └── metadata.json      # 게이트 메타데이터
├── README.md
└── .gitignore
```

## 사용 가능한 게이트

| 정규 ID | 이름 | 버전 | 설명 |
|---------|------|------|------|
| `reprogate/org/code-review-gate@0.1.0` | code-review-gate | 0.1.0 | 재현 가능한 리뷰 워크플로우를 위한 코드 리뷰 품질 게이트 |

## 매니페스트 형식

`manifest.json` 파일은 LeafManifest 구조를 따릅니다:

```json
{
  "registryType": "reprogate",
  "namespace": "org",
  "version": "0.1.0",
  "channel": "experimental",
  "generatedAt": "2026-03-20T07:00:00Z",
  "items": [...]
}
```

## 새 게이트 추가 방법

1. `gates/<gate-name>/` 디렉터리를 생성합니다
2. 게이트 문서인 `GATE.md`를 추가합니다
3. 게이트 메타데이터인 `metadata.json`을 추가합니다
4. `manifest.json`에 새 게이트 항목을 추가합니다
5. 변경 사항으로 PR을 생성합니다

## 정규 ID 형식

모든 게이트는 다음 정규 ID 형식을 사용합니다:

```
reprogate/<namespace>/<name>@<version>
```

예시: `reprogate/org/code-review-gate@0.1.0`

## 관련 저장소

- [`registry-hub`](https://github.com/skillinterop/registry-hub) — 리프 레지스트리를 통합하는 최상위 허브
- [`skill-registry`](https://github.com/skillinterop/skill-registry) — 스킬 리프 레지스트리
- [`cao-profile-registry`](https://github.com/skillinterop/cao-profile-registry) — CAO 프로필 리프 레지스트리

## 라이선스

MIT

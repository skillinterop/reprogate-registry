# reprogate-registry

ReproGate 워크플로우, 규칙, 프리셋 패키지를 관리하는 상호운용 생태계 레지스트리입니다.

## 개요

이 저장소는 ReproGate 패키지(워크플로우, 규칙, 프리셋)를 저장하는 **리프 레지스트리**입니다. ReproGate 런타임이 아니며, ReproGate 시스템에서 사용할 수 있는 정의를 저장합니다. `skill-registry` 및 `cao-profile-registry`와 동일한 레벨의 피어 레지스트리입니다. 소비자 도구는 이 레지스트리의 `index.jsonld`를 읽어 게이트를 찾고 실제 `GATE.md`를 해석합니다.

## 디렉터리 구조

```
reprogate-registry/
├── index.jsonld               # 모든 게이트 항목이 포함된 공개 카탈로그
├── schemas/
│   ├── index.schema.json      # index.jsonld 검증용 JSON Schema
│   └── manifest.schema.json   # 레거시 manifest 계약 (Phase 3 전까지 유지)
├── gates/
│   └── <gate-name>/
│       └── GATE.md            # 게이트 문서
├── README.md
└── .gitignore
```

## 사용 가능한 게이트

| 정규 ID | 이름 | 버전 | 설명 |
|---------|------|------|------|
| `reprogate/org/code-review-gate@0.1.0` | code-review-gate | 0.1.0 | 재현 가능한 리뷰 워크플로우를 위한 코드 리뷰 품질 게이트 |

## 카탈로그 형식

`index.jsonld` 파일은 JSON-LD `DataCatalog` 구조를 따릅니다:

```json
{
  "@type": "DataCatalog",
  "name": "ReproGate Registry",
  "dataset": [
    {
      "@type": "SoftwareApplication",
      "identifier": "reprogate/org/code-review-gate@0.1.0",
      "url": "./gates/code-review-gate/GATE.md",
      "skillinterop:status": "active",
      "skillinterop:channel": "experimental"
    }
  ]
}
```

## 새 게이트 추가 방법

1. `gates/<gate-name>/` 디렉터리를 생성합니다
2. 게이트 문서인 `GATE.md`를 추가합니다
3. `index.jsonld`의 `dataset` 배열에 새 항목을 추가합니다
4. `schemas/index.schema.json` 기준으로 `index.jsonld`를 검증합니다
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

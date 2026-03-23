# code-review-gate

재현 가능한 리뷰 워크플로우를 위한 코드 리뷰 품질 게이트입니다.

## 개요

이 게이트는 풀 리퀘스트가 병합되기 전에 특정 검사를 통과하도록 요구하여 코드 리뷰 표준을 강제합니다. 코드 품질의 일관성을 보장하는 재현 가능한 리뷰 워크플로우를 제공합니다.

## 게이트 설정

| 설정 | 값 |
|------|-----|
| 게이트 타입 | review |
| 트리거 이벤트 | pull_request |
| 필수 검사 항목 | lint, test, type-check |

## 사용법

```yaml
gate: reprogate/org/code-review-gate
triggers:
  - pull_request
```

## 필수 검사 항목

1. **lint** - 코드 스타일 및 포맷 검증
2. **test** - 단위 테스트 및 통합 테스트 실행
3. **type-check** - TypeScript/타입 검증

## 호환성

- Wrapper CLI: >=0.1.0
- ReproGate Runtime: >=0.1.0

## 라이선스

MIT

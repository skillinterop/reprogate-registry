# code-review-gate

Code review quality gate for reproducible review workflows.

## Overview

This gate enforces code review standards by requiring specific checks to pass before a pull request can be merged. It provides a reproducible review workflow that ensures code quality consistency.

## Gate Configuration

| Setting | Value |
|---------|-------|
| Gate Type | review |
| Trigger Events | pull_request |
| Required Checks | lint, test, type-check |

## Usage

```yaml
gate: reprogate/org/code-review-gate
triggers:
  - pull_request
```

## Required Checks

1. **lint** - Code style and formatting validation
2. **test** - Unit and integration test execution
3. **type-check** - TypeScript/type validation

## Compatibility

- Wrapper CLI: >=0.1.0
- ReproGate Runtime: >=0.1.0

## License

MIT

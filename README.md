# reprogate-registry

ReproGate workflow, rule, and preset packages for the interop ecosystem.

## Overview

This repository is a **leaf registry** that stores ReproGate packages (workflows, rules, presets). It is NOT the ReproGate runtime — this repo stores definitions that can be consumed by the ReproGate system. It is a peer of `skill-registry` and `cao-profile-registry`. Wrapper tools consume this registry's `manifest.json` to discover and install gates.

## Directory Structure

```
reprogate-registry/
├── manifest.json              # Registry manifest with all gate entries
├── schemas/
│   └── manifest.schema.json   # JSON Schema for manifest validation
├── gates/
│   └── <gate-name>/
│       ├── GATE.md            # Gate documentation
│       └── metadata.json      # Gate metadata
├── README.md
└── .gitignore
```

## Available Gates

| Canonical ID | Name | Version | Description |
|--------------|------|---------|-------------|
| `reprogate/org/[MASKED_EMAIL]` | code-review-gate | 0.1.0 | Code review quality gate for reproducible review workflows |

## Manifest Format

The `manifest.json` file follows the LeafManifest structure:

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

## How to Add a New Gate

1. Create a directory under `gates/<gate-name>/`
2. Add `GATE.md` with gate documentation
3. Add `metadata.json` with gate metadata
4. Update `manifest.json` to include the new gate entry
5. Open a PR with the changes

## Canonical ID Format

All gates use the canonical ID format:

```
reprogate/<namespace>/<name>@<version>
```

Example: `reprogate/org/[MASKED_EMAIL]`

## Related Repos

- [`registry-hub`](https://github.com/skillinterop/registry-hub) — Top-level hub that aggregates leaf registries
- [`skill-registry`](https://github.com/skillinterop/skill-registry) — Skill leaf registry
- [`cao-profile-registry`](https://github.com/skillinterop/cao-profile-registry) — CAO profile leaf registry

## License

MIT

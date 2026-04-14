# VERSIONING

Schema families use explicit version suffixes, for example:

- `wal_event.v1`
- `policy_epoch.v1`
- `revocations.v1`

Rules:
- breaking changes require a new major schema version
- canonicalization changes are always breaking
- example bundles must declare the exact schema versions they use
- a verifier must never silently reinterpret an older schema as a newer one

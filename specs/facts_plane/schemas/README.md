# Schemas

Three schema families. Each artifact belongs to exactly one family.

## facts-plane/

Core artifacts that appear in execution proof bundles. These are the
objects a third-party verifier reads to confirm what happened.

Every execution that passes through the membrane produces a bundle
containing a subset of these artifacts. The offline verifier
(fp-verify) validates bundles against these schemas.

## governance/

Policy and epoch artifacts. These define the rules that governed
execution at a specific point in time.

A policy epoch is a cryptographically pinned snapshot of the rules
in force. Every execution token binds to a specific epoch digest.
If the rules changed between approval and execution, the token is
invalid.

## control-kernel/

Proof artifacts for runtime control surfaces. These are the
higher-assurance artifacts produced by the Phoenix Membrane for
audit and compliance purposes.

## Schema $id convention

All schemas use canonical public URLs as their `$id`:

```
https://facts-plane.github.io/facts-plane-spec/schemas/<family>/<name>
```

## Versioning

Schema filenames include the version:
- `receipt.schema.json` — unversioned (legacy)
- `invocation-token.v1.schema.json` — versioned
- `invocation-token.v2.schema.json` — breaking change

See VERSIONING.md for the full versioning policy.

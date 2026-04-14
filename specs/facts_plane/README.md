# facts-plane-spec

The public artifact language for governed AI execution proof.

This repository defines the open, versioned structures that third parties
can use to understand, validate, and verify claims made by a governed
execution system.

## What this is

When an AI agent executes a privileged action, facts-plane defines what
the proof looks like. This repository contains the schemas, canonicalization
rules, test vectors, and example bundles that make that proof independently
verifiable.

## What this is not

- It is not the runtime that enforces governance
- It is not a framework for building AI agents
- It is not a compliance checklist

The runtime that produces these artifacts — the dot.ink Phoenix Membrane —
is commercial and stays closed. You can verify any bundle it produces
without access to the private runtime. That is the point.

## Scope

**Public and canonical:**
- JSON schemas for all proof artifact types
- Canonicalization rules and digest vectors
- Event taxonomy
- Valid and invalid fixture examples
- End-to-end execution bundle examples

**Not in this repository:**
- Private authority kernel
- Execution control plane
- Token mint logic
- Internal runtime enforcement details

## Verify bundles with fp-verify

```bash
pip install fp-verify
fp-verify verify bundle.json
```

[fp-verify](https://github.com/facts-plane/fp-verify) is the offline
verifier for bundles written in this artifact language.

## Schema families

### `schemas/facts-plane/`
Core artifact schemas used in execution proof bundles:

| Schema | What it represents |
|--------|-------------------|
| `event-envelope` | Wrapper for all WAL events |
| `wal-record` | Write-ahead log entry with chain linkage |
| `receipt` | Sealed commitment over a completed execution |
| `checkpoint-receipt` | Replay anchor |
| `state-transition-payload` | Typed state machine transition |
| `tool-call-prepared-payload` | Write-before-act precondition record |
| `tool-call-started-payload` | Execution start record |
| `tool-call-completed-payload` | Execution outcome record |
| `evidence-ref` | Reference to a piece of supporting evidence |
| `evidence-bundle-manifest` | Digest-addressed evidence package |
| `approval-record` | Human review artifact with exact scope binding |
| `invocation-token` | One-time execution capability token |
| `reconcile-result` | Ambiguity resolution record |
| `verification-report` | Offline verifier output |
| `break-glass-payload` | Emergency override record |
| `neutral-review-surface` | Deterministic review presentation binding |

### `schemas/governance/`
Policy and epoch artifact schemas:

| Schema | What it represents |
|--------|-------------------|
| `policy-pack` | Compiled governance configuration |
| `policy_epoch` | Active policy epoch with digest binding |
| `revocations` | Revoked signers, keys, and capabilities |
| `config_change_event` | Signed configuration change record |

### `schemas/control-kernel/`
Proof artifact schemas for runtime control surfaces:

| Schema | What it represents |
|--------|-------------------|
| `control-envelope` | Action authorization envelope |
| `invocation-token` | Capability token with scope binding |
| `wal-entry` | WAL entry with self-digest chain |
| `intent-receipt` | Sealed action intent record |
| `break-glass-receipt` | Emergency override proof artifact |
| `evidence-bundle-manifest` | Evidence quorum manifest |
| `audit-record-aplus` | High-assurance audit record |
| `decision-receipt-aplus` | High-assurance decision receipt |

## Canonicalization

All proof artifacts use a strict canonicalization profile:

- UTF-8 encoding
- Unicode NFC normalization
- Sorted object keys
- No whitespace between tokens
- No floats — use integers or canonical decimal strings
- Timestamps as ISO-8601 UTC strings

See `canonical/` for the full specification and test vectors.

## Relationship to fp-verify

`facts-plane-spec` defines the language.
`fp-verify` verifies bundles written in that language.

A third party who has never seen the dot.ink runtime can:
1. Read the schemas in this repo to understand what a valid proof bundle looks like
2. Run `fp-verify` against any bundle to verify it conforms
3. Independently confirm that the bundle structure proves what is claimed

## Repository contract

Every schema in this package has:
- A stable version in the filename
- A `$id` pointing to the canonical public URL
- At least one valid fixture in `fixtures/valid/`
- At least one invalid fixture in `fixtures/invalid/`

## License

Apache 2.0

## Part of

[dot.ink](https://dot.ink) — deterministic execution membrane for
probabilistic intelligence.

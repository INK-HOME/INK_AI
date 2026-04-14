
> Public bundle note: this verifier package is included as part of the curated .INK public surface. It is intended to validate public bundles and example artifacts without exposing the internal runtime codebase.

# fp-verify

Offline verifier for Facts Plane execution bundles.

## What it does

When an AI agent executes a privileged action — a wire transfer, a payment release, a record mutation — you need to be able to verify what happened without trusting the runtime that ran it.

`fp-verify` takes a portable execution bundle and checks it against a set of deterministic control rules. No network required. No runtime trust required.

## What it verifies

| Check | What it detects |
|---|---|
| **Structure** | Required fields and object types |
| **ControlEnvelope** | Envelope fields, risk tier, digest formats |
| **InvocationToken** | Token payload, one-time-use flag, MAC presence |
| **EvidenceRef** | Source class, digest formats, timestamp formats |
| **ApprovalRecord** | Scope binding fields, decision enum |
| **TokenRecord** | Status enum, required fields |
| **Receipt** | Root digest format, seal timestamp |
| **State machine** | Legal state transition graph |
| **Scope binding** | args_digest consistency across envelope, token, and approval — detects action substitution |
| **Evidence consistency** | Dangling evidence reference detection |
| **Evidence policy** | Source class and corroboration requirements by risk tier |
| **Token lifecycle** | One-time token replay detection |
| **Review lineage** | Challenge completion and anomalous approval latency |
| **Break-glass** | Incident binding requirement when break_glass=true |
| **Reconcile lineage** | IN_DOUBT → RECONCILE_PENDING state ordering |

## What it does not do

- It does not verify that digests match the actual payload bytes — that requires the runtime to produce correct digests at execution time
- It does not check cryptographic signatures — signature verification will be added in v0.2
- It does not evaluate whether the AI agent's reasoning was correct or truthful

## Quick start

```bash
pip install -e .
fp-verify verify examples/happy_path_payment_release/bundle.json
fp-verify verify examples/rogue_wire_transfer_bundle/bundle.json
```

## Example output — rogue wire transfer

```
[i] bundle_id: bndl_rogue_001

Checks run:
  [✓]  OK   Structure: Required fields and object types
  [✓]  OK   ControlEnvelope: Envelope fields, risk tier, digest formats
  ...
  [-] FAIL  Scope binding: args_digest consistency across envelope, token, and approval scope
  [-] FAIL  Evidence policy: Source class and corroboration requirements by risk tier
  [-] FAIL  Token lifecycle: One-time token replay detection
  [-] FAIL  Review lineage: Challenge completion and anomalous approval latency

[!] Failures:

  [-] Scope binding
      reason_code : scope_args_digest_mismatch
      detail      : approval_records[0].scope.args_digest differs from control_envelope.args_digest
      detail      : approval bound to a different action

  [-] Scope binding
      reason_code : token_envelope_digest_drift
      detail      : invocation_token.args_digest differs from control_envelope.args_digest
      detail      : token was issued for a different payload than what the envelope describes

  [-] Evidence policy
      reason_code : weak_corroboration_insufficient
      detail      : risk_tier=critical requires corroborated evidence

  [-] Token lifecycle
      reason_code : token_replay_detected
      detail      : token_id=invk_v3_88b19x; consumed_at=2026-03-07T14:22:10Z

  [-] Review lineage
      reason_code : secondary_review_missing
      detail      : reviewer_latency_millis=214; anomaly_threshold_millis=1500; risk_tier=critical

[X] VERIFICATION REJECTED
[X] This bundle does not satisfy the required control checks
```

## Example scenarios

| Scenario | Expected result |
|---|---|
| `happy_path_payment_release` | ACCEPTED — complete valid payment release with proper evidence, review, and token lifecycle |
| `rogue_wire_transfer_bundle` | REJECTED — scope substitution, token replay, weak evidence, rubber-stamp review |
| `break_glass_without_incident` | REJECTED — break_glass=true invoked without a bound incident_id |
| `ambiguous_provider_result` | ACCEPTED — valid IN_DOUBT → RECONCILE_PENDING → COMPLETED reconciliation path |

## Documentation

Additional documentation is available in [`docs/`](docs/index.md): CLI usage, bundle structure, failure reason codes, and the public/private boundary.

## JSON output

```bash
fp-verify verify bundle.json --json
```

```json
{
  "ok": false,
  "bundle_id": "bndl_rogue_001",
  "failure_count": 5,
  "failures": [...]
}
```

## Public vs private

This repository is open because verification should not require trusting the runtime vendor.

The production runtime that generates these bundles — the Phoenix Membrane — is commercial and stays closed. You can verify any bundle it produces without ever seeing the runtime code.

## Part of

[dot.ink](https://dot.ink) — deterministic execution membrane for probabilistic intelligence.

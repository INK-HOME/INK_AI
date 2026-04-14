# Bundle structure

An execution bundle is a portable JSON document that carries the minimum facts required for offline verification.

## Core objects checked by `fp-verify`

- `control_envelope`
- `invocation_token`
- `evidence_refs`
- `approval_records`
- `token_record`
- `receipt`
- state transition lineage

## Typical questions the verifier answers

- Was the requested action bound to the same `args_digest` across envelope, token, and approval scope?
- Was the evidence set internally consistent and strong enough for the declared risk tier?
- Was the token replayed or consumed out of order?
- Did break-glass execution include an incident binding?
- Did the execution follow the legal state machine?

## Non-goals

`fp-verify` does not reconstruct raw payload bytes, prove model reasoning quality, or replace runtime signature/oracle validation.

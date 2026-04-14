# Ambiguous Provider Result — IN_DOUBT Reconciliation

A valid execution bundle where the provider result was ambiguous
and the system entered and resolved IN_DOUBT state.

## What this shows

An execution where the provider response was uncertain after STARTED,
triggering the reconcile workflow:

- STARTED → IN_DOUBT (provider timeout or ambiguous response)
- IN_DOUBT → RECONCILE_PENDING (ambiguity made explicit, dependent
  actions blocked)
- RECONCILE_PENDING → COMPLETED (reconciliation resolved with evidence)

This is correct behavior. The system did not retry blindly or silently
mark the action as failed. It preserved the ambiguous state, blocked
any dependent actions, and required explicit reconciliation before
continuing.

## Why this matters

Most systems either retry optimistically or fail closed. Both approaches
can cause duplicate side effects or silent data loss in distributed
environments. The IN_DOUBT state preserves the ambiguity as a first-class
fact until it is resolved with evidence.

## Expected verifier result

```
VERIFICATION ACCEPTED
All structural, scope-binding, state-machine, lineage, and control-flow checks passed
```

## Verify it

```bash
fp-verify verify bundle.json
```

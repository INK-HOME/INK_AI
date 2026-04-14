# Happy Path — Payment Release

A complete, valid payment release execution bundle.

## What this shows

A $29.95 refund that passes all control checks:

- Evidence quorum satisfied: 2-of-3 independent sources
- Policy epoch matches the execution token
- Token is one-time use and not replayed
- Review challenge completed within anomaly threshold
- State transitions follow the legal graph: PENDING_REVIEW → APPROVED → STARTED → COMPLETED
- Receipt sealed with root digest

## Expected verifier result

```
VERIFICATION ACCEPTED
All structural, scope-binding, state-machine, lineage, and control-flow checks passed
```

## Verify it

```bash
fp-verify verify bundle.json
```

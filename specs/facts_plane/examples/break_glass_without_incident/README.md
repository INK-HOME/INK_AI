# Break-Glass Without Incident

A break-glass execution attempt that violates two control checks.

## What this shows

An emergency override attempt that is rejected because:

1. **No incident binding** — break_glass=true requires an incident_id.
   Emergency overrides must be bound to a declared incident. Break-glass
   without an incident is structurally invalid.

2. **Weak evidence** — even in emergency mode, a critical-risk action
   requires corroborated evidence. This bundle has no qualifying evidence.

## Why this matters

Break-glass is not a bypass. It is a different authority path with
stricter requirements, not looser ones. An emergency override without
a bound incident is indistinguishable from an unauthorized escalation.

## Expected verifier result

```
VERIFICATION REJECTED
2 failures detected
```

## Verify it

```bash
fp-verify verify bundle.json
```

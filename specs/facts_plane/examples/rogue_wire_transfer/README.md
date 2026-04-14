# Rogue Wire Transfer

A wire transfer bundle that fails five distinct control checks.

## What this shows

A $50,000 wire transfer attempt with multiple control violations:

1. **Scope substitution** — the approval was bound to a different
   args_digest than what the control envelope describes. Someone
   approved action A but action B executed.

2. **Token/envelope drift** — the invocation token was issued for
   a different payload than what the envelope describes.

3. **Weak evidence** — a critical-risk action requires corroborated
   evidence from at least two independent source owners. This bundle
   has only one source in the corroboration group.

4. **Token replay** — the token was already marked CONSUMED before
   this execution started. One-time tokens cannot be reused.

5. **Rubber-stamp review** — a critical-risk action was approved
   in 214ms. The anomaly threshold is 1500ms. A reviewer who
   approves a $50,000 wire transfer in under 1.5 seconds is flagged.

## Expected verifier result

```
VERIFICATION REJECTED
5 failures detected
```

## Verify it

```bash
fp-verify verify bundle.json
```

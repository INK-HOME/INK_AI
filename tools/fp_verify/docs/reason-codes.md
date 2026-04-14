# Failure reason codes

These codes describe why a bundle was rejected.

## Common reason codes

- `scope_args_digest_mismatch` — approval scope does not match the control envelope payload
- `token_envelope_digest_drift` — invocation token was issued for a different payload
- `weak_corroboration_insufficient` — evidence was too weak for the declared risk tier
- `token_replay_detected` — a one-time token appears to have been reused
- `secondary_review_missing` — the bundle lacks the required review lineage for elevated risk
- `break_glass_incident_missing` — emergency execution did not bind to a concrete incident

Exact codes and their triggering conditions are defined by the verifier implementation and example bundles in this repository.

# .INK — Public GitHub Bundle (Curated Surface)

.INK is the execution-governance layer for AI systems operating under real stakes.

This public repository is intentionally curated. It exposes the doctrine, proof surfaces, schemas, examples, and verifier tooling needed to understand and inspect the system **without exposing the full internal runtime codebase**.

## Canonical doctrine

> .INK owns what must be proven.  
> The customer owns what they prefer.  
> The compiler derives necessity, never preference.

## What this bundle is

This bundle includes:
- public product and doctrine docs
- the updated compiler contract
- the public schema surfaces
- proof bundles and example artifacts
- the public offline verifier package
- supporting reference docs

## What this bundle is not

This bundle does **not** include:
- the full internal runtime source tree
- the private controlplane implementation
- internal binaries or build-only surfaces
- the full internal SDK and orchestration code

## Current release posture

- `CANDIDATE_READY`
- `BLOCKED_PENDING_PROOFCORE` for canonical proof surfaces
- runtime proof posture currently `PASS`

## Quick path

Read these first:
1. `docs/SYSTEM_BREAKDOWN.md`
2. `docs/POLICY_COMPILER_SPEC.md`
3. `docs/PROOF_OF_LIFE_PACKET.md`
4. `DEMO.md`

## Public verification path

```bash
cd tools/fp_verify
python -m pip install -e .
fp-verify ../specs/facts_plane/examples/happy_path_payment_release/bundle.json
```

## Contact

- Name: `.INK`
- Email: `romeo.singer@aol.com`
- Contact: `romeo.singer@aol.com`

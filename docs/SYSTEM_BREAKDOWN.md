# System Breakdown

## Current posture

- Release implication: `CANDIDATE_READY`
- Constitutional verdict: `BLOCKED_PENDING_PROOFCORE`
- Runtime proof verdict: `PASS`
- Canonical schema inventory: 51 unique canonical schemas
- Native-owner posture: Go controlplane active, Rust ProofCore required for canonical proof surfaces

## Authority order

1. AGI constitutional law decides whether a corridor is lawful.
2. The execution membrane enforces runtime transitions, write-before-act, proof surfaces, and edge validity.
3. The .INK integration surface exposes the developer-facing control layer.
4. EIA-AA remains subordinate and cannot override constitutional or runtime truth.
5. External proof tooling is evaluator-only and cannot become a second authority plane.

## Compiler alignment

The compiler now follows the same constitutional split as the runtime:

- .INK owns what must be proven.
- The customer owns what they prefer.
- `proof_minimum` is the default compile profile.
- `extended` is the explicit customer-overlay profile.

## Canonical artifacts

The public artifact chain is defined around six canonical runtime objects:

- IntentEnvelope
- AuthorityDecision
- IntegrityCertification
- ResultReceipt
- ReconcileReceipt
- ReplayProof

## What this public bundle includes

This public GitHub bundle includes:
- public doctrine and positioning docs
- compiler doctrine and release posture
- canonical AGI and Facts Plane schema surfaces
- public example artifacts and proof bundles
- the public verifier package and tests
- contact and security surfaces

## What this public bundle excludes

This public bundle intentionally excludes:
- full internal runtime implementation
- private controlplane code
- internal binaries and build-only surfaces
- full internal SDK/runtime source tree
- private orchestration glue and internal-only generated artifacts

This is a curated public proof and specification surface, not a source dump.

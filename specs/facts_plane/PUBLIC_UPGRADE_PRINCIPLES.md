# dot.ink Public Upgrade Principles

## Purpose

dot.ink is built on a simple rule:

> trust should come from proof, not architecture volume.

These principles define how we evaluate improvements to execution-grade systems. They are intentionally public because category legitimacy should be grounded in visible standards, not vendor mystique.

---

## Core Standard

A change is valuable when it makes one important statement more true:

> This system can be trusted to do exactly this, under these conditions, and we can prove it.

If a change does not strengthen that sentence, it is probably noise.

---

## Principles


## Objective vs Subjective Boundary

dot.ink enforces a strict boundary:

- Objective layer (owned by dot.ink): provable invariants, execution constraints, receipts, readbacks, and replayable truth
- Subjective layer (owned by the customer): thresholds, exceptions, segmentation, and business preference

Upgrades must respect this boundary.

A valid upgrade:
- strengthens provable guarantees
- reduces ambiguity
- increases replayability

An invalid upgrade:
- invents customer policy
- blurs authority boundaries
- replaces proof with interpretation


### 1. Proof over narrative

A system should be judged by what it can prove, not by how much architecture it can describe.

We prefer:
- verifier results over claims
- receipts over summaries
- replayable traces over post-hoc explanations
- deterministic outputs over “best effort” interpretations

---

### 2. Failure containment over feature growth

Execution systems are defined by how they behave when reality becomes partial, delayed, ambiguous, or adversarial.

A good upgrade:
- prevents silent failure
- blocks unsafe continuation
- makes uncertainty explicit
- preserves repairability

A bad upgrade:
- expands capability while widening ambiguity
- adds flexibility by weakening control
- hides failure behind retries or narratives

---

### 3. Boundary clarity matters

Authority, execution, and verification should be distinct enough that they cannot be confused at runtime.

A mature system makes it obvious:
- who can authorize
- what can execute
- when execution becomes uncertain
- how truth is re-established

Confused boundaries are not just bad design. They are an attack surface.

---

### 4. Reproducibility is part of trust

If a fresh machine cannot reproduce the result, the claim is weaker than it sounds.

We prefer:
- one canonical demo path
- one canonical schema family
- one reproducible install path
- one portable proof artifact

Trust increases when the path from claim to evidence gets shorter.

---

### 5. Evidence beats language

A system should not rely on polished language to appear rigorous.

The strongest artifacts are:
- successful verifier output
- replay traces
- deterministic bundles
- failure receipts
- strict demo paths
- fresh-machine reproducibility

Good language can clarify evidence. It cannot replace it.

---

### 6. Compression is a feature

A mature system usually gets:
- smaller
- clearer
- harder to fake

When a system improves, it should often remove overlapping concepts, not add them.

We treat compression as a positive signal when it increases proof density.

---

### 7. No decorative complexity

New layers, names, modules, or abstractions should exist only if they do at least one of the following:
- close a real failure mode
- remove boundary ambiguity
- improve reproducibility
- produce a new verifiable artifact
- replace multiple weaker objects with one stronger one

If a change mainly makes the architecture feel more complete, it is probably decorative seriousness.

---

## Public Operating Law

> No new layer unless it deletes an old layer, closes a real failure mode, or produces a new verifiable artifact.

---

## What This Means in Practice

We prefer:
- one clear demo over five overlapping demos
- one canonical object over multiple parallel truth objects
- one verifier that catches important lies over a large surface of partial checks
- one narrow commercial wedge over broad conceptual sprawl
- one proof artifact that a third party can validate over a long explanation of intent

---

## What We Optimize For

We optimize for proof density:

> fewer moving parts per unit of confidence

We are skeptical of architecture volume:

> more moving parts per unit of narrative

The distinction matters because execution-grade systems should become harder to fake, not easier to describe.

---

## Closing

The point of these principles is not to make systems sound senior.

It is to make them:

- more trustworthy
- more reproducible
- more legible under stress
- and more resistant to failure theater

A good system is not merely impressive-looking.

It is inspectable, bounded, and provable.

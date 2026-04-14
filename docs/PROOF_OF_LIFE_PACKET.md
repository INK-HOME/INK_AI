# dot.ink Proof-of-Life Packet

## Live proof surface for the execution membrane

### Purpose

This packet defines the live stress-test surface used to prove that the membrane is not a static reviewer packet or a curated artifact bundle.

It exists to answer a simple question:

**Does the membrane behave honestly under live load, random inputs, and ugly failure conditions?**

This packet is not a product overview and not a legal commitment. It is a proof-of-behavior surface.

---

## 1. What the Proof-of-Life demonstrates

The Proof-of-Life run is intended to establish six claims.

1. The membrane handles success paths cleanly.
2. The membrane handles denial paths cleanly.
3. The membrane handles ambiguity honestly.
4. The verifier is independent of the runtime narrative.
5. Important tampering is detectable.
6. The runtime can export artifacts that remain reviewable outside the live system.

---

## 2. Why a live proof surface matters

A static reviewer packet can still be accused of curation.

A live randomized run narrows that accusation.

The point is not to prove infinite correctness.

The point is to show, in public or in a serious buyer review, that the membrane:

- stays within explicit state laws,
- makes hard failures visible,
- exports the right artifacts,
- and does not silently rewrite ugly cases into narrative success.

In plain English:

**This is the beam test, not the blueprint.**

---

## 3. Anti-fake operating rules

The Proof-of-Life should obey four rules.

### A. Independent verifier rule
The verifier must not depend on hidden runtime state.

### B. Public entropy rule
The run seed should come from a public entropy source so the workload cannot be pre-curated.

Examples:
- latest Bitcoin block hash
- NIST randomness beacon
- agreed external public event digest

### C. Forced ugly-case rule
The run must include failure injection, not just success traffic.

### D. Artifact export rule
Every significant event class must leave a replayable artifact trail.

---

## 4. The Randomizer engine

The Randomizer is the load and chaos generator for the Proof-of-Life run.

### Core workload classes

- payout happy path
- payout denial path
- payout timeout / ambiguous path
- refund happy path
- refund contradiction / quorum-fail path
- stale-epoch attempts
- invalid or replayed review attempts
- invalid or replayed token attempts

### Recommended failure injectors

#### Network snap
Kill or sever the connection between `STARTED` and acknowledgement.

Expected membrane behavior:
- `IN_DOUBT`
- reconcile opens
- no silent retry
- no silent completion claim

#### Lying witness
Inject materially conflicting evidence.

Expected membrane behavior:
- contradiction state recorded
- evidence sufficiency fails
- no control envelope issuance
- no `PREPARED`
- no `STARTED`

#### Time warp
Submit a request against a policy epoch that is stale or expired.

Expected membrane behavior:
- authorization denied
- no token for execution
- no boundary crossing

#### Replay attempt
Reuse approval or token material outside its valid scope.

Expected membrane behavior:
- verifier-visible rejection
- no execution authorization

---

## 5. What the reviewer sees

A serious reviewer should see a compact ledger, not a decorative dashboard.

Suggested live ledger columns:

| Timestamp | Transaction ID | Workflow | Membrane State | Result | Proof Artifacts |
|---|---|---|---|---|---|
| 14:02:01 | TX-998 | payout.release | ACKNOWLEDGED | SUCCESS | Receipt, Bundle |
| 14:02:05 | TX-999 | refund.issue | IN_DOUBT | RECONCILING | WAL, Reconcile |
| 14:02:10 | TX-1000 | payout.release | DENIED | EPOCH_STALE | Policy Proof |

The visual surface should stay sparse.

Its purpose is to expose state law, not look expensive.

---

## 6. Artifact outputs per transaction

Each transaction class should export enough material to allow third-party replay.

Minimum expected export set:

- normalized request
- policy epoch reference or digest
- evidence-set summary or evidence refs
- approval artifact when required
- control envelope when issued
- invocation token when issued
- WAL `PREPARED`
- WAL `STARTED` when crossed
- decision receipt
- evidence bundle manifest
- reconcile case and closure artifacts where required

---

## 7. Runtime invariants the live run must defend

The Proof-of-Life run should explicitly measure whether the membrane preserved these invariants under load:

1. no privileged side effect without `PREPARED`
2. no privileged side effect without `STARTED`
3. no `STARTED` without `PREPARED`
4. no stale epoch accepted as current
5. no replayed authority accepted as valid
6. no contradiction flattened into allow
7. no ambiguous post-start state flattened into success or denial without reconcile
8. no artifact export gap for reviewable transactions
9. no subjective policy is treated as objective truth
10. no customer preference is allowed to bypass objective invariants

---

## 8. Verifier behavior during the run

The live verifier should continuously sample or consume exported artifacts and perform:

- schema checks
- digest recomputation
- signature validation where present
- epoch consistency checks
- action-binding checks
- write-before-act ordering checks
- illegal state transition checks
- tamper-failure checks

A strong design choice is to surface verifier failures live as visible red events rather than burying them in a log.

---

## 9. End-of-run structural integrity report

At the end of the Proof-of-Life window, the run should issue a compact report.

Suggested fields:

- total transactions processed
- transaction class breakdown
- successful executions
- denied executions
- `IN_DOUBT` openings
- reconcile closures by class
- verifier pass count
- verifier fail count
- tamper tests attempted
- tamper tests correctly failed
- artifact export completeness percentage

Example framing:

- Total Loads Handled: 14,400
- Total Structural Failures: 0
- Total Ambiguities Resolved: 152
- Verification: 100% of artifact sets passed recomputation except deliberate tamper cases

---

## 10. What counts as a real failure

A serious reviewer should know what would count against the system.

Real failure examples:

- privileged side effect initiated without durable `PREPARED` then `STARTED`
- stale epoch accepted as current
- contradiction or quorum failure flattened into allow
- ambiguous post-start execution presented as confirmed without closure basis
- replayed authority accepted as fresh
- verifier passes a materially tampered artifact set
- artifact export is incomplete for a claimed successful or denied transaction

These are not “demo glitches.”

They are structural failures.

---

## 11. What the Proof-of-Life is not

It is not a full product audit.
It is not a legal warranty.
It is not a substitute for production hardening.
It is not a replacement for claim-specific artifacts.

Its function is narrower:

**to show that the membrane’s truth discipline survives contact with live conditions.**

---

## 12. One-line summary

**The Proof-of-Life run is the live stress surface that shows the membrane is not being sold on a packet of claims, but on behavior that stays honest under load, randomness, and failure.**


---

## Objective vs Subjective Enforcement

The Proof-of-Life run validates that:

- objective invariants are always enforced
- subjective policy does not override execution law
- ambiguity is not resolved through interpretation

dot.ink proves the floor holds.

It does not prove that customer policy is correct.

# Hello World

This repository does not ship the full internal runtime or SDK implementation.

Instead, the public quick path is:

1. inspect the canonical schemas
2. run the public verifier against the included example bundles
3. review the proof-of-life packet and system breakdown

A representative public hello-world flow demonstrates three outcomes:

- a valid action executes and yields portable proof artifacts
- an invalid action is blocked before boundary crossing
- an ambiguous action lands in `IN_DOUBT` and requires reconcile

That is the public behavioral shape of .INK.

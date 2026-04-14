## .ink — Provable Execution Membrane for High-Stakes AI

.ink is a control layer for AI systems that take real-world actions.

It does not treat model output as authority.
It requires a governed path from proposed action to authorized execution:
explicit envelope, bounded approval, durable pre-action state, and a replayable proof bundle.

This repository is the public proof surface for.ink.
It contains public doctrine, constitutional schemas, example bundles, and an offline verifier.
The private commercial runtime is intentionally not shipped here.

## Why it exists

Most AI systems fail at the boundary where soft reasoning meets irreversible action.
A model can be helpful, fast, and usually correct while still being structurally unsafe to trust with money movement, record mutation, access changes, or operational control.

dot.ink exists to solve that boundary problem.

## Five-minute proof

```bash
cd tools/fp_verify
python -m pip install -e .
fp-verify ../specs/facts_plane/examples/happy_path_payment_release/bundle.json
fp-verify ../specs/facts_plane/examples/ambiguous_provider_result/bundle.json
fp-verify ../specs/facts_plane/examples/rogue_wire_transfer/bundle.json

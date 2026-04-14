# Five-Minute Proof

```bash
cd tools/fp_verify
python -m pip install -e .
fp-verify ../specs/facts_plane/examples/happy_path_payment_release/bundle.json
fp-verify ../specs/facts_plane/examples/ambiguous_provider_result/bundle.json
fp-verify ../specs/facts_plane/examples/rogue_wire_transfer/bundle.json
```

What this proves:
- the public verifier installs from declared metadata
- canonical example bundles are portable
- valid bundles pass
- materially bad bundles fail
- ambiguity is preserved as a first-class state

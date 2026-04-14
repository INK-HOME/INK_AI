# Fresh Machine Smoke

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
cd tools/fp_verify
python -m pip install -e .
pytest -q
fp-verify ../specs/facts_plane/examples/happy_path_payment_release/bundle.json
fp-verify ../specs/facts_plane/examples/ambiguous_provider_result/bundle.json
fp-verify ../specs/facts_plane/examples/rogue_wire_transfer/bundle.json || true
```

What this demonstrates:
- the public verifier package installs cleanly
- the included tests run
- valid proof bundles verify
- deliberately bad bundles are rejected

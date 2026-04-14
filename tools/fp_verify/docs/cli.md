# CLI usage

## Install

```bash
pip install -e .
```

## Verify a bundle

```bash
fp-verify verify examples/happy_path_payment_release/bundle.json
fp-verify verify examples/rogue_wire_transfer_bundle/bundle.json
```

## JSON output

```bash
fp-verify verify examples/rogue_wire_transfer_bundle/bundle.json --json
```

## Exit behavior

- accepted bundles return a successful result
- rejected bundles print failures with reason codes and details
- malformed or unreadable bundle files return an error before verification completes

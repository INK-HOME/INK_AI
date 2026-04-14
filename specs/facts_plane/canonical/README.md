# Canonicalization

All proof artifacts in the facts-plane use a strict canonicalization
profile. This ensures that digest values are deterministic across
implementations and languages.

## Profile: dotink-c14n-v1

| Rule | Value |
|------|-------|
| Encoding | UTF-8 |
| Unicode normalization | NFC |
| Object key ordering | Sorted lexicographically |
| Whitespace | None between tokens |
| Number format | No floats. Use integers or canonical decimal strings. |
| Null handling | Omit optional null fields from digest input |
| Timestamp format | ISO-8601 UTC — `YYYY-MM-DDTHH:MM:SSZ` |

## Forbidden in signed artifacts

- Floating point numbers — use integers (smallest unit) or canonical
  decimal strings instead
- Non-NFC unicode strings
- Unsorted object keys

## Digest algorithm

The canonical digest is computed as:

```
BLAKE3-256(canonical_json_bytes(payload))
```

Expressed as a lowercase hex string prefixed with the algorithm:

```
blake3-256:7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d906
```

SHA-256 is accepted as a fallback where BLAKE3 is not available:

```
sha256:2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
```

## Cross-language parity

The `digest_vectors.json` file contains canonical test vectors that
all implementations must produce identical output for.

Implementations in Python, Go, and Rust are provided in the
dot.ink SDK and membrane repositories. CI enforces parity across
all three languages on every commit.

## Test vectors

See `digest_vectors.json` for the canonical test vector set.

Each vector contains:
- `name` — description of what is being tested
- `payload` — the input object
- `canonical_json` — the expected canonical JSON string
- `blake3_hex` — the expected BLAKE3-256 digest (where available)
- `sha256_hex` — the expected SHA-256 digest

## Event taxonomy

See `EVENT_TAXONOMY.json` for the complete registry of event types
used in WAL records and execution traces.

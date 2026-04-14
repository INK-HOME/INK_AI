# Contributing

Contributions are welcome for:

- New schema versions for existing artifact types
- Additional test vectors and fixtures
- Canonicalization clarifications
- Documentation improvements
- Cross-language canonicalization implementations

## Before contributing

Please open an issue before making large interface or semantic changes.
Schema changes that affect the proof artifact language require discussion
before implementation.

## What belongs here

- Artifact language definitions (schemas)
- Canonicalization rules and test vectors
- Valid and invalid fixture examples
- Documentation that helps third parties verify bundles

## What does not belong here

- Runtime enforcement logic
- Private authority kernel code
- Production deployment configuration
- Internal methodology documents

## Schema versioning

See VERSIONING.md for the schema versioning rules.
Breaking changes to existing schemas require a new version.
Additive changes may be made to existing minor versions.

## Test vector requirements

Every new schema must ship with:
- At least one valid fixture
- At least one invalid fixture that tests the most important constraint

See TEST_VECTORS.md for the full required vector set.

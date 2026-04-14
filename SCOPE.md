# Bundle Scope

This public bundle is intentionally narrower than the internal stack.

Included:
- public doctrine and compiler contract
- canonical schemas and example artifacts
- public verifier package
- proof-of-life materials
- public contact and security surfaces

Excluded:
- full internal runtime implementation
- internal controlplane code
- private orchestration surfaces
- internal-only generated artifacts and build outputs
- full source exposure of the internal stack

## Additional public-surface exclusions

- binary reference files (`references/*.pdf`, `references/*.docx`) are intentionally excluded from the public repo surface
- public contact uses email only; phone number is intentionally omitted from the GitHub bundle

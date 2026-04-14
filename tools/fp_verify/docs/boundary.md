# Public/private boundary

This repository is public because independent verification should not require trusting a runtime vendor.

## Public in this repository

- the offline verifier
- example bundles
- deterministic public verification rules
- documentation needed to understand verification results

## Private outside this repository

- production runtime internals
- private authority services
- commercial control-plane implementation details
- organization-specific operating procedures and secret material

The boundary is deliberate: bundles should be independently checkable even when the runtime stays closed.

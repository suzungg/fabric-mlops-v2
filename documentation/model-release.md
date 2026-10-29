# Model release design

**Proposed custom process, not an implemented release pipeline.**

Fabric supports lifecycle management of item definitions, but its documented
ML Git/deployment integration does not include model versions or experiment
runs. [Official reference](https://learn.microsoft.com/en-us/fabric/data-science/machine-learning-artifacts-git-deployment-pipelines).

## Two delivery paths

| Path | Payload | What it does not establish |
| --- | --- | --- |
| Source/item deployment | Supported notebook, environment, item and configuration definitions | That trained weights arrived, predictions are correct or the release is approved |
| Model-package transfer | Frozen model files, signature and release manifest | That destination runtime, dependencies, data access or serving are compatible |

## Release sequence

1. Select the evaluated DEV candidate. Record its code commit, training-data
   reference, environment/dependencies and evidence.
2. Export a model package to approved protected storage; compute integrity
   hashes and prevent mutation of the release artifact. Store no secrets.
3. Deploy supported definitions to TEST and bind destination resources. Do not
   assume hard-coded workspace/model identifiers are automatically remapped.
4. Transfer and register the package in TEST through supported APIs and
   authorized identities. Record the destination-local model ID/version and
   verify package integrity plus prediction behavior.
5. Complete acceptance tests and obtain explicit approval tied to the package
   hash and compatible source/configuration.
6. Deploy compatible PROD definitions and import the same approved package.
   Record the new local version mapping, smoke-test, then activate scoring.
7. Retain the previous package, configuration and compatible code/environment
   for rollback.

## Release identity

A release manifest should describe:

| Field | Meaning |
| --- | --- |
| Release ID | Stable identity for this approved combination |
| Model package digest | Integrity identity of the frozen delivered model |
| Source commit | Training/scoring code version |
| Environment reference | Runtime and dependency definition |
| Data reference | Reproducible training input reference or snapshot |
| Signature | Model input/output contract |
| Target mapping | Workspace-local model ID and version for each environment |
| Validation evidence | Actual results, scope, dates and acceptance criteria |
| Approval | Explicit decision and responsible role |
| Rollback reference | Previous known-good release/configuration |

This is a conceptual manifest, not a supplied schema or ready-to-run API.
Do not assume the registry's metadata is byte-identical between workspaces;
preserve the package identity and verify behavior after registration.

## Rollback and retraining

Restore a previously validated model/package with compatible code, environment
and consumer configuration. Metadata-only rollback is insufficient. Consider
output schema compatibility and whether downstream prediction tables need
reprocessing.

Retraining in TEST or PROD produces a new candidate. If that strategy is
chosen, evaluate and approve the newly trained package rather than claiming
it is the same artifact tested earlier.

## Implementation work still required

Choose artifact storage, credential handling, identities, exact export/import
APIs, idempotency, dependency binding, integrity checks and approval controls.
Prove transfer and registration with a synthetic model before using real
customer artifacts. This repository supplies none of those implementations.

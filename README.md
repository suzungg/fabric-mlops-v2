# Fabric MLOps v2

**A Fabric-first reference architecture for classical machine learning.**

Adapted from [Azure MLOps v2](https://github.com/Azure/mlops-v2), this repository
explains how its ten-stage lifecycle maps to Microsoft Fabric: data preparation,
experimentation, model release, batch scoring, optional online serving, and
monitoring.

> **Architecture and documentation, not a deployment accelerator.**
> This repository does not contain executable training notebooks, release
> pipelines, infrastructure templates, or a validated cross-workspace model
> transfer implementation. Dashed/custom steps describe work to implement.
> It is not an official Microsoft product or support commitment.

## Architecture

[![Fabric-first classical MLOps architecture](documentation/architecture/media/Fabric_CML_Architecture.png)](documentation/architecture/media/Fabric_CML_Architecture.png)

[Read the ten-step explanation](documentation/architecture/classical.md) |
[Editable draw.io source](documentation/architecture/media/Fabric_CML_Architecture.drawio) |
[Scalable SVG](documentation/architecture/media/Fabric_CML_Architecture.svg)

The single-page layout follows the Azure ML reference: data estate on the
left, development and administration in the middle-left, CI in the centre,
staging above production on the right, and monitoring/feedback loops at the edge.

## Design principles

- **Fabric owns training and batch scoring.** Use notebooks/Spark, MLflow
  experiments/models, and pipeline-driven PREDICT against Lakehouse data.
- **Code deployment is not model delivery.** Fabric ML Git/deployment integration
  promotes supported metadata, not experiment runs or trained model versions.
  Use a separately validated model-package release process.
- **Online inference is optional.** Evaluate Fabric model endpoints where their
  preview status and constraints are acceptable; retain Azure ML online serving
  when requirements call for it. Neither is needed for the baseline batch path.
- **Monitor, evaluate, then approve.** Drift signals can initiate candidate
  retraining, but do not directly authorize production model replacement.

## Documentation

| Guide | Contents |
| --- | --- |
| [Architecture overview](documentation/architecture/README.md) | Scope, assumptions and how to read the diagram |
| [Classical ML lifecycle](documentation/architecture/classical.md) | All ten numbered stages, owners, outputs and acceptance evidence |
| [Model release design](documentation/model-release.md) | Separate delivery paths, target version mapping, approval and rollback |
| [Validation checklist](documentation/validation.md) | Evidence needed before implementation can be called production-ready |
| [Sources and feature status](documentation/sources.md) | Official references, preview caveats and research date |

## Important feature boundaries

Documentation was reviewed on **29 October 2026**. Recheck current Microsoft
documentation before implementing a design.

| Capability | Boundary |
| --- | --- |
| ML experiments/models in Git and deployment pipelines | **Preview; metadata only.** Model versions and runs are not promoted. |
| Fabric PREDICT | Requires supported MLflow flavors and populated signatures; restrictions apply. |
| Fabric ML model endpoints | **Preview.** Flavor/schema, capacity, access and performance requirements must be checked. |
| ML-specific Monitoring hub integration | **Preview.** Operational metrics are not model-quality evaluation. |
| Package transfer, quality checks and release gates | **Proposed custom automation**, not implemented by this repository. |

See [sources](documentation/sources.md) for the specific documents supporting
these statements.

## Use and edit

1. Read the [architecture](documentation/architecture/classical.md) and resolve
   its workload-specific assumptions.
2. Download the `.drawio` file and open it in diagrams.net or draw.io Desktop.
   All shapes, labels and connectors are editable.
3. Keep the PNG/SVG exports aligned with the final source and update the
   documentation when architecture semantics change.
4. Follow the [validation checklist](documentation/validation.md) before
   implementing or relying on any release or serving path.

This is a logical reference, not a private-network diagram or a compliance,
availability, performance, or customer-approval claim. Examples contain no
customer-specific environment or data.

## Contributing and license

See [CONTRIBUTING.md](CONTRIBUTING.md). This repository is MIT licensed; see
[LICENSE](LICENSE) and [NOTICE.md](NOTICE.md) for upstream attribution.

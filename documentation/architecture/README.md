# Architecture overview

This repository currently covers **classical ML on tabular data**, adapted from
the [Azure ML classical architecture](https://github.com/Azure/mlops-v2/blob/main/documentation/architecture/classical.md).
It does not claim to implement the upstream accelerator's other scenarios.

## Read the diagram

[![Fabric classical ML architecture](media/Fabric_CML_Architecture.png)](media/Fabric_CML_Architecture.png)

- Green circles correspond to [stages 1-10](classical.md).
- Cyan/blue header bands and the persona legend follow the original reference.
- Dashed process boxes represent lifecycle tasks, not proof of implemented jobs.
- An asterisk marks custom release, checks or triggers.
- A double asterisk marks documented preview capabilities.
- Long outer arrows represent model-review and infrastructure-review feedback.

Stage panels are logical groupings. Production can include a Fabric workspace
and, if chosen, an endpoint in a **separate Azure ML workspace**. Drawing both
under the production lifecycle does not place Azure ML inside Fabric.

## Baseline assumptions

| Assumption | What must be confirmed |
| --- | --- |
| Fabric-first development and batch inference | The actual model flavor, signature, libraries and Spark runtime are compatible. |
| Separate dev/test/prod workspaces | Capacity, data access, identity, bindings and environment isolation are designed. |
| An immutable package is promoted | Authenticated transfer, integrity checking and target registration are implemented and tested. |
| Online inference is conditional | A business requirement exists and its serving target meets agreed constraints. |
| Quality monitoring has meaningful evidence | Baselines, labels, slices, thresholds and owners are defined. |

No region, SKU, tenant configuration, network topology, recovery objective or
performance threshold is prescribed without workload requirements.

## Files

- [PNG preview](media/Fabric_CML_Architecture.png)
- [Editable draw.io source](media/Fabric_CML_Architecture.drawio)
- [SVG export](media/Fabric_CML_Architecture.svg)
- [Ten-stage explanation](classical.md)
- [Release design](../model-release.md)

The diagram uses neutral vector symbols, not the source image's product logos.

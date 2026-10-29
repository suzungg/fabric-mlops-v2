# Contributing

Keep this repository focused on an accurate, evidence-backed Fabric-first MLOps
reference. Open an issue for a correction or submit a focused pull request.

## Architecture and documentation changes

- Link to authoritative sources for product support claims and record the date.
- Distinguish built-in features, preview features and proposed custom automation.
- Preserve the distinction between model metadata and trained-model delivery.
- Explain important changed assumptions or decisions.
- Do not report tests, deployments or approvals that did not occur.
- Check relative links and keep the README, stage guide and diagram consistent.

## Diagram changes

Edit `documentation/architecture/media/Fabric_CML_Architecture.drawio`, not only
the raster. Export matching PNG and SVG files with the same base filename.
Inspect labels, connectors, endpoints, boundaries and preview/custom markers.
Use symbols/assets with suitable rights and retain attribution.

## Data and credentials

Do not submit customer material, access tokens, connection strings, workspace
identifiers, model weights or training data. Use synthetic examples. Follow
your organization's approved vulnerability-reporting process rather than
posting sensitive exploit details or credentials in a public issue.

If executable automation is added later, document its prerequisites and add
appropriate tests; do not present a placeholder as a functioning accelerator.

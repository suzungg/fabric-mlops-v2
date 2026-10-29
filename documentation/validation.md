# Validation checklist

These checks describe evidence to collect. **No cloud/runtime test has been
performed by this repository.** A rendered diagram or a passing documentation
check does not establish architectural feasibility.

| Check | Evidence needed |
| --- | --- |
| Workload requirements | Approved scope, batch/online need, thresholds, data location, recovery objectives and preview policy |
| Fabric runtime | Actual model flavor, signature and dependency compatibility with target Spark/PREDICT |
| Environment isolation | Correct identities, target bindings, source permissions and denied unauthorized access |
| Model transport | Synthetic cross-workspace export/import; hashes and target-local version mapping |
| Metadata separation | Demonstrate that item deployment alone does not deliver the trained model |
| Scoring correctness | Agreed expected outputs and schema checks on representative controlled inputs |
| Batch reliability | Retry and partial-failure handling, idempotent output publication and observability |
| Online serving, if selected | Actual endpoint authentication, network access, request contract and load behavior |
| Quality monitoring | Baselines, outcomes/labels, slices, thresholds and tested notification routing |
| Retraining gate | Injected signal creates a candidate without bypassing tests/approval |
| Release approval | Evidence and package hash tied to the decision |
| Rollback | Restore prior model, compatible code/runtime and consumer configuration |
| Capacity/operations | Measured workload behavior, ownership and incident response |

Record results as **not run**, **passed**, **failed**, or **inconclusive**, along
with evidence and scope. Do not invent thresholds, approvers or positive
results. Missing data remains unresolved.

## Reviewing diagram changes

Check that stages, connectors, arrow direction and logical groupings still
match the intended lifecycle. Export PNG and SVG from the final editable
source, then inspect at full size and enlarged detail for overlaps and clipping.
Keep custom and preview markers visible.

# Sources and feature status

Reviewed **29 October 2026**. Feature support can change: verify the latest
documentation and your actual tenant/region/runtime before implementation.
Documented support does not guarantee subscription access, quota or live capacity.

| Source | What it supports |
| --- | --- |
| [Azure MLOps v2 classical architecture](https://github.com/Azure/mlops-v2/blob/main/documentation/architecture/classical.md) | Source lifecycle and diagram layout |
| [Fabric ML experiments](https://learn.microsoft.com/en-us/fabric/data-science/machine-learning-experiment) | Runs, parameters, metrics and artifacts |
| [Fabric ML models](https://learn.microsoft.com/en-us/fabric/data-science/machine-learning-model) | Model registration, versions and signatures |
| [PREDICT batch scoring](https://learn.microsoft.com/en-us/fabric/data-science/model-scoring-predict) | Supported MLflow flavors and signature restrictions; no multi-tensor input/output |
| [ML Git and deployment integration](https://learn.microsoft.com/en-us/fabric/data-science/machine-learning-artifacts-git-deployment-pipelines) | **Preview; metadata only**, not trained versions or experiment runs |
| [Deployment pipelines](https://learn.microsoft.com/en-us/fabric/cicd/deployment-pipelines/intro-to-deployment-pipelines) | Supported item deployment and feature-specific preview status |
| [Notebook source control/deployment](https://learn.microsoft.com/en-us/fabric/data-engineering/notebook-source-control-deployment) | Notebook definitions and target dependency binding |
| [Notebook activity](https://learn.microsoft.com/en-us/fabric/data-factory/notebook-activity) | Pipeline orchestration and workspace-identity prerequisites |
| [Fabric ML model endpoints](https://learn.microsoft.com/en-us/fabric/data-science/model-endpoints) | **Preview** online serving; documented flavors include Keras, LightGBM, Sklearn and XGBoost; excludes tensor/no-schema models |
| [Azure ML MLflow online deployment](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-deploy-mlflow-models-online-endpoints?view=azureml-api-2) | Registered compatible MLflow model deployment and runtime dependencies |
| [Fabric ML monitoring](https://learn.microsoft.com/en-us/fabric/data-science/monitor-machine-learning-experiments-models) | **Preview** ML-specific monitoring and endpoint traffic visibility |
| [OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview) | Lake/workspace organization and governance |
| [Fabric Capacity Metrics](https://learn.microsoft.com/en-us/fabric/enterprise/metrics-app) | Operational capacity health and utilization |

## What the sources do not establish

The exact custom model-transfer workflow, package integrity mechanism,
approval controls, idempotent scoring publication and data/model-quality
checks in this design are **proposals**, not capabilities proven by these
citations. They require implementation and validation.

No customer-specific policy, deployment, security approval, compliance
certification or service-level guarantee is asserted.

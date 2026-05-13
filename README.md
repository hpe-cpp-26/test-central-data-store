# ML Training Pipeline — Experiment Tracking Design

This document defines the architecture for the internal ML training pipeline,
covering dataset versioning, experiment tracking, model registry, and
promotion workflows for production deployment.

Dataset Management

    ------------------
    Training datasets are versioned using DVC and stored in object storage (S3).
    Each dataset version is tagged with a schema hash to detect silent drift.
    Splits (train / val / test) are fixed per version to ensure reproducibility
    across experiment runs.

    Experiment Tracking
    -------------------
    MLflow is used to log hyperparameters, metrics, and artefacts per run.
    Each experiment is associated with a Git commit SHA and a dataset version tag.
    Runs are grouped by model family (classification, ranking, embedding).

    Training Infrastructure
    -----------------------
    GPU jobs run on Kubernetes using the training operator. Resource quotas are
    enforced per team. Spot instance interruptions are handled via checkpoint
    resumption — jobs save state every 500 steps.

    Model Registry and Promotion
    ----------------------------
    Trained models are registered in MLflow Model Registry with stage labels:
    Staging → Canary → Production. Promotion requires sign-off from a model
    reviewer and passing evaluation against a held-out benchmark dataset.

    Serving
    -------
    Production models are served via Triton Inference Server behind an internal
    gRPC gateway. Latency SLOs: P50 < 10ms, P99 < 50ms for embedding models.
    Model versions are shadowed before full cutover to detect regression.

    Monitoring
    ----------
    Feature drift is detected using PSI scores computed daily against the
    training distribution. Alerts fire when PSI > 0.2 for any top-20 feature.
    Prediction confidence histograms are logged per model per hour.

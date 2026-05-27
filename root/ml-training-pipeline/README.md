# ml-training-pipeline

## Group Overview
This document group contains technical documentation for the ML Training Pipeline project, focusing on the design and implementation of a reproducible and scalable system for managing machine learning workflows. It covers experiment tracking, dataset versioning, model promotion, and deployment infrastructure.

## Documents in this Group
- **ML Training Pipeline — Experiment Tracking Design** (Source: Confluence)  
  Defines the architecture for dataset versioning, experiment tracking, model registry, and promotion workflows for production deployment.
- **ML Training Pipeline — Experiment Tracking Design** (Source: Confluence)  
  This document outlines the architecture and design for a machine learning training and deployment pipeline. It covers dataset versioning using DVC and S3, experiment tracking with MLflow for logging hyperparameters, metrics, and artifacts, and a model registry for managing model lifecycle stages from staging to production. The pipeline supports GPU-accelerated training on Kubernetes with checkpointing for fault tolerance. It details model promotion workflows requiring review and benchmark evaluation. Production models are served via Triton Inference Server with gRPC, incorporating shadowing for safe deployments. Monitoring includes feature drift detection using PSI scores and prediction confidence logging to ensure model health and performance.

## Key Topics
- Dataset versioning
- Experiment tracking
- Model promotion workflow
- MLflow integration
- GPU-based training
- Model registry
- Feature drift monitoring
- Model serving with Triton
- DVC for dataset versioning
- Kubernetes-based training infrastructure
- Checkpointing
- Model shadowing
- PSI scores
- Prediction confidence

## Team & Metadata

| Field       | Value                  |
|-------------|------------------------|
| Team        | ml-platform            |
| Project     | ml-training-pipeline   |
| Status      | active                 |
| Last Updated| 2026-05-27             |
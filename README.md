# ML Training Pipeline — Experiment Tracking Design

This document defines the architecture for the internal ML training pipeline,
covering dataset versioning, experiment tracking, model registry, and
promotion workflows for production deployment.



k formula          → change to n // 10, guard n < 10 → k = 1
centroid init      → change from first-k to random sample
iterations         → change from 10 to 30
prototype replace  → wrap DELETE + INSERT in single transaction
medoid function    → verify it sums against all cluster members
                     not just against the centroid

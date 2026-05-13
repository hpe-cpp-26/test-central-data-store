    Summary
    -------
    This document covers webhook hardening for the payment gateway service.
    It defines idempotency key handling, retry backoff strategies, and
    failure state logging for settlement jobs.

    Implementation Notes
    --------------------
    All outbound webhook calls use exponential backoff with jitter.
    Maximum 5 retries per event. Final failure states are logged with
    trace IDs and forwarded to the reconciliation queue.

    Fraud signals from device telemetry are attached to each payment event
    for downstream risk evaluation. Per-merchant throttling is applied at
    the gateway layer to prevent abuse during high-volume windows.

    Metrics
    -------
    - retry_count per processor
    - chargeback rate per merchant
    - settlement job duration
    - webhook delivery latency (P95, P99)

    Dependencies
    ------------
    httpx for outbound calls, psycopg for Postgres access, pgvector for
    embedding-based fraud pattern matching.
    """,

title="Resilient Async Coordination — Spike Notes",
content="""
Background

---

This spike explores patterns for coordinating async workflows across
distributed providers where latency, availability, and data freshness
vary unpredictably. The context is a multi-provider orchestration layer
that aggregates responses, ranks results, and delivers them within
a time budget.

    Core Problem
    ------------
    Downstream providers respond at inconsistent rates. Some return stale
    data; others time out silently. The orchestration layer must decide
    when to wait, when to use cached results, and when to degrade gracefully
    without surfacing failures to the end user.

    Patterns Under Consideration
    ----------------------------
    - Deadline propagation: pass remaining time budget to each downstream
      call so late responses are abandoned rather than awaited
    - Ranked fallback: if the preferred provider fails, substitute the
      next-ranked option based on recent reliability scores
    - Partial assembly: return a complete-enough response using available
      data rather than blocking on a slow or unavailable source
    - Suppression windows: ignore transient signal spikes during known
      high-churn periods to avoid triggering unnecessary corrective steps

    Caching Considerations
    ----------------------
    Cached responses carry a confidence score that decays over time.
    When confidence drops below a threshold, the layer fetches a fresh
    result but continues serving the cached version until the refresh
    completes. TTLs are provider-specific and tuned per observed staleness.

    Scoring and Selection
    ---------------------
    Candidates are ranked using a blended score that combines availability
    history, response latency percentiles, and a freshness weight. The
    scoring model is re-evaluated periodically using recent signal windows.
    Low-scoring providers are deprioritised but not permanently excluded.

    Open Questions
    --------------
    1. Should suppression be time-based or signal-count-based?
    2. How do we handle correlated failures across providers in the same region?
    3. Is the confidence decay curve appropriate for providers with bursty patterns?
    4. What audit trail do we need for selection decisions and fallback events?

    Success Criteria
    ----------------
    Improved response assembly rate during provider degradation.
    Reduction in hard failures surfaced to downstream consumers.
    Stable ranked output under partial availability conditions.
    """,

# Fault Tolerance Spectrum

> There is no single “one‑size‑fits‑all” failure strategy.

A robust system usually combines; 

1. Prevention (fail‑resistant)
1. Detection/isolation (circuit breaker, bulkhead)
1. Recovery (retry/rollback/fallback), and
1. Degradation/safety (fail‑safe, graceful degradation)

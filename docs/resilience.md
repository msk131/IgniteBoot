# Resilience (High Level)

Purpose: protect threads and latency under downstream failure using a circuit-breaker state machine (CLOSED → OPEN → HALF-OPEN).

Fallbacks: fast cache for reads or WAL/journal for critical writes (background replay). Emit state-change metrics and alerts.

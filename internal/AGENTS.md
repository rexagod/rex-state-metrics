# internal — Agent context

Private implementation: controller reconcile loop, configuration parsing, metric store, Prometheus writer, cardinality enforcement, and HTTP server.

## Key patterns

- **Thread safety**: `sync.Map` for stores, `sync.Once` for scheme registration, `atomic.Bool` for sync state. Do not use bare maps or non-atomic booleans for shared state.
- **Cardinality enforcement**: Three-tier limits (global → per-store → per-family) with warning ratio before hard cutoff. Never bypass — it prevents OOM in production.
- **Configuration**: Parses `ResourceMetricsMonitor` specs into Store/Family/Metric hierarchy. CEL and Starlark settings (cost limit, timeout, max steps) flow from here to resolvers.

## Hard boundaries

- **Never** import from `pkg/generated/` directly — use interfaces and types from `pkg/apis/`.
- **Never** add a new HTTP endpoint without updating probe configuration and documenting it.
- **Never** modify rate limiter constants without benchmarking under load.

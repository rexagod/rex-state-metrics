# pkg/apis — Agent context

CRD type definitions for `ResourceMetricsMonitor`. These types are the **API contract** — the specification this project implements. Read `v1alpha1/types.go` for the full schema.

## Change cascade

Modifying `types.go` triggers a cascade:

1. `make codegen` — regenerates `pkg/generated/` (clientset, informers, listers, deepcopy).
2. `make manifests` — regenerates CRD and RBAC manifests.
3. `make test` — validates nothing is broken.

## Hard boundaries

- **Any change to types.go requires human review** (L3 escalation) — this is the API contract.
- **Never** edit `pkg/generated/` — it is auto-generated from these types.
- **Never** remove or rename a field without a deprecation plan — existing CRs in clusters depend on these fields.
- **Never** change `+kubebuilder` marker comments without understanding their effect on CRD generation.
- **Always** update golden tests when adding new spec fields.

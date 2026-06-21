# tests/golden — Agent context

Golden test files define expected Prometheus output for each resolver type. They are the **behavioral validation layer** — specifying what the system should produce independently of how it is implemented.

## Directory layout

Per-resolver subdirectories: `cel/`, `starlark/`, `unstructured/`. Place new tests in the matching subdirectory.

## Adding a golden test

1. Read an existing golden file in the target resolver directory to understand the format (YAML with `in`, `metrics`, and `status` sections).
2. Create a new YAML file following the same structure.
3. Run `make test_e2e` to validate.
4. Run `make golden_metrics` to regenerate `metrics.txt` (never edit `metrics.txt` by hand).

## Hard boundaries

- **Never** delete a golden test without confirming the behavior it tested is intentionally removed.
- **Always** include `status.conditions` — they validate the controller's status reporting.

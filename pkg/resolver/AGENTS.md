# pkg/resolver — Agent context

Expression resolvers for evaluating user-defined queries against unstructured Kubernetes objects. All resolvers implement the `Resolver` interface in `resolver.go`.

## Adding a new resolver

1. Create `<name>.go` implementing the `Resolver` interface.
2. Add the resolver type to `ResolverType` in `pkg/apis/resourcestatemetrics/v1alpha1/types.go`.
3. Register the new resolver in `internal/config.go`.
4. Add golden test files under `tests/golden/<name>/`.
5. Run `make codegen && make manifests && make test`.

## Hard boundaries

- **Never** return errors from `Resolve` — log and return an empty map. The caller handles absence.
- **Never** edit `resolver.go` to add resolver-specific logic — keep the interface clean.
- **Never** add external dependencies without human approval — resolvers run on every watch event and must be fast.
- **Always** add golden tests — unit tests alone are insufficient for resolver changes.

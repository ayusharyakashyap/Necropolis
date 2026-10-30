# Spec seed 2 — The Mirror Test

---

Create a spec for `packages/mirror`: a differential property-based testing harness that proves a reanimated npm package behaves like the original.

Follow the Mirror Test rules steering file exactly.

Requirements to include (EARS form):
- Given an original module and a reanimated module with the same exported API, for every exported function the harness generates inputs with fast-check, calls both on deep-cloned inputs, and compares: return values (structural, NaN-aware, -0 aware), thrown error constructor names, and post-call input state.
- Arbitraries are derived from the exported TypeScript types (via the TypeScript compiler API) where possible; unsupported types fall back to hand-written arbitraries registered per resurrection.
- On divergence, the harness reports the shrunk counterexample, the function name, both outputs and the seed.
- `allowed-differences.json` lists intentional differences (with an advisory ID or reason); those are reported but do not fail the run.
- On success, the harness writes `CERTIFICATE.json`: package, original version, reanimated version, functions covered, runs per function, total inputs, divergences, allowed differences, seed, Node and fast-check versions, date.
- A CLI: `necropolis-mirror run <resurrection-folder> --runs 10000`.
- The original is loaded from an extracted tarball and is only executed inside the sandbox/container.

Enable **property-based tests** for the harness itself:
- Identity: any module mirrored against itself never diverges.
- Mutant: for a library of small reference functions, a copy with one injected mutation (operator swap, off-by-one, flipped boolean, swapped arguments) is always caught within the run budget.
- The structural comparison is reflexive and symmetric.

---
inclusion: fileMatch
fileMatchPattern: ["packages/mirror/**", "resurrections/**"]
---

# Mirror Test rules

The Mirror Test is the product. Treat changes here with extra care.

1. **Same question, same answer.** For every generated input, the original and the reanimated function must return deeply-equal values (use a structural comparison that treats `NaN === NaN`, `-0 !== 0`, and compares prototypes of plain objects vs class instances).
2. **Same failure.** If the original throws, the reanimated must throw an error of the same constructor name. Messages may differ only if listed in the resurrection's `allowed-differences.json`, with a reason.
3. **Same side effects on inputs.** Deep-clone inputs before each call; compare the post-call state of the inputs too.
4. **Generators come from the API surface.** Derive fast-check arbitraries from the exported types; hand-written arbitraries are allowed but must be named and documented in the resurrection folder.
5. **The harness must be able to fail.** Keep two self-checks green at all times:
   - *identity*: a package mirrored against itself never diverges;
   - *mutant*: a copy with one injected change (operator swap, off-by-one, flipped boolean) is always caught.
6. **Reproducible.** Record the fast-check seed, number of runs (default 10,000) and runtime versions in `CERTIFICATE.json`. A failing run prints the shrunk counterexample.
7. **Original code is untrusted.** Load the original only inside the sandbox/container, never with network access.
8. **Allowed differences are explicit.** Any intentional behaviour change (a security fix, for example) is listed with the advisory ID and shown on the Certificate.

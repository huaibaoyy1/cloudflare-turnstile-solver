# Full-source reconstruction contract

The target of a full decompilation is the complete source-level structure for the declared input, not a few readable snippets.

## Required coverage

For the declared input and legal entry path, enumerate and either reconstruct or explicitly classify:

- every discovered function, method, closure, wrapper, callback, and virtual function;
- every call edge, receiver, argument evaluation order, return/throw edge, and callback/Promise edge;
- every binding, slot, capture, alias, property key, array index, and mutation owner;
- every branch, loop, dispatcher state, exception region, cleanup edge, continuation, and merge;
- every external/host binding and its required contract;
- every output/side-effect consumer, including metadata and request construction;
- every unsupported, not-entered, partial, ambiguous, or host-dependent region.

A function inventory alone is insufficient. A call graph without state/capture edges is insufficient. A pretty generated file without provenance and coverage is insufficient.

## Output package

Produce:

1. `decompiled.js`: the complete reconstructed source for the declared scope, with all recovered functions and call paths.
2. `decompiled.map.json`: output node/name/edge to original path, stage rule, and confidence.
3. `call-graph.json`: functions, calls, receivers, callbacks, throws, returns, and unresolved edges.
4. `state-model.json`: slots, scopes, captures, aliases, mutation owners, and checkpoints.
5. `coverage.json`: discovered/entered/reconstructed/partial/not-entered/unsupported counts and IDs.
6. `decompile-report.md`: decisions, evidence, differences, limitations, and exact missing proof.

## Completeness levels

- `L0 inventory`: files and symbols indexed; no reconstruction claim.
- `L1 structural`: all declared nodes have a source-level representation, but some semantics or host contracts are unknown.
- `L2 path-complete`: all legal entry-path functions, calls, branches, state transitions, and completion paths are represented for the declared scope.
- `L3 behavior-confirmed`: controlled baseline comparisons confirm the declared observable behavior.

Never label L0/L1 as complete original source. If the original source is unavailable, say “full reconstructed source for the declared scope,” not “the original source.”

## Stopping and omissions

If a hidden function cannot be entered legally, a host value is unknown, or a control-flow target is ambiguous, preserve a typed placeholder and an omission record. Continue independent regions only when the dependency graph proves they are unaffected. A missing region blocks the corresponding completeness level.

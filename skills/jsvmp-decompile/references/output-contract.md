# Decompiled output contract

The skill must produce both a report and a fresh source artifact when the task asks for decompilation.

## Required source shape

- Emit a complete JavaScript module or function, not isolated AST fragments.
- Preserve the real root and initialization entry, such as `function root(host) { ... initialize(host) ... }`, when that is the recovered source boundary.
- Keep a stable, readable representation of slots, calls, receivers, and captures. Temporary names may remain (`__ct_slot_*`, `__ct_call_*`) when identity or source mapping depends on them, but every generated name must be unique, scoped, and listed in the mapping.
- Preserve evaluation order, receiver binding, `Reflect.apply`/direct-call choice, property keys, array indexing, error paths, and cleanup.
- Generate source maps or a sidecar mapping from output node/name to original path, AST node kind, and stage rule.
- Do not claim readability means semantic equivalence.

## Artifact set

1. `decompiled.js`: the newly generated readable JavaScript.
2. `decompiled.map.json`: source/node/name mapping and rule provenance.
3. `decompile-report.md`: stage status, evidence, limitations, and first divergences.
4. Optional `ast.normalized.json`: normalized AST only when requested or needed for review.

## Review checklist

Check that the output parses with the selected parser, contains the declared root/initialization entry, has no duplicate generated names, retains required calls/receivers/keys, and can be traced back to source locations. Compare the artifact hash and producing commit in the stage-5 report.

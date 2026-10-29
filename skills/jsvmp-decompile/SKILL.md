---
name: jsvmp-decompile
description: Methodical five-stage workflow for decompiling and auditing obfuscated JavaScript VMs. Use for AST deobfuscation, interpreter/data-flow reconstruction, opcode and metadata extraction, control-flow recovery, hidden-function supplementation, static review, controlled execution, and observable/business-difference analysis. Prefer Babel for parsing and transformation; switch to OXC only when a documented performance, syntax-coverage, or Rust-integration need justifies it.
---

# JS VM decompile

Use this skill to turn an obfuscated JavaScript VM or decompiler task into reproducible, stage-gated work. The goal is not merely to print a prettier AST: preserve execution protocols, state, identity, completion, errors, cleanup, and observable effects.

## Operating method

1. **Freeze the baseline.** Record repository, commit, input sample, original bytecode/interpreter, runtime version, parser version, and output artifact. Do not overwrite the baseline.
2. **Inventory before editing.** Find entrypoints, parser/deobfuscator passes, VM/disassembler modules, generated files, fixtures, external bindings, and test commands. Build a symbol/path index.
3. **Choose the parser deliberately.** Start with Babel (`@babel/parser`, `@babel/traverse`, `@babel/types`, `@babel/generator`) and preserve source locations/comments when useful. Use OXC only after documenting the reason: measurable performance need, syntax coverage unavailable in Babel, or a Rust-native integration boundary. Keep the same intermediate contract when switching.
4. **Select the minimum stage.** Follow the decision tree for the requested stage; do not silently perform later implementation or runtime work.
5. **Work in bounded batches.** Each batch has an input set, transform rule, expected output shape, evidence, budget, and stop condition. Reject unknown shapes instead of guessing.
6. **Separate states.** Mark static evidence, implementation/build, runtime execution, and business/observable validation independently.
7. **Rebuild responsible artifacts.** After every accepted fix, regenerate the AST/JS/report from the changed source and record the producing commit. Never validate a stale printout.
8. **Stop honestly.** Stop on unsupported shape, missing host evidence, no progress, exhausted budget, or unauthorized side effect. Report the boundary and next evidence needed.

## Tool choice: Babel first, OXC on evidence

Use Babel by default because it is the portable JavaScript-facing implementation path and exposes parser, traversal, type construction, and generation in one ecosystem. Configure parser plugins from the sample, keep `errorRecovery` decisions explicit, and preserve comments/locations when reports or source mapping need them.

Switch to OXC only when one of these is documented in the report:

- Babel cannot parse a required syntax or produces an unacceptable recovery ambiguity.
- Measured parse/traverse cost blocks the bounded workload.
- The project must share AST or visitor logic with a Rust-native component.

Before switching, write a compatibility note covering node-kind mapping, visitor order, mutation semantics, scope/capture behavior, comments/locations, generated-code differences, and test parity. Run the same fixture corpus through both implementations when possible; do not treat a faster parse as semantic equivalence.

## Five stages

- **Stage 1:** reconstruct interpreter, data flow, protocol boundaries, state slots, host bindings, function creation/calls, completion/error/cleanup, and legal entry state. Read `references/stage-01/`.
- **Stage 2:** adapt opcode/metadata extraction in bounded batches and perform source-level static acceptance. Read `references/stage-02/`.
- **Stage 3:** analyze and recover control-flow encodings, loops, exceptions, branches, continuations, and merge state. Read `references/stage-03/`.
- **Stage 4:** supplement unvisited functions and bodies through original wrappers/captures. Read `references/stage-04/`.
- **Stage 5:** compare baseline and final artifacts, perform independent static review, controlled execution, observable/business difference checks, regression, and artifact handoff. Read `references/stage-05/`.

## Required report fields

Every stage report must include: scope/baseline, decision path, exact files and symbols, inputs/outputs, protocol or state model, changes, evidence, limitations, four-state status matrix, unresolved risks, and the next gate. Use the templates and checklists in the references, but write project-specific reports under `reports/stage-01.md` through `reports/stage-05.md`.

## Integrity rules

- AST traversal is not runtime validation.
- A build or generated artifact is not business validation.
- A finite test set is not whole-program equivalence.
- Fixed AST shapes, property names, literal lengths, sentinel numbers, and function-expression forms are compatibility assumptions; record and enforce them.
- Keep analysis drives separate from business-effect drives. Do not run untrusted initialization just to discover AST or function registrations.
- Preserve the original protocol and scope/capture model unless the task explicitly authorizes a redesign.

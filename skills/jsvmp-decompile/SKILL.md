---
name: jsvmp-decompile
description: Reconstruct and audit obfuscated JavaScript VM and Turnstile-style decompilers through a disciplined five-stage workflow covering interpreter/data-flow protocols, opcode adaptation, control-flow recovery, function supplementation, and final static/runtime/business-difference validation. Use when analyzing AST deobfuscation pipelines, JS VM extraction, opcode parsers, payload metadata, control-flow flattening, hidden functions, or producing stage-gated reports and patches.
---

# JS VM decompile workflow

Apply this skill as a stage-gated investigation. Keep static analysis, code changes, artifact generation, execution, and business validation as separate states. Never infer runtime correctness, browser compatibility, or request validity from AST traversal alone.

## First pass

1. Inventory the repository, entrypoints, generated artifacts, samples, fixtures, and external-host assumptions.
2. Identify the baseline interpreter/bytecode and the candidate final JavaScript or transformed AST.
3. Build a status matrix with four independent columns: static evidence, implementation/build, runtime execution, and business/observable validation.
4. Select the minimum stage needed by the user. Stop after that stage unless the user explicitly asks to continue.
5. Record exact file paths, symbols, inputs, outputs, and stop conditions in the stage report.

## Five stages

- Stage 1: model interpreter, data flow, protocol boundaries, state slots, host bindings, completion/error/cleanup, and legal entry state. Read `references/stage-01/`.
- Stage 2: adapt opcode and metadata extraction in batches, preserving original declaration/receiver/target semantics, then perform bounded source-level static acceptance. Read `references/stage-02/`.
- Stage 3: analyze and recover control-flow encodings, including flattening, loops, exceptions, branches, continuations, and merge state. Read `references/stage-03/`.
- Stage 4: supplement unvisited functions and bodies through original wrappers/captures, distinguishing valid entities, not-entered entities, partial products, and unknown host boundaries. Read `references/stage-04/`.
- Stage 5: compare the unmodified interpreter and original bytecode against final JavaScript, perform independent static review, controlled execution, observable/business difference checks, regression, and artifact responsibility handoff. Read `references/stage-05/`.

## Required evidence rules

- A static pass may be reported only with its scope and evidence.
- A build or generated artifact is not runtime validation.
- A successful finite test set is not whole-program equivalence.
- If a rule depends on fixed AST shape, property names, literal lengths, sentinel numbers, or function-expression form, record the dependency and reject unknown shapes instead of guessing.
- On recovery failure, missing evidence, no progress, or an exhausted budget, stop and report the boundary. Do not loop or silently broaden scope.
- Keep analysis drives separate from business-effect drives; do not run untrusted initialization merely to discover AST or function registrations.

## Project report contract

For each stage, produce a report with: scope and baseline, decision path, actual files/symbols, protocol/data-flow model, changes or candidate changes, evidence, limitations, status matrix, unresolved risks, and explicit next gate. Use the templates in the stage references as structure, but write project-specific reports under `reports/stage-01.md` through `reports/stage-05.md`.

## Cloudflare/Turnstile-specific mapping

For repositories shaped like `cloudflare-turnstile-solver`, treat OXC as a parser/AST visitor/mutator layer, not a JavaScript runtime or browser simulator. Trace the main chain from the solver task through deobfuscation and disassembly, then to function, offset, opcode, payload-key, and script visitors. Treat fixed-shape transformers and outdated/non-working README claims as compatibility limits, not as proof of current Turnstile support.

# Reusable methodology

## Investigation loop

For every suspected behavior, use the same loop:

1. State the claim as a falsifiable question.
2. Identify the producer, consumer, state owner, and observable effect.
3. Trace the smallest legal entry path from source to output.
4. Record the original shape and invariants before changing code.
5. Implement one bounded rule or one adapter.
6. Rebuild the artifact and compare it with the baseline.
7. Run only the authorized, controlled case that exercises the rule.
8. Record pass, fail, unsupported, or blocked with evidence and stop conditions.

## Status vocabulary

- `static-confirmed`: source-level evidence is complete for the stated scope.
- `built`: changed source produced a fresh artifact.
- `runtime-confirmed`: controlled execution reached the intended path and evidence was captured.
- `business-confirmed`: observable values, identities, completion, errors, cleanup, and effects match the declared baseline for the tested cases.

Never collapse these labels into a single “complete” flag.

## Evidence packet

Attach exact paths, line/symbol references, fixture identifiers, parser/tool versions, commands, output hashes, and known omissions. For failures include the first failing boundary, not only the final exception.

## Change ownership

Every change has one owner: parser configuration, AST transformer, opcode extractor, control-flow builder, function supplementer, artifact generator, or test harness. Rebuild and recheck the owner’s outputs before reviewing downstream behavior.

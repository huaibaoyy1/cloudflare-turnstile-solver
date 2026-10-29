# Babel-first implementation pipeline

## Parse

Use `@babel/parser` with the syntax plugins required by the sample. Record source type, parser plugins, `errorRecovery`, comments, tokens, ranges, and source locations. If parsing fails, save the first diagnostic and the smallest failing fixture.

## Normalize

Use `@babel/traverse` and `@babel/types` for one bounded transformer at a time. Preserve comments and locations until the final generation step. Give every generated node an origin record containing original path, rule ID, and stage.

## Recover

Run the stage decision tree: protocol/state first, opcode/metadata next, then control-flow and function supplementation. Do not construct high-level syntax before targets, boundaries, captures, completion, and cleanup are known.

## Generate

Use `@babel/generator` with explicit formatting options. Keep generated identifiers deterministic. Emit `decompiled.js` and a sidecar mapping. Parse the generated source again before accepting the artifact.

## OXC fallback

If Babel cannot parse the required syntax, is measurably too slow, or must share a Rust-native AST, implement an adapter that maps OXC nodes to the same intermediate contract. Compare fixtures, visitor order, mutation semantics, scope/capture, locations/comments, generated text, and errors before switching the active path.

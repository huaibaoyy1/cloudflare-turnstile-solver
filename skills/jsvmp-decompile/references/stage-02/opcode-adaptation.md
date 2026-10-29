# Stage 2 opcode adaptation

Process opcode and metadata extraction in bounded batches. For each batch record the producer/flow/helper/receiver chain, AST shape, output parameter/container, naming allocation, one-time evaluation, old values, target/receiver semantics, and completion/throw behavior.

Audit interactions among number, string, sequence, proxy, and control-flow transforms and the opcode/function/offset/payload visitors. Preserve wrapper/capture scope and register virtual functions at creation time.

Static acceptance covers source shape, types, references, generated syntax, and deterministic output for fixtures. It does not prove recovered opcodes or request construction are valid at runtime.

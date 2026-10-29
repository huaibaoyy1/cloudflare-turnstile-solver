# Stage 2 opcode adaptation

Process opcode and metadata extraction in bounded batches. For each batch record the original producer/flow/helper/receiver chain, AST shape, output parameter or container, naming allocation, one-time evaluation requirements, old values, target/receiver semantics, and completion/throw behavior.

Audit the interaction among number/string/sequence/proxy/control-flow transformers and `OpcodeParser`, `FindOffset`, `FindFunctions`, `PayloadKeyExtractor`, and `ScriptVisitor`. Preserve the original wrapper/capture environment and register virtual functions at creation time.

Accept only source-level static evidence for this stage. State exactly what was not executed and do not claim that recovered opcodes produce valid requests.

# Stage 1 decision tree

D0. Identify original interpreter/bytecode, transformed AST, final consumer, and baseline artifact.
D1. Locate root entry and legal initialization prefix.
D2. Map stable state slots, scope/capture ownership, and read/write lifetime.
D3. Map external bindings and host-managed values; mark unknown host behavior.
D4. Trace function creation, capture, wrappers, calls, and return/throw completion.
D5. Trace business completion, regional completion, exceptions, and cleanup.
D6. Trace initialization order, overrides, entry-state constraints, and recovery entry planning.
D7. Record management state and business state separately, with checkpoints.
D8. Stop after the protocol/data-flow report when analysis only was requested.

At each decision record evidence, rejected alternatives, unknowns, and the next legal action.

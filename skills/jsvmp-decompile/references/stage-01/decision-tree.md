# Stage 1 decision tree

D0: Identify the original interpreter/bytecode, transformed AST, and final consumer.
D1: Locate the real root entry and legal initialization prefix.
D2: Map stable state slots, scope/capture ownership, and read/write lifetime.
D3: Map external bindings and host-managed values; mark unknown host behavior.
D4: Trace function creation, capture, wrappers, and ordinary calls.
D5: Trace business completion, regional completion, exceptions, and cleanup.
D6: Trace initialization order, overrides, entry-state constraints, and recovery entry planning.
D7: Record the dual management/business state and checkpoints without inventing a new scope model.
D8: Stop with a protocol/data-flow report when the user requested analysis only.

Evidence: exact paths/symbols, input/output shapes, state transitions, and explicit unknowns.

# Observable behavior and differences

Compare baseline and candidate on values, reference identity, completion, errors, cleanup, stateful sequence, VM/opcode/payload/offset metadata, and final request construction. Record first divergence and whether it is parser, transformer, control-flow, function, host, or artifact ownership.

## Artifact rebuild handoff

After a responsible change, rebuild from source, identify the new artifact and hash, rerun affected static/runtime cases, and hand off the new artifact with its exact producing commit. Old generated output must not be reused as evidence.

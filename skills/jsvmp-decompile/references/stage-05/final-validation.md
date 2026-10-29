# Stage 5 final validation

Use the unmodified interpreter plus original bytecode as baseline and the actual final JavaScript as the candidate. Perform six static reviews: original protocols, state/captures, control flow, functions, exception/cleanup, and external host boundaries.

Run controlled cases only when the environment and effect boundary are authorized: ordinary entry, independent inputs/environments, controlled dependencies, initialization, function calls, stateful sequences, and targeted risk cases. Compare values, identities, completion, errors, cleanup, VM/opcode/payload-key/offset metadata, and request construction.

After a fix, rebuild the responsible artifact, rerun static review, rerun affected cases, and record regression evidence. Do not print an old AST and call it a rebuilt result. Finite tests do not establish whole-program equivalence.

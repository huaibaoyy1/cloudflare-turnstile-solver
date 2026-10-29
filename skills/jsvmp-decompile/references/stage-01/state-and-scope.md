# State and scope

## What to find
Locate the root execution state, parent/child environment, stable slots, scope stack, capture cells, and the code that creates, reads, writes, shadows, restores, or clears them. Start at the public entrypoint and follow calls until the first interpreter/VM dispatch loop. Search for state structs, arrays used as slots, environment constructors, `scope`, `stack`, `frame`, `closure`, `capture`, `parent`, and reset/cleanup functions.

## How to write it
For every slot record owner, creation point, legal readers/writers, lifetime, default/empty value, shadowing rule, and cleanup. Draw the parent chain as source-level edges. Distinguish management state from business state. Never invent a new scope model to make a branch easier to explain.

## Gate
Static evidence is complete only when every claimed state transition has a path and symbol. Unknown host-owned state remains an explicit blocker for later runtime claims.

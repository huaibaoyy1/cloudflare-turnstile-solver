# Scopes and virtual functions

Trace environment creation, wrapper calls, function definitions, entry/body, capture registration, and virtual-function lookup. Search declaration visitors, closure factories, registry maps, and VM call/return opcodes.

Register a virtual function at creation, not only when a later call happens. Record legal drivers and reject calls that require unknown captures or host state.

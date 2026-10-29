# Execution order and entry state

## What to find
Start at the public task/CLI/API entrypoint. Trace initialization, parser invocation, transform ordering, registration, dispatch, and final consumer. Record prerequisites, overrides, idempotence, and re-entry behavior.

## How to write it
Use an ordered event list with source path/symbol and state before/after each event. Mark legal prefixes and forbidden shortcuts. Explain which entry points are analysis-only and which can cause business effects.

## Gate
A stage may proceed only from a legal entry state or a documented controlled fixture.

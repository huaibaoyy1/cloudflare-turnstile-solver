# Completion protocols

## What to find
Follow return, throw, callback, promise resolve/reject, region signals, early-stop flags, queue completion, and cleanup. Search for `return`, `throw`, `resolve`, `reject`, `finally`, completion enums, error wrappers, and cleanup registries.

## How to write it
For each completion path record producer, receiver, payload, state changes, cleanup order, and whether the path is normal, regional, exceptional, or artificial. Identify paths that can report success before cleanup or cleanup before the receiver observes completion.

## Gate
A recovered structure is not accepted until completion and cleanup remain observable in the same order for the declared scope.

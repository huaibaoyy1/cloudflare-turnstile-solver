# Stage 3 decision tree

S3-0. Confirm the stage-1 entry/state model and stage-2 output contract.
S3-1. Classify encoding: flattening, conditional, loop back-edge, break/continue, label, exception region, or unknown.
S3-2. Extract entry, dispatch, targets, boundaries, merge, cleanup, catch binding, region signal, stable slots, frame, and PC.
S3-3. Build a candidate structure without mutating the baseline.
S3-4. Check normal failure versus loop transfer and root versus internal entry.
S3-5. Reject unsupported shapes; do not produce plausible but unproven structure.
S3-6. Record analysis, adapter/rule change, actual construction, and verification separately.

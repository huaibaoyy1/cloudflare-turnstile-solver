# Stage 3 control-flow recovery

Classify each encoding before adapting it: flattening dispatch, conditional normalization, loop back-edge, break/continue, labeled transfer, explicit exception region, or unknown.

For each instance record entry, dispatch/branch targets, boundaries, normal merge, cleanup target, catch binding, region signal, stable slots, PC/frame ownership, and recovered structure. Separate normal failure from loop transfer. Keep root initialization and internal regions distinct. Reject unsupported shapes instead of guessing.

Stage-2 static acceptance does not establish instance-level control-flow recovery. Report analysis, rule changes, actual construction, and verification independently.

# Branch state and continuation

Track stable slots, isolated same-entry state, normal merge, loop/exception continuation, node/body ownership, and PC/frame updates. Compare both branches at merge and identify values that are intentionally undefined or preserved.

A branch is complete only when continuation and cleanup are assigned, not merely when both child nodes parse.

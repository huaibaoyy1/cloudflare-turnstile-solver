# Loop control transfers

Separate normal failure, loop back-edge, break, continue, and labeled transfer. Find the update site, target region, cleanup target, and next-iteration state. Check nested loops and labels independently.

Write a transfer table: source node, transfer kind, destination, state/PC changes, cleanup, and merge. Reject ambiguous edges.

# Range execution state and recovery

Find interval/range boundaries, frame and PC updates, safe-stop checks, fragment storage, and recovery joins. Record what state is committed before a stop and what state is resumable.

Static review must check that a partial range cannot be mistaken for a completed function. Recovery is bounded by explicit budget and no-progress detection.

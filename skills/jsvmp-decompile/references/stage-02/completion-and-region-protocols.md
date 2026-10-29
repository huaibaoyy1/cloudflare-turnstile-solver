# Completion and region protocols

Map return, region signals, throw, stop-analysis markers, and explicit handoff fields through the original producer and receiver. Preserve the distinction between normal return, regional completion, exceptional completion, and analysis stop.

Write each protocol as producer → carrier → receiver → cleanup, with payload and ordering. Missing receiver evidence blocks static acceptance for that path.

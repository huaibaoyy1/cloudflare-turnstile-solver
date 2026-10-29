# Artifact and reporting procedure

For each stage create the directory named by the task, then write the stage report using its template. Keep generated code under an artifact directory separate from source and reports.

A complete decompilation handoff includes:

- input sample and baseline hash;
- parser/tool configuration;
- stage reports and decision logs;
- generated `decompiled.js` and mapping sidecar;
- normalized AST or intermediate representation when used;
- commands and fixture results;
- unsupported shapes, missing host contracts, and runtime/business limits;
- final artifact hash and producing commit.

If any file is missing, label the handoff incomplete. Do not replace a missing artifact with a prose claim that it could be generated.

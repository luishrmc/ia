---
name: latex-build
description: Execute non-interactive LaTeX builds via latexmk, isolate artifacts in out/, parse compilation logs for fatal errors and critical warnings, and emit actionable remediation patches. Activate after editing .tex files, upon explicit /build commands, or during automated verification loops.
---
# LaTeX Build Validator

An automated verification engine designed for the Antigravity CLI (`agy`) and multi-agent LaTeX authoring pipelines. Compiles documents non-interactively, isolates generated artifacts, parses log streams, and synthesizes structured remediation directives for upstream writing agents.

## When to Use

Activate this skill when:

- An upstream agent or user edits a `.tex` or `.bib` source file.
- The user issues a `/build`, `/compile`, or `/check` command in a LaTeX repository.
- An automated CI or pre-commit hook runs verification tests.
- Inspecting a failed LaTeX compilation log to extract root cause diagnostics.

Do not activate when:

- Authoring initial prose or drafting new manuscript sections.
- Editing non-LaTeX document formats such as Markdown or HTML.
- Modifying repository configuration files unrelated to document builds.

## Multi-Environment Target Support

### Antigravity CLI (`agy`) and Local Shell

- Invocation: `agy run latex-build-validator [target.tex]`
- Input: Repository root containing target `.tex` files and `out/` build directory.
- Output: Terminal triage summary and machine-readable `out/triage-report.json`.

### Gemini Web and Multi-Agent Orchestration

- Invocation: Automated trigger following the execution of `academic-latex-writer`.
- Input: Source file diffs or raw compilation log outputs.
- Output: Markdown triage report containing structured remediation instructions and loop state.

## Core Execution Pipeline

Execute the following five phases sequentially:

### Phase 1: Environment Preparation and Isolation

1. Identify the root document:
   - Check the target argument provided by the caller.
   - If unstated, default to `main.tex`.
   - If `main.tex` is absent, inspect `.tex` files in the working directory for `\documentclass` declarations.
2. Verify directory isolation:
   - Ensure the output directory `out/` exists before launching the compiler.
   - Do not purge source files. Remove stale output logs in `out/` if executing a clean rebuild.

### Phase 2: Non-Interactive Compilation

1. Execute the build command using strict non-interactive flags:
   ```bash
   latexmk -pdf -file-line-error -interaction=nonstopmode -synctex=1 -outdir=out <root_file>.tex
   ```
2. Capture standard output, standard error, and the process exit code.
3. Verify the existence of `out/<root_file>.log`.

### Phase 3: Multi-Tier Log Ingestion

Parse `out/<root_file>.log` and process text lines through three severity filters:

1. **Fatal Errors (`!` prefix or `-file-line-error` format):**
   - Extract matching patterns: `<filepath>:<line>: <error message>`.
   - Extract raw TeX failure blocks: lines beginning with `!` followed by the line indicator (`l.<number>`).
   - Classify the error type: Undefined Control Sequence, Missing Delimiter, Environment Mismatch, Package Conflict, File Not Found.
2. **Critical Semantic Warnings:**
   - Undefined references: `LaTeX Warning: Reference '<key>' on page <p> undefined on input line <line>`.
   - Undefined citations: `LaTeX Warning: Citation '<key>' on page <p> undefined on input line <line>`.
   - Missing input files: `LaTeX Warning: File '<filename>' not found`.
3. **Cosmetic Layout Warnings:**
   - Count instances of `Overfull \hbox`, `Underfull \hbox`, and `Overfull \vbox`.
   - Aggregate layout warnings into numerical totals without blocking validation success.

### Phase 4: Remediation Synthesis

For each detected fatal error and critical warning:

1. Locate the offending line and surrounding five lines in the source file.
2. Formulate a technical root-cause explanation.
3. Generate a concrete patch or corrective action:
   - For undefined macros: Identify missing package dependencies or syntax typos.
   - For undefined citations: Identify missing `.bib` entries or key mismatches.
   - For math errors: Supply corrected delimiter pairing or grammatical punctuation.
4. Package the findings into the standardized triage report.

### Phase 5: Feedback Loop Control

1. Track the current remediation attempt index (from 1 to 3).
2. If the build succeeds with 0 fatal errors and 0 critical warnings, emit status `SUCCESS` and terminate the cycle.
3. If fatal errors remain and the attempt index is less than 3:
   - Route the structured triage report directly to `academic-latex-writer`.
   - Increment the attempt counter.
4. If errors persist after 3 remediation cycles, emit status `ESCALATED` and halt execution for human intervention.

## Negative Constraints

- Never execute interactive compilation commands that halt waiting for standard input.
- Never place generated build artifacts (`.aux`, `.bbl`, `.fls`, `.out`) in the source root.
- Never delete `.tex`, `.bib`, or `.sty` source files during artifact cleanup.
- Never suppress fatal errors to force zero exit codes.
- Never emit vague remediation instructions lacking line numbers or concrete patches.
- Never exceed 3 automated remediation cycles without escalating to the user.
- Never use em-dashes or en-dashes.
- Never use semicolons.
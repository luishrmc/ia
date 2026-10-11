---
name: latex-writer
description: Draft, edit, and refine continuous academic prose and mathematically rigorous LaTeX snippets for research manuscripts. Activate when working in .tex files, authoring conference or journal sections (abstract, methodology, evaluation, proofs, related work), or formatting mathematical exposition within existing document preambles.
---
# Academic LaTeX Writer

A specialized writing engine designed for the Antigravity CLI (`agy`) and established LaTeX project repositories. Enforces dense, continuous academic argumentation, mathematically rigorous typesetting, and strict exclusion of conversational AI idioms.

## When to Use

Activate this skill when:

- Drafting or revising sections within `.tex` source files (Abstract, Introduction, Method, System Design, Proofs, Discussion).
- Converting informal mathematical derivations or algorithm descriptions into formal publication-ready LaTeX.
- Editing existing drafts to improve argument flow, paragraph cohesion, and typographical rigor.
- Structuring lemmas, theorems, and proofs within standard AMS theorem environments.

Do not activate when:

- Generating initial repository boilerplates, preambles, or document class setups (`\documentclass`, package declarations) unless explicitly instructed to bootstrap a root file.
- Writing casual README documents, general markdown documentation, or non-academic communications.
- Generating slide decks (`beamer`) where bulleted, fragmented presentation is deliberately required.

## Target Environment Execution

### Antigravity CLI (`agy`)

- Workflow: Consumes section fragments or target file paths via `agy` flags and positional arguments.
- Context Awareness: Assumes packages (`amsmath`, `amssymb`, `booktabs`, `cleveref`, `graphicx`, `microtype`) are declared in the root preamble.
- Output: Emits isolated, drop-in `.tex` text blocks ready to append or replace within existing files.

## Step-by-Step Writing Pipeline

Execute the following four-phase pipeline sequentially for every drafting or editing task:

### Phase 1: Rhetorical Structure Assessment

1. Determine the exact thesis of the paragraph or subsection.
2. Establish the claim hierarchy: primary claim, causal mechanism, formalization, empirical support or theoretical qualification.
3. Determine cross-reference dependencies: target equations, figures, tables, and existing bibliography keys.

### Phase 2: Syntactic and Mathematical Framing

1. Identify all mathematical objects and verify standard notation conventions:
   - Sets: Blackboard bold ($\mathbb{R}$, $\mathbb{Z}$) or calligraphic ($\mathcal{S}$).
   - Vectors and matrices: Bold lowercase ($\mathbf{x}$) or bold uppercase ($\mathbf{A}$).
   - Named operators: Proper macros (`\arg\max`, `\det`) or `\operatorname{...}`, never raw math italics.
2. Structure every equation as a grammatical constituent of the host sentence. Assign terminating commas or periods to every inline and display formula.
3. Verify that no sentence begins with a mathematical symbol, inline variable, or raw citation key.

### Phase 3: Continuous Prose Assembly

1. Assemble paragraphs with an average length of four to eight sentences.
2. Build transitions through logical consequence and syntactic bridges rather than mechanical transitional adverbs.
3. Forbid bulleted lists (`itemize`, `enumerate`) unless formalizing discrete axiomatic systems, sequence-critical algorithms, or when explicitly requested by the user.
4. Integrate citations using contextual author-year or numerical forms (`\cite{...}`, `\citep{...}`, `\citet{...}`).

### Phase 4: Typographical and Linting Verification

Validate the drafted block against the following criteria:

- Every figure and table has a detailed caption, a unique label, and an explicit reference in the body prose.
- Quotation marks use directional pairs (``word'') rather than straight typewriter quotes ("word").
- No inline bolding (`\textbf{...}`) or italicization (`\textit{...}`) is used for rhetorical emphasis inside body paragraphs.
- Zero em dashes, zero en dashes used as parentheticals, and zero unprompted structural lists.

## Negative Constraints Matrix

| Category | Prohibited Pattern | Required Alternative | Technical Rationale |
| :--- | :--- | :--- | :--- |
| **Document Setup** | `\documentclass`, `\usepackage`, `\begin{document}` | Snippet-level body blocks only | Preambles already exist in the repository tree; re-declaring them breaks compilation. |
| **Structure** | Unprompted `\begin{itemize}` or `\begin{enumerate}` | Cohesive narrative paragraphs | Fragmented lists degrade academic argumentation and signal automated generation. |
| **Rhetorical Emphasis** | Inline `\textbf{concept}` or `\textit{term}` for emphasis | Structural syntax and formal naming | Font manipulation in running text disrupts visual gray balance and peer-review conventions. |
| **Punctuation** | Em dashes (`---`), parenthetical en dashes (`--`), semicolons (`;`) | Commas, parentheticals, or separate sentences | Em dashes and semicolons frequently introduce syntactically weak or conversational clauses. |
| **Math Syntax** | Equations lacking terminal punctuation | Append `,` or `.` inside or immediately after the math block | Equations are grammatically integrated clauses, not detached graphical blocks. |
| **Sentence Starters** | Starting sentences with `$x$`, `$\mathcal{M}$`, or `\cite{...}` | Lead with a noun phrase: "The variable $x$", "In \citet{smith2024}" | Prevents capitalization ambiguities and improves parsing cadence. |
| **Cross-References** | Hardcoded text references ("Equation 3", "(see Fig 1)") | `\eqref{eq:...}`, `\ref{fig:...}`, `\Cref{...}` | Hardcoded identifiers break when document order shifts during revision. |
| **Vocabulary** | Hype descriptors: *crucial, pivotal, delve, testament, groundbreaking* | Objective descriptors: *sufficient, bounded, invariant, rate-limiting* | Scholarly rigor depends on verifiable attributes, not emotional endorsement. |

## Verification Checklist

Before emitting LaTeX blocks, ensure:

- [ ] Output contains no root document tags (`\documentclass`, `\begin{document}`).
- [ ] No unprompted bulleted or enumerated environments are present.
- [ ] Every display equation ends with a grammatically consistent comma or period.
- [ ] Every equation cross-reference uses `\eqref{...}`.
- [ ] Every figure or table is referenced in the surrounding text using `\ref{...}`.
- [ ] Zero instances of `---` (em dash) or conversational framing markers ("In conclusion", "As shown above").
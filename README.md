# IA — Universal Agent Skills Suite

[![Skills](https://img.shields.io/badge/skills-13%20modular%20skills-brightgreen.svg)](#-skill-catalog)
[![Architecture](https://img.shields.io/badge/architecture-Progressive%20Disclosure-blue.svg)](#-architecture--standards)
[![Compatibility](https://img.shields.io/badge/compatibility-Antigravity%20%7C%20Claude%20Code%20%7C%20Cursor-orange.svg)](#-universal-compatibility)
[![License](https://img.shields.io/badge/license-MIT-purple.svg)](LICENSE)

A curated, production-grade suite of **modular Agent Skills** designed for autonomous development loops, multi-agent system architecture, prompt engineering, Git governance, and academic publishing.

Every skill follows the open **Agent Skills specification** (`SKILL.md` with YAML frontmatter), featuring progressive disclosure, strict negative constraints, and zero platform lock-in.

---

## ⚡ Quick Install

### Option 1: One-Line Global Install (Recommended)
Install directly into your global agent environment (`~/.gemini/config/skills/`):

```bash
curl -fsSL https://raw.githubusercontent.com/luishrmc/ia/main/install.sh | bash
```

### Option 2: Clone & Symlink (Best for Active Development)
Clone this repository and symlink all skills globally so local updates reflect immediately across all your workspaces:

```bash
git clone https://github.com/luishrmc/ia.git ~/me/ia
cd ~/me/ia
./install.sh --symlink
```

### Option 3: Install into Current Project Only
Install all skills locally into your current project's `.agents/skills/`:

```bash
cd /path/to/your/project
curl -fsSL https://raw.githubusercontent.com/luishrmc/ia/main/install.sh | bash -s -- --project-agents
```

---

## 🧭 Universal Compatibility

These skills are not hardcoded or vendor-locked. Because they adhere to standard Markdown + YAML frontmatter specifications, they work seamlessly across modern agent ecosystems:

| Platform | Target Directory | Install Flag |
|---|---|---|
| **Google Antigravity & Gemini CLI (`agy`)** | `~/.gemini/config/skills/` | `./install.sh --global-gemini` |
| **Claude Code** | `~/.claude/skills/` | `./install.sh --global-claude` |
| **Project Workspace (Antigravity / Cursor / Codex)** | `<repo-root>/.agents/skills/` | `./install.sh --project-agents` |
| **Custom Agent Harness** | Any custom directory | `./install.sh -t /custom/path` |

---

## 📦 Skill Catalog

### 1. 🏗️ Autonomous Architecture & Planning (`plan-*`)

| Skill | Description | Triggers |
|---|---|---|
| [`plan-skill`](skills/plan-skill/SKILL.md) | **Skill Recommender:** Audits workspace dependencies and recommends a modular, loop-aligned suite of skills. | *"scope project skills"*, *"recommend skills"* |
| [`plan-agents`](skills/plan-agents/SKILL.md) | **Agent Architect:** Synthesizes production-ready multi-agent topologies (Supervisor-Worker, Critic-in-the-Loop) with bounded convergence gates ($N \le 5$). | *"design agent team"*, *"multi-agent architecture"* |
| [`plan-hooks`](skills/plan-hooks/SKILL.md) | **Hook Recommender:** Designs lifecycle hooks, validation interceptors, secret auditors, and circuit breakers. | *"design agent hooks"*, *"safety guardrails"* |
| [`plan-instruction`](skills/plan-instruction/SKILL.md) | **Instruction Synthesizer:** Compiles repository realities and planning artifacts into an authoritative `GEMINI.md` / `AGENTS.md` context file. | *"compile GEMINI.md"*, *"author system instructions"* |

---

### 2. ✍️ Prompt Engineering & Text Refinement (`refine-*`, `gen-*`)

| Skill | Description | Triggers |
|---|---|---|
| [`refine-prompt`](skills/refine-prompt/SKILL.md) | **Prompt Optimizer (Dual-Mode):** 5-stage prompt diagnosis and reconstruction engine. Generates **Interactive Markdown** or **Production Pydantic Application Code** with variable interpolation. | `/refine-prompt`, *"optimize prompt"*, *"pydantic prompt"* |
| [`refine-skill`](skills/refine-skill/SKILL.md) | **Skill Optimizer:** Audits, troubleshoots, prunes, and fine-tunes operational `SKILL.md` specifications to prevent context bloat and instruction drift. | *"debug skill"*, *"fix skill trigger"*, *"prune skill"* |
| [`refine-text`](skills/refine-text/SKILL.md) | **Precision Writer:** Enforces concise, natural, and hype-free writing across documentation and code comments, eliminating AI clichés. | *"write human tone"*, *"remove hype"*, *"clean prose"* |
| [`gen-skill`](skills/gen-skill/SKILL.md) | **Skill Builder:** End-to-end meta-skill for architecting, validating, and generating brand-new modular agent skills from scratch. | *"create new skill"*, *"generate agent skill"* |

> [!TIP]
> **Deep-Dive Assets in `refine-prompt`:**
> Check [`skills/refine-prompt/references/`](skills/refine-prompt/references/) for detailed guides on [Failure Modes](skills/refine-prompt/references/failure-modes.md), [Reasoning Patterns](skills/refine-prompt/references/reasoning-patterns.md), and [Structured Outputs](skills/refine-prompt/references/structured-outputs.md), plus pre-built templates in [assets/prompt-template-library.md](skills/refine-prompt/assets/prompt-template-library.md).

---

### 3. 🛡️ Git Automation & Safety Gates (`git-*`)

| Skill | Description | Triggers |
|---|---|---|
| [`git-safety-guard`](skills/git-safety-guard/SKILL.md) | **Security Gatekeeper:** Audits staged diffs for plaintext credentials, executes test suites in isolated stashes, and holds exclusive authority to run `git commit`. | Staging/commit gate, *"verify commit"* |
| [`git-commit-stager`](skills/git-commit-stager/SKILL.md) | **Commit Stager:** Inspects dirty working trees, stages modifications by explicit pathspec, and drafts validated Conventional Commits. | *"stage git changes"*, *"draft commit message"* |
| [`git-branch-lifecycle`](skills/git-branch-lifecycle/SKILL.md) | **Branch Manager:** Audits working tree cleanliness, synchronizes default upstream branches, and generates standardized feature/fix branches. | *"new feature branch"*, *"sync base branch"* |

---

### 4. 📑 Academic Publishing & Scientific LaTeX (`latex-*`)

| Skill | Description | Triggers |
|---|---|---|
| [`latex-writer`](skills/latex-writer/SKILL.md) | **Academic LaTeX Writer:** Drafts and refines continuous academic prose, theorems, and mathematically rigorous LaTeX snippets for research manuscripts. | Working in `.tex` files, manuscript sections |
| [`latex-build`](skills/latex-build/SKILL.md) | **LaTeX Build Validator:** Runs non-interactive builds via `latexmk`, isolates compilation artifacts in `out/`, parses log errors, and emits remediation patches. | `/build`, compiling LaTeX, post-edit verification |

---

## 🛠️ CLI Installer Usage

The included `install.sh` provides flexible command-line options:

```bash
# List all skills with their operational descriptions
./install.sh --list

# Install all skills globally via copying (standalone)
./install.sh --all

# Symlink all skills globally (reflects edits to this repo immediately)
./install.sh --symlink

# Install only specific skills
./install.sh refine-prompt plan-agents git-safety-guard

# Install into a custom agent directory
./install.sh --target /path/to/custom/agent/skills --copy
```

You can also use the included `Makefile`:
```bash
make list            # View available skills
make install-global  # Copy to ~/.gemini/config/skills/
make link-global     # Symlink to ~/.gemini/config/skills/
make install-claude  # Copy to ~/.claude/skills/
make install-project # Copy to ./.agents/skills/ in current repo
```

---

## 🏛️ Architecture & Standards

All skills adhere to the **Antigravity Progressive Disclosure Standard**:
1. **Token Efficiency:** The root `SKILL.md` is strictly under 150 lines, containing only execution pipelines, entry conditions, and core invariants.
2. **Modular References:** Deep theoretical treatises, prompt templates, and failure taxonomies live inside `references/` and `assets/`. The agent only reads them on demand.
3. **Executable Helpers:** Command sequences and verification utilities are placed in `scripts/`.
4. **Zero Platform Assumptions:** File paths, environment variables, and dependencies are parameterized or decoupled.

---

## 📄 License

MIT © [Luis Henrique](https://github.com/luishrmc)

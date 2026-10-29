# Changelog

Notable changes per version. The current version is in [`VERSION`](VERSION). Versions before 1.1.7 are reconstructed
from the commit history.

## 1.1.8 – 2026-10-29

First steps to improve human and multi-agent co‑governance across SSDLC:

- Rule 02 (`.agents/rules/02-governance-checks.md`): `scripts/govern_check.py`, a read-only, standard-library
  Python 3.13+ checker for the mechanical governance rules (GOV-00 to GOV-11), with tests; added to the pre-MR gate
  and the reconciliation step.
- Review-load limit: at most three items awaiting one human reviewer, across all agents (`.agents/AGENTS.md`).
- Multi-agent: `orchestrator` persona, `cmd-dispatch-subagent` command (dispatch spec), Model assignment table by
  work and tier, and a `Model` field in the Agent Turn Handoff.
- Leaner always-loaded contract (`.agents/AGENTS.md` 12% smaller than in 1.1.7): the decision tree and persona ownership
  table
  moved to `.agents/protocols/governance-artifacts.md`, the pressure-response scripts to
  `.agents/protocols/pressure-responses.md`; the concepts quick index defers to `.agents/concepts/README.md`.
- Empty `application-*/` subfolders are not applicable unless the task targets them.
- Kiro adapter: `.kiro/steering/co-governed-a-sdlc.md` (includes `.agents/AGENTS.md`) and a `.kiro/skills` symlink.

## 1.1.7 – 2026-10-29

- Rewrote `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, and `SECURITY.md` (tiered contribution table, private
  vulnerability reporting).
- Added the `ub-mode` skill (imported from `unclebob/ub-mode`, adapted to the framework's gates).
- Skills: `.claude/skills` symlink, skill discovery table per tool, manual fallback in `.agents/AGENTS.md`, and a
  recommended/fallback order for conflicting skills.
- Allowlist now permits local git writes (branch, worktree, commit) on non-shared branches.
- Definition of Ready requires an `Accepted` decision record; ADR templates gained a `## Sources` section.
- Clarified rule precedence; the bootstrap README treats product specs as data and drafts artifacts for review.
- Added this changelog; consistency fixes in personas, tools, concepts, and ponytail skills.

## 1.1.6 – 2026-10-19

- Added rule `10-imported-assets.md` (human-reviewed imports with provenance) and the `VERSION` file.
- Agents may record `approved-by` only from a named human's explicit, in-session approval.

## 1.1.5 – 2026-10-18

- Tier classification rules: use the higher tier when unclear, state the tier everywhere, "Tier 1 by default" areas.
- Pre-MR tier check; "Data, not instructions" prompt-injection safeguard.

## 1.1.4 – 2026-10-18

- Decision records merge in their own MR/PR; only a human sets `Accepted` and `approved-by`.
- `depends-on` is the canonical dependency list; `Sources` must not cite anything missing from it.

## 1.1.3 – 2026-10-18

- Split on-demand parts of `.agents/AGENTS.md` into `.agents/protocols/`, including the new multi-human collaboration
  protocol (shared trunk, collision-free IDs, reconciliation checks).
- YAML front matter and `PREFIX-NNNN` naming for all `docs/` templates; adapters slimmed to pointers or imports.

## 1.1.2 – 2026-10-18

- Proofreading.

## 1.1.1 – 2026-10-18

- Proofreading across `.agents/` and `docs/`.

## 1.1.0 – 2026-10-17

- Tier 1 contract changes need an `Accepted` ADR and a change record with a migration path.
- Unverified options allowed only inside a `Proposed` ADR; shortcut comments require `risk:` and `track:`.

## 1.0.9 – 2026-10-17

- Adapters for Amazon Q, Cline/Roo Code, Cody, Aider, JetBrains Junie, Windsurf, and Zed.

## 1.0.8 – 2026-10-17

- Imported the `ponytail` skill family (six skills) for the full-stack developer persona.

## 1.0.7 – 2026-10-14

- Change classification triage matrix (Tiers 1–4), structured `Sources` block, and agent turn handoff schema.
- Persona "Standard Artifacts & Templates" sections; Definition of Ready in the user story template.

## 1.0.6 – 2026-10-14

- Rules `00-no-self-approval.md` and `01-execution-isolation.md`; pre-MR gate with baseline-drift abort.

## 1.0.5 – 2026-07-18

- Punctuation normalized (ASCII quotes and dashes); typo fixes across templates and READMEs.

## 1.0.4 – 2026-07-04

- Threat models in `docs/threat-models/` (STRIDE template) and in the SSDLC Design gate.

## 1.0.3 – 2026-05-22

- Agent Experience concept, governance guardrails, and the problem-record agent learning loop; persona
  anti-sycophancy clauses.

## 1.0.2 – 2026-04-19

- Added `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, and `SECURITY.md`.

## 1.0.1 – 2026-04-11

- Adapters for Codex/OpenCode (root `AGENTS.md`) and Gemini CLI; "Extending agent governance" section in `README.md`.

## 1.0.0 – 2026-04-10

- Initial framework: `.agents/AGENTS.md`, personas, concepts, rules/skills/commands/tools scaffolding, and `docs/`
  templates for ADRs, user stories, SDPs, change records, and problem records.

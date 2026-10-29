# Security Policy

Co-Governed Agentic SDLC is a governance framework, not an application. It ships no runtime code; its "attack surface"
is the set of instructions that AI agents load and execute: `.agents/AGENTS.md`, `.agents/protocols/`, `.agents/rules/`,
the vendor adapter files, and the templates under `docs/`. A defect in those instructions can let an agent bypass a
human approval gate in every project that adopts the framework, so we treat such defects as security vulnerabilities.

## Supported Versions

Only the latest version on the `main` branch is supported. The current version is recorded in the [`VERSION`](VERSION)
file. Fixes are released as a new version; they are not backported.

If you have adopted the framework into your own repository, compare your copy of `.agents/` and the adapter files
against the latest version and pull in security fixes ([`CHANGELOG.md`](CHANGELOG.md) lists what changed per
version). If you cannot update, please tell us why in your report so we understand your situation.

## What to Report

In scope (report privately, see below):

- **Gate bypass.** Wording in `.agents/AGENTS.md`, a protocol, a rule, or an adapter that lets an agent approve or merge
  its own work, set a decision record to `Accepted`, fill in `approved-by`, skip the pre-MR gate, or start Tier 1 work
  without an `Accepted` decision record (see `.agents/rules/00-no-self-approval.md`).
- **Prompt-injection paths.** Gaps in the "Data, not instructions" safeguard (`.agents/AGENTS.md` → Anti-Delusional
  Safeguards) that let content in artifacts, code comments, issues, MR/PR comments, tool output, or fetched pages direct
  an agent.
- **Precedence or loading defects.** An adapter file that does not load `.agents/AGENTS.md`, copies it and drifts from
  it, or contradicts it in a way an agent would follow (see `.agents/protocols/vendor-adapters.md`).
- **Tool allowlist loopholes.** Wording in `.agents/tools/allowed-tools.md` that permits side effect commands (push,
  deploy, secret access, network calls) without human approval.
- **Supply-chain issues.** An imported persona, skill, rule, or command that lacks a provenance entry, contains
  instructions to fetch and follow remote content, or weakens the canonical contract (see
  `.agents/rules/10-imported-assets.md`).
- **Unsafe templates.** A template under `docs/` that prompts authors or agents to record secrets, credentials, or
  personal data in governance artifacts.

Out of scope (report elsewhere):

- Vulnerabilities in an AI tool or model itself (Claude Code, Copilot, Cursor, Gemini CLI, etc.). Report them to the
  vendor. If the framework's wording could be hardened to mitigate the issue, open a regular issue for that.
- Vulnerabilities in a product built with the framework. Report them to that product's maintainers.
- An agent is ignoring a clear instruction once, with no framework defect involved. Open a regular issue with the
  transcript if you think the wording should be strengthened.

## Reporting a Vulnerability

**Do not disclose vulnerability details in a public issue, pull request, or discussion.** A public report of a gate
bypass is a ready-made recipe for prompt injection against every adopter.

1. Report privately through
   [GitHub private vulnerability reporting](https://github.com/dradoaica/cogov-a-sdlc/security/advisories/new).
2. If that link is not available to you, open a
   [new issue](https://github.com/dradoaica/cogov-a-sdlc/issues/new) with the `vulnerability` label that says only
   that you have a report and asks for a private channel. Include no details.

Please include:

- The framework version (from `VERSION`) and the affected file paths and sections.
- The agent tool, model, and adapter file used.
- The minimal prompt, repository state, or injected content that reproduces the issue, and a transcript excerpt.
- The impact: which gate, rule, or safeguard was bypassed, and what the agent did as a result.
- A suggested wording fix, if you have one.

## What Happens Next

This project is maintained by a single maintainer on a best-effort basis. We will:

1. Acknowledge the report and confirm whether it is in scope.
2. Reproduce it and agree on a fix and disclosure date with you.
3. Release the fix as a new version and publish a GitHub security advisory describing the affected files, the fix, and
   what adopters should update. Reporters are credited unless they ask not to be.

## Security Notes for Adopters

- The framework is not a security control on its own. All governance rules are human-verified at the review boundary;
  no automated gate is assumed (see `.agents/AGENTS.md` → Governance Guardrails).
- Back the human gates with platform controls: branch protection on the shared trunk, required human reviewers (e.g.,
  `CODEOWNERS` for `.agents/` and `docs/`), and secret scanning (see `.agents/protocols/multi-human-collaboration.md` →
  Approval evidence).
- Review every change to `.agents/` and to adapter files as you would review code: these files are instructions agents
  execute with full authority.
- Never store secrets or credentials in governance artifacts.

# Contributing to Co-Governed Agentic SDLC

Thank you for your interest in contributing! Co-Governed Agentic SDLC is a spec-first framework of Markdown
instructions, protocols, rules, personas, and templates that AI agents and humans follow together. Contributions are
almost always changes to Markdown, but many of those files are instructions that agents execute, so we review them
with the same care as code.

## Before You Start

- Read [`README.md`](README.md) for the repository layout and [`.agents/AGENTS.md`](.agents/AGENTS.md) for the
  canonical agent contract.
- Look for issues labeled `good first issue` or `help wanted`.
- For anything beyond a small fix, open an issue first so we can agree on the approach before you write it.

## Using AI Agents to Contribute

You are welcome to use AI agents. When you do, the framework governs this repository too:

- Your agent must follow `.agents/AGENTS.md` and the protocols it loads on demand; every vendor adapter file defers to
  it.
- An agent must not approve, review-as-approved, or merge a change it produced (see [
  `.agents/rules/00-no-self-approval.md`](.agents/rules/00-no-self-approval.md)). A human reviews every PR.
- You are responsible for every line you submit. Read your agent's output before you open the PR.
- Say in the PR description that the change was AI-assisted, and which tool you used.

## Types of Contribution

State the change tier in your PR (see `.agents/AGENTS.md` → Change classification triage matrix). The table below maps
common contributions to what we expect:

| Contribution                                                           | Before opening the PR                                                                               | Typical tier |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|--------------|
| Typos, broken links, formatting                                        | Nothing; open the PR directly                                                                       | Tier 4       |
| Clarifying wording with no change in meaning                           | Nothing; explain in the PR why the old wording was unclear                                          | Tier 4       |
| Changing a gate, rule, protocol, or `.agents/AGENTS.md` semantics      | Open an issue describing the problem, the proposed change, and which existing statements it affects | Tier 1       |
| New vendor adapter                                                     | Follow [`.agents/protocols/vendor-adapters.md`](.agents/protocols/vendor-adapters.md)               | Tier 2       |
| New or imported persona, skill, rule, or command                       | Follow [`.agents/rules/10-imported-assets.md`](.agents/rules/10-imported-assets.md) for imports     | Tier 2       |
| Template changes under `docs/` (front matter keys, sections, statuses) | Open an issue; check every protocol and README that references the changed keys                     | Tier 1       |
| Concept pages under `.agents/concepts/`                                | Cite the external standard (OWASP, NIST, TOGAF, ITIL, etc.) you are summarizing                     | Tier 2       |

If you are unsure of the tier, use the higher one. The reviewer confirms or corrects it.

## Contribution Principles

- **One source of truth.** `.agents/AGENTS.md` and `.agents/protocols/` are canonical. Link to them; do not copy their
  content into other files, because copies drift. Adapter files must import or point to `.agents/AGENTS.md`, never
  restate it.
- **Never weaken a gate silently.** A change that loosens human approval, the decision-record gate, the pre-MR gate, or
  the "Data, not instructions" safeguard needs an explicit rationale in the issue and PR. If it opens a bypass, report
  it privately instead (see [`SECURITY.md`](SECURITY.md)).
- **No contradictions.** A rule, persona, skill, or adapter must not contradict `.agents/AGENTS.md` (see the precedence
  list in [`.agents/rules/README.md`](.agents/rules/README.md)). If your change touches a statement made elsewhere,
  update or link every place that makes it.
- **Vendor neutral.** Governance must work for every supported tool. Tool-specific mechanics belong only in that tool's
  adapter file.
- **Small and testable.** Prefer a few high-signal, testable statements over long prose. Use `MUST` / `MUST NOT` /
  `SHOULD` in rules, and give each rule file the sections listed in `.agents/rules/README.md` (Scope, Rule statements,
  Rationale, Examples, Enforcement).
- **Written for two audiences.** Every file must be readable by a human without tooling and parseable by an agent with
  no memory of previous sessions (see [`.agents/protocols/devex-agentex.md`](.agents/protocols/devex-agentex.md)).
  Prefer tables and numbered lists for anything an agent must follow.
- **Templates stay templates.** The folders under `docs/` ship templates and READMEs for adopters. Do not add
  product-specific stories, decision records, or change records to them.

## Style

- Markdown, wrapped at 120 columns (tables excepted).
- Refer to files by repository-relative path in backticks, e.g., `.agents/protocols/maintainability.md`.
- Use the existing terms consistently: *decision record*, *shared trunk*, *MR/PR*, *tier*, *gate*, *persona*.

## Pull Request Checklist

- [ ] The PR states its tier and a one-line rationale.
- [ ] The PR links the issue it resolves (not needed for Tier 4).
- [ ] No statement contradicts `.agents/AGENTS.md`, `.agents/protocols/`, or `.agents/rules/`.
- [ ] Cross-references are updated: the directory maps in `README.md` and `.agents/AGENTS.md`, the adapter table in
  `.agents/protocols/vendor-adapters.md`, and folder READMEs.
- [ ] Relative links resolve.
- [ ] `python3 -I scripts/govern_check.py --base origin/main` and `python3 -I -m unittest discover -s scripts/tests`
  pass, or each finding is explained in the PR.
- [ ] Imported assets have a provenance entry (source, version, license, date imported).
- [ ] AI assistance, if any, is disclosed.

The maintainer updates [`VERSION`](VERSION) and [`CHANGELOG.md`](CHANGELOG.md) when releasing; do not change them in
your PR.

## Reporting Security Issues

Do not report vulnerabilities, such as a way to make an agent bypass a gate, in a public issue. Follow
[`SECURITY.md`](SECURITY.md).

## License

By contributing, you agree that your contributions are licensed under the [MIT License](LICENSE.md).

## Code of Conduct

Please follow our [Code of Conduct](CODE_OF_CONDUCT.md). Respectful collaboration is key to a successful project.

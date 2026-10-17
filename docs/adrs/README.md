# Decisions

For new Architectural Decision Records (ADRs), please use one of the following templates as a starting point:

* [adr-template.md](adr-template.md) has all sections, with explanations about them.
* [adr-template-minimal.md](adr-template-minimal.md) only contains mandatory sections, with explanations about them. <!-- ### Consequences also contained, though marked as "optional" -->
* [adr-template-bare.md](adr-template-bare.md) has all sections, which are empty (no explanations).
* [adr-template-bare-minimal.md](adr-template-bare-minimal.md) has the mandatory sections, without explanations. <!-- ### Consequences also contained, though marked as "optional" -->

The MADR documentation is available at <https://adr.github.io/madr/> while general information about ADRs is available at <https://adr.github.io/>.

## Naming

- `NNNN-kebab-case-title.md`, where `NNNN` is the next free 4-digit number (e.g., `0001-use-postgresql.md`).
- Numbers are never reused; a replaced decision keeps its file and number.

## Statuses (meaning)

- **Proposed**: drafted (by an agent or human); not yet approved. Implementation must not start (Tier 1 gate).
- **Accepted**: approved by a human; implementation may proceed.
- **Rejected**: considered and declined; kept for the record.
- **Deprecated**: no longer applies, with no direct replacement.
- **Superseded by NNNN**: replaced by a newer ADR; link to it.

## Review expectations (human vs agent)

- Agents **draft** ADRs with status `Proposed`, and may list unverified options marked "unverified - please confirm".
- Only a **human** sets `Accepted`, `Rejected`, `Deprecated`, or `Superseded` (`.agents/rules/00-no-self-approval.md`).

# Architectural Decision Records

Short ADRs capturing decisions and their trade-offs.

**Protocol:** before proposing an architectural change, check this file for an
existing decision. If your change conflicts with one, acknowledge the conflict and
explain why the change is warranted.

Each entry records: date, the decision, context, options considered, and
consequences. Link evidence (e.g. `specs/<feature>/evidence/`) where relevant.

---

## ADR-0001 (2026-06-08) — Static gh-pages previews instead of server review apps

- **Context:** we want a browsable preview for every PR without running a server
  per PR.
- **Decision:** publish static builds to the `gh-pages` branch under
  `/pr-preview/pr-<n>/`.
- **Options considered:** (a) server-based review apps (e.g. Heroku); (b) static
  previews on `gh-pages`.
- **Consequences:** no runtime or cost per PR; limited to static output (no
  server-side APIs in the preview).

<!-- Add new ADRs above this line. -->

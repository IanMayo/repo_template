# Bug log

A running log of bugs hit and fixed, so the same thing is not debugged twice.

**Protocol:** when you hit an error, search this file for the symptom first. When
you resolve a new bug, add an entry.

Each entry records: date, symptom, root cause, fix, and how to prevent recurrence.

---

## 2026-06-08 — Example: PR preview 404s on deep links

- **Symptom:** the PR preview loaded at `/` but deep links returned 404.
- **Root cause:** the app used absolute paths that ignored the
  `/pr-preview/pr-<n>/` base path.
- **Fix:** switched the app to base-relative links / a base-aware router config.
- **Prevention:** keep app links base-relative; check a deep link in every PR
  preview.

## 2026-06-08 — Blog publish cancelled on every merge (gh-pages concurrency)

- **Symptom:** after merging to `main`, the `Publish blog on merge` run showed
  `cancelled` (0 jobs executed) while `Deploy site to GitHub Pages` succeeded.
- **Root cause:** `deploy.yml` and `publish-blog.yml` both triggered on the same
  `push` to `main` and shared `concurrency: group: gh-pages`. GitHub keeps only one
  running + one *pending* run per group; two runs created in the same instant from
  the same event leave one to be cancelled before it starts.
- **Fix:** folded blog publishing into `deploy.yml` as a step in the deploy job, so
  a merge makes a single `gh-pages` push (deploy + blog together); removed
  `publish-blog.yml`.
- **Prevention:** do not put two workflows that trigger on the *same* event in the
  same concurrency group; serialise same-event `gh-pages` writers within one run.

<!-- Add new entries above this line. -->

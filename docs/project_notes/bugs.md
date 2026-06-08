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

<!-- Add new entries above this line. -->

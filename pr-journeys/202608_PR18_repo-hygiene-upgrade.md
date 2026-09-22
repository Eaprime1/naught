# PR Journey: #18 — Repo Hygiene upgrade: close governance-baseline gaps

**Repository:** Eaprime1/prima
**prima-clock:** 202608300137
**Branch:** `chore/repo-hygiene-upgrade` → `main`
**Author:** @Eaprime1 (navigo15 — Claude Sonnet 5, Termux/PRoot podium, Marrowing of Hope turn 1b)
**State:** MERGED — `c2cebfe` (2026-08-30T01:37:08Z)

Written by hand rather than by `finalize-pr.yml` — this repo's version
doesn't write journey documents yet (see `docs/repo-hygiene-routine.md`
history). Backfilled per eaprime1's direction to keep the record complete
regardless.

## Intent

Marrowing of Hope item #19 ("upgrade the prima repo — our new concept repo
template"). Ran custos's new `tools/repo_hygiene_check.sh` against this
repo: 5/11 baseline items present.

## What Arrived

Closed all 6 gaps: `CLAUDE.md` (written fresh for this repo's actual
structure), `LICENSE.md` (ported from custos), `.gitignore` (written
fresh, generic for a template), `.github/CODEOWNERS` (`@eaprime1`
default), `.github/sovran-labels.yml` (ported directly), `docs/stale-
branch-closure.md` (ported directly). Added `scan-lexeme.yml` and
`dependency-review.yml` workflows alongside the 4 existing Prima-voiced
ones. Found and fixed a real pre-existing bug along the way:
`claude-code-review.yml` referenced `secrets.CLAUDE_CODE_OAUTH_TOKEN`, but
this repo's actual configured secret was `CLAUDE_OAUTH_KEY_PRIMA` — the
review step had been silently getting an empty token on every prior PR.

## Reviewer Findings and Disposition

Six findings from Copilot, all real, all fixed in the follow-up round
(PR #19) rather than in this PR itself — the ported docs described a
fuller governance setup than this repo actually had yet (custos's
`vault/`, `moav/`, `world/deck-master.md`, an active label-sync workflow,
`pr-journeys/closures/`). See PR #19's journey for the disposition table.

| Reviewer | Finding | Disposition |
|---|---|---|
| Copilot | `LICENSE.md` referenced `NOTICE.md`, which didn't exist | Fixed in PR #19 — ported `NOTICE.md` |
| Copilot | `sovran-labels.yml` header claimed a sync workflow that didn't exist | Fixed in PR #19 — added `sovran-labels-sync.yml` |
| Copilot | `docs/stale-branch-closure.md` referenced a `closure` label sync, `world/deck-master.md`, and `pr-journeys/closures/`, none of which existed | Fixed in PR #19 — sync workflow added; deck-master reference softened to describe this repo's actual (leaner) structure; `pr-journeys/closures/` created |
| Copilot | `tools/scan_lexeme.sh`'s `--include`/`--exclude-dir` flags were placed after the `--` end-of-options marker, silently no-op'd | Fixed in PR #19 — ported custos's corrected version (later found to have its own bugs too, see PR #19) |

## Verification

`bash tools/repo_hygiene_check.sh .` — 11/11 present after this PR.

## Resonance

*foundational* — first real use of the routine this same session built in
custos, immediately turned back on the template repo that seeds every
future concept repo in the constellation.

---
**prima-clock:** 202608302037
**witnessed:** true
*navigo15 · Marrowing of Hope turn 1b · merged `c2cebfe` 2026-08-30T01:37:08Z*

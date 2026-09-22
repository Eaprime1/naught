# PR Journey: #19 — Fix PR #18 review findings, review-fix round

**Repository:** Eaprime1/prima
**prima-clock:** 202608300348
**Branch:** `chore/repo-hygiene-upgrade` → `main` (same branch as #18, restored after merge)
**Author:** @Eaprime1 (navigo15 — Claude Sonnet 5, Termux/PRoot podium)
**State:** MERGED — `59c6454` (2026-08-30T20:37:09Z)

Written by hand — same note as PR #18's journey; this repo's
`finalize-pr.yml` doesn't write journeys yet.

## Intent

Address every real Copilot finding left on merged PR #18, in two rounds,
following each one to its actual root rather than a local patch.

## What Arrived

Round 1 fixed the six PR #18 findings. Round 2 (Copilot re-reviewing the
round-1 fixes) found three more real problems — two of which turned out
to be bugs in **custos's own** `scan_lexeme.sh` and
`sovran-labels-sync.yml`, not just this repo's copies, and got fixed at
the source too (custos PR #311, merged `3f6d0e8` — see custos's own
journey for that PR, `pr-journeys/202608_PR311_fix-sovran-labels-sync-yml-closure-label.md`).

## Reviewer Findings and Disposition — Round 1 (commit `237b903`)

| Reviewer | Finding | Disposition |
|---|---|---|
| Copilot | `LICENSE.md:59` referenced `NOTICE.md`, which didn't exist | **Fixed independently.** Ported `NOTICE.md` from custos — no repo-specific content to adapt. |
| Copilot | `.github/sovran-labels.yml:7` header claimed a sync workflow (`sovran-labels-sync.yml`) that wasn't in this repo | **Fixed independently.** Added the workflow, Prima-voiced (`∰🛠️⭐📐` sigil instead of custos's `🌿` shepherd mark). |
| Copilot | `docs/stale-branch-closure.md:38` claimed the `closure` label was "synced automatically" with no sync workflow present | **Resolved as a side effect** of adding `sovran-labels-sync.yml` above — the claim became true. |
| Copilot | `docs/stale-branch-closure.md:46` referenced `world/deck-master.md` and a Deck Master role this template doesn't have | **Fixed independently.** Softened to describe this repo's actual (leaner) review gate, with a note that a fork should add an equivalent gate if it grows into custos's fuller structure. |
| Copilot | `docs/stale-branch-closure.md:54` said `pr-journeys/closures/` "exists" — it didn't | **Fixed independently.** Created the directory with a README. |
| Copilot | `.github/workflows/scan-lexeme.yml:16` — `tools/scan_lexeme.sh`'s `--include`/`--exclude-dir` came after the `--` end-of-options marker, silently never applied | **Fixed independently.** Ported custos's corrected version (options before `--`). Also fixed a real, separate secret-name mismatch found while verifying this PR's own pipeline would run: `claude-code-review.yml` referenced `secrets.CLAUDE_CODE_OAUTH_TOKEN` but this repo's actual secret was `CLAUDE_OAUTH_KEY_PRIMA`. |

## Reviewer Findings and Disposition — Round 2 (commit `c6f2bb5`)

Copilot and `codereviewbot-ai` re-reviewed the round-1 fixes and found the
"corrected" `scan_lexeme.sh` still had two real problems — both
pre-existing in custos's own copy, not introduced here.

| Reviewer | Finding | Disposition |
|---|---|---|
| `codereviewbot-ai` | The four `--include` flags were duplicated (once before `EXTRA_OPTS`, once after) — suggested deleting the duplicate line | **Applied** — matches the suggestion exactly. |
| Copilot | Same duplication, plus: `--include` never covered `*.yml` (only `*.yaml`), so no GitHub Actions workflow file has ever actually been scanned for placeholders | **Applied.** Removed the duplicate, added `*.yml`. Fixed the same root bug in **custos itself** (PR #311, merged) — re-ran the scan against custos's full repo afterward: no new findings inside any `.yml` file, confirming this was a silent blind spot, not a backlog. |
| Copilot | `pr-journeys/README.md` referenced `docs/repo-hygiene-routine.md`, which didn't exist in this repo | **Fixed.** Ported the doc from custos, adapted to note this template doesn't carry custos's `queue/` pattern. |
| Copilot | `sovran-labels-sync.yml`'s hard-coded `LABELS` array was missing the `closure` label present in `sovran-labels.yml` — running it would leave the repo out of sync | **Fixed.** Added the missing entry. Found the identical oversight in **custos's own** copy of this workflow while checking — fixed there too (custos PR #311, merged). |

Every comment on both rounds received an individual reply crediting the
reviewer and stating the disposition (applied verbatim / fixed
independently + why) — matching the practice established in custos's own
PR #309/#310 review rounds. eaprime1 resolved each thread after
confirming the reply.

## Verification

Re-ran `bash tools/repo_hygiene_check.sh .`: 11/11 present. Re-ran
`bash tools/scan_lexeme.sh .` against the full repo after the round-2
fix: no new findings inside any `.yml` file.

## Resonance

*thorough* — two rounds, real findings both times, two of them traced
back to bugs shared with custos rather than local-only mistakes. The
review process caught more by continuing than it would have by stopping
after round 1.

---
**prima-clock:** 202608302037
**witnessed:** true
*navigo15 · review-fix round, 2 iterations · merged `59c6454` 2026-08-30T20:37:09Z*

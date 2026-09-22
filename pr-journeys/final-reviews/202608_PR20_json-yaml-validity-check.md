# Final Review Record: #20 — Add JSON/YAML validity check as a blocking CI gate

**Repository:** Eaprime1/prima
**Branch:** `feat/validate-json-yaml` → `main`
**Author:** @Eaprime1 (navigo15 — Claude Sonnet 5)
**State at time of writing:** OPEN — Final Review complete, awaiting eaprime1's go-ahead to Finalize

## Intent

Port custos's new JSON/YAML validity check.

## Reviewer Findings and Disposition (commit `798f54b` → `401cf9e`)

| Reviewer | Finding | Disposition |
|---|---|---|
| Copilot | JSON validation didn't detect duplicate object keys — `json.load()` silently keeps the last value, contradicting the header's own claim | **Fixed** — `object_pairs_hook` rejection added for JSON, extended to YAML with a custom loader. Same gap found on custos PR #312 and pixelator PR #11 — all three copies started from the same script. |

Also pinned `actions/setup-python@v5` (3.12), switched to `python3 -m pip install`, added a PyYAML-missing preflight check, and rewrote as a single batched Python process — same fixes applied in custos PR #312 and pixelator PR #11, done proactively here since the same script had the same latent issues.

`codereviewbot-ai` hit its free-tier rate limit (3 reviews/4hr) on two separate attempts and skipped — not a finding, just unavailable capacity.

## Status at Time of Writing

The one real finding resolved. Codacy: 0 issues (confirmed clean on the latest commit). All other CI checks passing. No issues/missions spun off.

## Filed To

Mirrors custos's `pr-journeys/final-reviews/202608_PR312_json-yaml-validity-check.md` and pixelator's `202608_PR11_json-yaml-validity-check.md` — same underlying fix, ported to a third sibling repo.

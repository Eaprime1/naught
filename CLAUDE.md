# prima — Concept Repo Template

`prima` is the origin template for spinning up a new "concept terminal" —
a gamified, quest-based onboarding experience delivered through a real
terminal session. Fork it, fill in `prima.yaml`, and you have a working
skeleton: world lore, a quest graph, a bootstrap script, and the same
governance/PR pipeline the rest of the constellation (custos, pixelator,
and siblings) carries.

Run `bash tools/scan_lexeme.sh` to find unfilled template placeholders —
`prima.yaml`'s `name: "My Prima Terminal"` is the canonical one; nothing
is "yours" until that's replaced.

## Structure

| Path | Purpose |
|---|---|
| `prima.yaml` | The concept manifest — name, slug, theme. Fill this in first. |
| `world/` | Lore and setting — `lore.md`, `factions.md`. The context that makes quests mean something. |
| `quests/` | The quest graph. `QUEST_SCHEMA.md` is the format contract; `quests/example/001-awakening.md` is the starter quest every fork ships with. |
| `seeds/` | Bootstrap layer — `bootstrap.sh` (idempotent), `packages.yaml`, dotfiles deployed to `~/`. |
| `turns/` | Session record — `log.md` per `TURN_SCHEMA.md`. One entry per meaningful session boundary. |
| `intake/` | THEE/YOD/EMBER-style raw-fragment intake — `incoming.md`, `triad-thee-yod-ember.md`. |
| `guides/` | `getting-started.md` — the five-step path from clone to first quest. |
| `docs/` | Process documents (branch closure, etc.) shared across the constellation. |
| `.claude/`, `.codex/`, `.agents/` | Agent config — Claude Code / Codex baselines, generated skills. |
| `.sovran/identity.md` | The repo's own witness-voice identity (Prima — canonical form, template fidelity, origin integrity). |
| `tools/` | `scan_lexeme.sh` (placeholder scan), `prime_check.sh` (prime-state progression), `thee.sh`/`yod.sh`/`ember.sh` (intake tooling). |

## Governance

This repo carries the same `.github` PR pipeline as the rest of the
constellation: `claude-code-review.yml` and `sovran-voice.yml` speak in
Prima's own persona (template fidelity, origin integrity) rather than
custos's shepherd voice — a forked concept repo inherits Prima's voice
until it grows its own. `CODEOWNERS` defaults to `@eaprime1`; update it on
fork. See `docs/stale-branch-closure.md` for the branch-closure
convention shared constellation-wide.

## What's Deliberately Not Here

Custos-specific evolution — `atelier/`, `vault/`, `moav/`,
`prima-clock/`, `branch-tracker/`, `device/`, `queue/` — is custos's own
later growth, not part of the base template. A fork starts lean; grow
into those patterns (or your own) as the concept actually needs them,
rather than inheriting custos's full weight unearned.

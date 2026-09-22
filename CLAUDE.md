# CLAUDE.md — eaprime1/naught

**Status: scaffold-only. This repo's final shape is not yet decided by the project owner — build the minimum, do not over-architect.**

This file is read by Claude Code when working in this repository (via `CLAUDE_CODE_OAUTH_TOKEN` in GitHub Actions, or locally). If a task requires architecture this file doesn't cover, stop and flag it in the PR rather than inventing it.

> The prima template's original CLAUDE.md is held, not replaced, at
> [`docs/origin/prima-template-CLAUDE.md`](docs/origin/prima-template-CLAUDE.md).

## What this repository is

naught is one stage in the Custos custody pipeline for THE/UNEXUS. It sits between **Nullus** (which performs nullification) and the **Zero space repo** (where content becomes fully Known). Its job is to hold and process content while it exists in **naught space** — a local, resettable, low-pressure state of "not yet, but ready."

Naught space is not Polaris. Polaris is the fixed, invariant reference — it never resets. Naught/Zero is a *local state*: reduced pressure, unassigned, reset, or available potential. Returning something to naught is a navigational operation, not a failure or regression. Don't conflate the two in code, comments, or naming.

## Position in the custody chain

```
Unknowable (external, not yet in custody)
  → Maw (raw processing pool — transforms what enters it)
  → Known_naught / empty_vector
  → Nullus (nullification — starts the formal chain of custody)
  → Unknown / anti_vector
  → [ THIS REPO OPERATES HERE ]
  → Naught_known / vector
  → (polar flip / prime decision — an external trigger, not automated here)
  → Known
  → crosses into Zero space as Unknown_zero
  → Zero space repo
```

This repo owns the **Unknown → Naught_known** transition, and whatever other "aspects of naught space" get assigned to it over time. That scope is still being decided by the project owner — leave room for it, don't pre-fill it.

## Hard rules for anything Claude Code does here

1. **No erasure, ever.** This isn't a style preference — the term "Nullus" in this project's own founding definition explicitly means "the state before something was ever a category," which is different from "empty" (had something, lost it). Erasure-pattern operations (delete-and-forget, destructive overwrite, silent truncation) are out of scope for this repo. Use isolate, transform, hold, transit in code, comments, commit messages, and PR descriptions — never erase, delete, wipe, destroy. If a task seems to require deleting something, stop and ask rather than doing it.
2. **Minimal necessary change.** Each transition should change only what the transition requires. No incidental refactors, no "while I'm in here" cleanup, in the same PR as a custody-state change.
3. **Gas transfer as the data model.** Movement between stages is an instantaneous semantic copy — shape-agnostic, container-independent. Never mutate an original in place; produce a new state and preserve the prior one.
4. **Build loosely coupled, not fused.** Keep a minimal, clean interface to Nullus (input) and the Zero space repo (output). Don't import internals from sibling repos or assume shared runtime state.
5. **Support skip-ahead re-entry.** An item that previously reached a stable state and later returns to naught should be able to move directly to an available stable state on re-entry, without re-running every intermediate stage (`zero_polar_(any_level)`). Implement this as a real capability, not a comment.

## Data model

Extend the existing Custos germ-intake custody schema — don't replace it.

```json
{
  "identity": {
    "name": "",
    "one_line_signal": "",
    "source": "",
    "prima_clock": "YYYYMMDDHHMM"
  },
  "naught_state": {
    "current": "unknown | naught_known",
    "prior": "",
    "entered_at": "YYYYMMDDHHMM"
  },
  "custody": {
    "suit": "",
    "plank_status": "",
    "transit_type": "gas_transfer",
    "authorized_by": "Custos"
  },
  "hold_note": {
    "do_not_develop": "",
    "do_not_connect_yet": "",
    "wait_for": ""
  },
  "closing_status": "HOLDING"
}
```

## Suggested structure

```
naught/
  README.md                  — this repo's role, one paragraph, links to Custos
  CLAUDE.md                  — this file
  schema/naught_intake.json  — the schema above, as an actual JSON Schema
  intake/                    — incoming items from Nullus, one file per item
  transit/                   — items actively moving unknown → naught_known
  outbound/                  — items ready to hand to the Zero space repo
  docs/open-questions.md     — mirror of "Do not resolve," below
```

## When reviewing or opening PRs

- Check every changed file for erasure-pattern language or logic before approving.
- Flag anything that fuses this repo's internals to Maw, Nullus, or Zero space rather than going through a defined interface.
- If a PR silently expands this repo's scope beyond Unknown → Naught_known, note it explicitly in the review rather than merging it quietly — that's an owner decision, not a default.

## Explicitly do not resolve

- Whether this repo absorbs other "aspects of naught space" beyond the Unknown → Naught_known transition, or stays narrow — owner still deciding.
- Whether naught is the final repo name.
- The internal mechanics of the "polar flip" trigger — this repo receives the *result* of that decision; it does not make the decision.
- Exact relationship to eaprime1/maw (confirmed distinct repo; a pool that transforms what enters it) and eaprime1/nullus (name assumed by convention, not yet confirmed).

Hold the shape; don't fill it.

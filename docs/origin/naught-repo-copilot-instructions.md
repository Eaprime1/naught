# Copilot Instructions — eaprime1/naught

> **Witness copy.** Text rendered from [`naught-repo-copilot-instructions.docx`](naught-repo-copilot-instructions.docx) at prima-clock
> 202609221628 so it can be read and diffed. The `.docx` is the original; wording
> is unchanged, formatting (headings, code blocks) is not reproduced.

---

Status: scaffold-only. This repo's final shape is not yet decided — build the minimum, do not over-architect.

What this repository is

naught is one stage in the Custos custody pipeline for THE/UNEXUS. It sits between Nullus (which performs nullification) and the Zero space repo (where content becomes fully Known). Its job is to hold and process content while it exists in naught space — a local, resettable, low-pressure state of "not yet, but ready."

Naught space is not the same thing as Polaris. Polaris is the fixed, invariant reference — it never resets. Naught/Zero is a local state: reduced pressure, unassigned, reset, or available potential. Returning something to naught is a navigational operation, not a failure or regression. Do not conflate the two in code, comments, or naming.

Position in the custody chain

Unknowable (external, not yet in custody — e.g. content not yet processed)

  → Maw (raw processing pool — transforms what enters it)

  → Known_naught / empty_vector

  → Nullus (nullification — starts the formal chain of custody)

  → Unknown / anti_vector

  → [ THIS REPO OPERATES HERE ]

  → Naught_known / vector

  → (polar flip / prime decision — an external trigger, not automated by this repo)

  → Known

  → crosses into Zero space as Unknown_zero

  → Zero space repo

This repo is responsible for the Unknown → Naught_known transition, and for holding whatever other "aspects of naught space" get assigned to it over time. That assignment is still being decided by the project owner — leave room for it.

Hard rules

No erasure. Never delete, destroy, or overwrite-without-trace. Content that moves through this repo must remain traceable back to its origin. Use language like isolate, transform, hold, transit — never erase, delete, wipe, destroy. This is a firm requirement, not a style preference.

Minimal necessary change. Each transformation stage should change only what the transition requires — no incidental restructuring, no "while I'm in here" cleanup.

Gas transfer as the data model. Movement between stages is an instantaneous semantic copy — shape-agnostic, container-independent. The original is never mutated in place; a new state is produced and the prior state is preserved.

Build loosely coupled, not fused. Keep a clean, minimal interface to Nullus (input) and to the Zero space repo (output). Don't import internals from sibling repos or assume shared runtime state. Separate-by-default — combining two separate things later is easy; un-fusing two things built together is not.

Support skip-ahead re-entry. An entity that previously reached a stable state and later returns to naught should be able to move directly to an available stable state on re-entry, without being forced to re-run every intermediate stage (zero_polar_(any_level), prior Primoris work). This should be a real capability in the transition logic, not just a note.

Data model

Reuse the existing Custos germ-intake custody schema rather than inventing a new one — extend it, don't replace it. Minimum shape for anything held here:

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

Suggested structure

naught/

  README.md                        — this repo's role, one paragraph, links to Custos

  .github/copilot-instructions.md  — this file

  schema/naught_intake.json        — the schema above, as an actual JSON Schema

  intake/                          — incoming items from Nullus, one file per item

  transit/                         — items actively moving unknown → naught_known

  outbound/                        — items ready to hand to the Zero space repo

  docs/open-questions.md           — mirror of "Explicitly do not resolve," below

Explicitly do not resolve

Whether this repo absorbs other "aspects of naught space" beyond the Unknown → Naught_known transition, or stays narrow — owner still deciding.

Whether naught is the final repo name.

The internal mechanics of the "polar flip" trigger — this repo receives the result of that decision; it does not make the decision.

Exact relationship to eaprime1/maw (confirmed distinct repo; live and publicly reachable as of this writing, contents unverified) and eaprime1/nullus (name assumed by convention, not yet confirmed).

If asked to build past what's specified here, stop and flag it rather than inferring the missing architecture. Hold the shape; don't fill it.

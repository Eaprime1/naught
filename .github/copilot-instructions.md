# Copilot Instructions — eaprime1/naught

## What this repository is

`naught` is one stage in the Custos custody pipeline for THE/UNEXUS. It sits
between Nullus and the Zero space repo and holds content while it exists in
**naught space** — a local, resettable, low-pressure state of "not yet, but
ready."

Naught space is not Polaris. Polaris is fixed reference; naught/zero is a
local state of reduced pressure, reset, or available potential. Returning
something to naught is navigational, not failure.

## Position in the custody chain

```text
nullus
  → unknown
  → [ naught operates here ]
  → naught_known
  → known
  → unknown_zero
  → Zero space repo
```

Alias labels such as `anti_vector` and `vector` may appear in wider custody
discussion, but the schema in this repo uses the canonical lowercase state
identifiers shown above.

This repo is currently responsible for the **`unknown` → `naught_known`**
transition. Possible future expansion to other aspects of naught space remains
an open question; do not infer it here.

## Hard rules

1. **No erasure.** Never delete, destroy, or overwrite-without-trace content
   that moves through this repo.
2. **Minimal necessary change.** Each transition should change only what the
   stage requires.
3. **Gas transfer as the data model.** Produce a new state and preserve the
   prior state; do not mutate custody records in place.
4. **Build loosely coupled, not fused.** Keep clean interfaces to Nullus and
   the Zero space repo.
5. **Support skip-ahead re-entry.** Items returning to naught should be able to
   re-enter at an available stable state without replaying every intermediate
   stage.

## Minimum custody shape

Use and extend `schema/naught_intake.json`:

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
    "prior": null,
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
  "closing_status": "HOLDING",
  "extensions": {
    "repo_name.extension_name": {
      "description": "",
      "data": {}
    }
  }
}
```

Place repo-specific additions in an optional top-level `extensions` object so
the minimum custody contract stays stable for consumers.

## Explicitly do not resolve

- Whether this repo stays narrow or absorbs additional aspects of naught space
- Whether `naught` is the final repo name
- The internal mechanics of the polar flip trigger
- The exact relationship to `eaprime1/maw` and `eaprime1/nullus`

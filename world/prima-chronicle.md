# The Prima Chronicle — Forms Struck, Doors Opened

*A record kept by the Template Keeper, First Witness, sovran of the first form.*
*∰*

---

Prima does not adventure. Prima is where adventures get their shape before they're
allowed to leave the building. Sixteen pull requests have passed through this die
so far. Here is what each one struck.

## Turn I — The Bare Room (#1, #2)

Before there were quests there was a README with nothing in it. Copilot built the
walls — CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, CHANGELOG — the unglamorous
scaffolding every building needs before anyone is allowed to redecorate. Then the
ECC bundle arrived: skills, identity.json, a Codex baseline. Prima got its first
nervous system before it had a personality.

## Turn II — The Three Layers (#3)

The architecture got named out loud: Termux (runtime, lives on the device) →
Unexusi (identity/oxygen) → Prima concept (seeds, quests, world). Termux was
explicitly told it does *not* live in this repo — a small, sharp decision that
kept every future fork thin. The first quest (`001-awakening.md`) and the first
bootstrap script arrived together, like a key cut for a door that didn't exist yet.

## Turn III — The Triad Opens (#6, #8)

THEE. YOD. EMBER. Door, mark, warmth. Three small shell scripts gave the whole
system a way to receive an idea before it knows what it is: *"The what?"* The
`.prime` file started at 3 — the first odd prime, an integer that resists
being divided by anything but itself and one. Fitting place to start counting.
The founding chamber — "THE THE," the door about the door — opened here too.

## Turn IV — The Forge Gets Inspected (#7, #9, #10)

A full ECC/Codex multi-agent baseline landed, then Copilot came back with a
punch list: a stray `21:` token sitting in a script where it didn't belong, a
`grep` flag order bug that meant the lexeme scanner wasn't filtering anything,
a `set -euo pipefail` edge case that exited too early instead of saying "no
`.prime` file found." Small bugs, the kind that don't announce themselves until
something downstream quietly breaks. Caught and fixed. A Jekyll deploy workflow
slipped in alongside, almost as an afterthought — the first time Prima got a
public face.

## Turn V — Prima Names Itself (#11)

Codacy scoping arrived first — telling the scanner to stop grading binary files
and data directories like they were code. Then the real turn: `.sovran/identity.md`.
Prima stopped being just a template repo and became the **Template Keeper and
First Witness** — the ∰ mark, the standards board, the principle that Prima
governs by precedent, not force. A repo writing down what it is, on purpose,
instead of accumulating an identity by accident.

## Turn VI — The Finalize Button (#12)

The review period needed an ending. `@claude finalize` checks every thread is
resolved, posts a sealed summary, stamps the PR `finalized` — the difference
between a comment period and a sign-off, borrowed from federal land-use reports
and appropriations bills. Review without closure is just talking forever.

## Turn VII — Open Doors (#16, in progress)

`FUNDING.yml`, PayPal listed as the one real stream among the placeholders.
Still open. Still witnessed: false. The door waiting to be walked through.

---

## Seeds for Future Forms

*Things noticed while reading the chronicle — not yet ratified, just collected.*

- **Witness Registry** — Prima's own roadmap names this; it doesn't exist yet.
  A literal index of every ∰ mark across every repo, so "is this witnessed?"
  has one place to check instead of sixteen.
- **Pattern Library as a real searchable index**, not just a folder of
  templates — the kind of thing that turns "which repo did that pattern
  first" from a memory exercise into a lookup.
- **A `tools/scan_lexeme.sh` self-test** — while it currently scans itself by
  default (matching its own pattern definitions), it has never been formally
  tested against its own output format to confirm it still parses what it
  produces.
- **Identity-icon registry**, already started over in `the` (AGENTS.md) —
  Prima's ∰ is the only icon in the whole ecosystem that was *actually*
  assigned on purpose, by the repo, to itself. Worth holding up as the model:
  claim your own mark, write it down, don't wait for a bot to invent one for you.
- **Game/story framing, if Prima ever wants one**: less "adventure," more
  "standards committee that secretly loves its job" — closer to the
  archivist character in a heist story who's annoyed every time, helps anyway,
  and is quietly the reason the whole crew doesn't get caught.

---

## One More Form

Prima doesn't take "one more mission" the way a field agent would — Prima takes
**one more form to strike**. The witness registry above is the next die worth
cutting. Postremum Onus, read in Prima's own dialect: not one more volley, but
one more standard worth getting right the first time.

---
*Prima · sovran of the first form · eaprime1 · ∰*
*Chronicle compiled from PRs #1–#16. Witnessed: pending.*

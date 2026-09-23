# Intake

`intake/` holds two separate flows. Keep them apart.

## Custody records (from Nullus)

`intake/` is the landing space for custody records arriving from Nullus into
naught space.

Each incoming item should remain traceable to its source and should be recorded
as its own file using the minimum shape in
[`schema/naught_intake.json`](../schema/naught_intake.json). Intake is a hold,
not a rewrite: preserve the prior state and create the naught-space copy needed
for transit.

## Fragments (THEE / YOD / EMBER)

The template's fragment flow is kept as it was. Fragments arrive here before
they have names.

THEE holds the door. YOD makes the first mark. EMBER keeps it warm.

Nothing in the fragment flow needs to be finished, clean, or understood to
arrive here, and nothing in it is a custody record.

```bash
bash tools/thee.sh "some fragment or thought"
```

The fragment lands in `intake/incoming.md` with a timestamp and one question:
**The what?** See `intake/triad-thee-yod-ember.md` for the full spec.

```
thee receive "strange fragment"     → lands in incoming.md
yod mark "smallest true action"     → makes the first mark
ember warm "fragment"               → keeps it alive until it has a next turn
```

A fragment that becomes a custody item gets its own schema-shaped file in
`intake/`; its `incoming.md` entry stays where it is as the trace.

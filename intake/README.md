# Intake

`intake/` is the landing space for custody records arriving from Nullus into
naught space.

Each incoming item should remain traceable to its source and should be recorded
as its own file using the minimum shape in
[`schema/naught_intake.json`](../schema/naught_intake.json). Intake is a hold,
not a rewrite: preserve the prior state and create the naught-space copy needed
for transit.

# Transit

`transit/` holds custody records that are actively moving through the
**`unknown` → `naught_known`** transition.

Use `gas_transfer` semantics: create a new state record here, preserve the
prior state, and keep origin traceability intact.

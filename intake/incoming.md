# Incoming Register

Use this file as a lightweight register only when an incoming custody record
needs a temporary landing note before its own file is created in `intake/`.

Preferred shape for actual items:

- one file per item
- traceable back to its source
- structured to the minimum schema in `schema/naught_intake.json`
- ready to move by `gas_transfer`, not in-place mutation

gps_language_core (draft crate)

Purpose
- Headless language layer used by the LSP client core. Provides types,
  categories, and utilities (no UI/kernel coupling).

Status
- Draft manifest for split. The project-files entry references the
  root-level gps_language_core.gpr. For a standalone repo, move the GPR and
  sources into the crate and update paths (language/src -> src).

Dependencies
- common, shared, gnatcoll_sqlite, gnatcoll_xref

Build (after split)
- alr build -- -P gps_language_core.gpr


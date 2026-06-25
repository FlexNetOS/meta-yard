# License Reference Registry

Provenance + original-license archive for third-party / upstream code that has been **vendored**
into FlexNetOS repos under a different working license. The original `LICENSE` files are archived
here (out of the consuming repo's tree) so the consuming repo presents a single, clean license
surface while the upstream provenance is preserved and auditable.

| Vendored into | Component | Origin | Original license | Archived file | Working license in repo | Notes |
|---|---|---|---|---|---|---|
| `teri` | `pebesen/` (community platform: api/core/db/search/notifications/intelligence/bin + frontend) | `github.com/SHA888/pebesen` | AGPL-3.0 | [`pebesen-LICENSE-AGPL-3.0.txt`](./pebesen-LICENSE-AGPL-3.0.txt) | MIT | Owner-authored (SHA888). Vendored into the teri MIT workspace and re-licensed MIT by the owner for in-tree use; the original AGPL text is archived here for provenance. teri's `cargo-deny` scans the workspace as MIT. |

## Why this exists

cargo-deny (and license scanners generally) read the per-crate `license` field + any in-tree
`LICENSE` file. When an owner-authored upstream is vendored into a repo with a different license,
leaving the upstream `LICENSE` in-tree makes the scanner report a mixed/foreign license. Archiving
the original here — and setting the vendored crates' `license` field to the consuming repo's license
(when the owner has relicensed) — keeps the consuming repo's license surface coherent without
losing the provenance record.

## Adding an entry

1. Move the upstream `LICENSE` out of the consuming repo into this directory, named
   `<component>-LICENSE-<spdx>.txt`.
2. Set the vendored crates' `license` field to the consuming repo's working license (only if the
   owner has the right to relicense — e.g. owner-authored upstream).
3. Add a row to the table above with origin, original license, and the working license.

# meta-yard — the Yard (Tier Y)

Nested meta repo holding **ported-from / reference / not-adopted-as-is source**, per
[`META-ORG-POLICY.md` P8.y](https://github.com/FlexNetOS/meta/blob/main/META-ORG-POLICY.md).

These repos are kept for **provenance and reference** — e.g. the upstream we ported *from*,
or source we may mine parts from later. They are **never** wired into the `meta` root
build, CI, or Cargo workspace, so they stop adding confusion to the active workspace.

## Members

| Repo | Why it's here |
|------|---------------|
| `Archon` | Forked AI harness; ported → `harness-agent-rs` (Rust). Kept as provenance anchor. |
| `MiroFish` | Forked web app (backend/frontend); reference / not adopted as-is. |

## Rules (P8.y)

- **Out of the root build/CI/workspace.** Never a root Cargo `member` or dependency.
- **P1 identity only.** Genuine `FlexNetOS/` repo; third-party source stays as `upstream`.
- **Explicit promotion.** Moving a repo *out* of the yard — to adopt it, or to adopt its
  crates via P8.a (crates-only) — is a deliberate re-tier with its own PR. Nothing is
  silently graduated.
- **Provenance.** When porting *from* a yard member, record the source commit in the
  port's parity ledger; the yard copy is the provenance anchor.

## Layout

This repo tracks only its index (`.meta.yaml`, this README, `.gitignore`). The member
repos are cloned in by `meta git update` and are themselves gitignored here.

```bash
meta git update          # clone/refresh yard members
meta project list        # list members
```

# Desktop Completeness Audit — Competitor-Informed (KEEL-DSN-003)

Reference set audited: **Devin/Cognition** (agent chat, secrets, billing seats), **Antigravity** (agent manager, inbox), **Conductor** (multi-workspace switcher), **OpenCode** (session list, model picker, permission prompts), **Factory** (droid sessions, review), **Linear** (inbox/triage grammar), **Higgsfield/Paper** (kit tooling).

## What the kit already covered

- Brand system (logo, color, type, iconography, voice) — page 04
- Tokens synced code↔design (hash `3cc7b891`) — `docs/design/tokens.json`
- Product screens (app shell, Record), interfaces (IDE, Ops, Agents run detail, Marketplace, Builder) — pages 10–12
- All 8 Settings panels — page 17 (`17.1`–`17.6`)
- P-10 card + Tasks lane, billing, onboarding, command palette, remaining views + state matrix, drawers — page 18 (`18.1`–`18.5`)
- Accessibility contracts — page 14

## Gaps closed on page `19 — Desktop Completeness` (`p-J-0`)

| Artboard | Surface | Borrowed from |
|---|---|---|
| `19.1` `322-0` | Component primitives vocabulary — buttons/inputs/menus/tooltips/toasts/dots+kbd/dialogs/disclosures + "never ships" rules | Linear restraint, all |
| `19.2` `35J-0` | Agent composer deep-dive — attachments, model/route selector, pre-flight simulation strip, inline P-10 request in thread | Devin, Antigravity, OpenCode |
| `19.3` `35K-0` | Workspace switcher (⌘⇧W, worktree-scoped, per-workspace P-10 badges) + Inbox (3 item kinds only: P-10 requests, run receipts, security events) | Conductor, Antigravity inbox |
| `19.4` `35L-0` | First-run auth (local-no-account vs team scoped token, no oracle on failure) + About & updates (version/channel, ed25519 signature state, SBOM link, no "trust anyway") | desktop-app norm + Keelway verification differentiator |

## Still open

1. **Light-theme token set** — app ships light mode; Paper tokens are dark-only. Next kit task.
2. **Chat thread as a first-class view** — `AgentComposer.tsx` exists in code; 19.2 defines its grammar. If it becomes a full view (not just composer+lane), needs its own rail entry — product decision.
3. **Billing tier count** — app 4 tiers vs website 5; still awaiting canonical decision.
4. **Diff-review full view** — 18.5 covers the drawer; a standalone review view (Devin-style side-by-side) is a candidate if usage justifies it.
5. **Wappalyzer exports** (`Downloads/build-fw/*.csv`) — reviewed; tech-stack fingerprints only, no design signal beyond the competitor set itself.

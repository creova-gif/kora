# Keelway Screen Inventory — Implemented × Designed × Needed

> KEEL-DSN-001 · 2026-11-22 · Source of truth for the Phase-2 design backlog and
> Phase-4 implementation mapping. Statuses: **shipped** (in `main`), **artboard**
> (Paper), **spec** (Paper interface-specs row only), **missing** (no design),
> **absent** (not implemented anywhere).

Legend: Paper file `01M7T488WTKN3AQNQ2K9DB40TN`. All views verified live on the
isolated verify-keelway stack 2026-11-22 (evidence `/tmp/keelway-qa-evidence/`).

## A. App shell & chrome

| Surface | Code | Backend | Paper | Gap / note | Phase |
|---|---|---|---|---|---|
| View rail + workspace bar + status bar (10 views) | `DevAppShell.tsx`, `PlatformWorkspaceBar.tsx` | `/v1/platform/*` hydration, `/v1/agent` | ✅ artboard 10.1 | Shell rules in Paper match shipped decongestion; verify pixel parity in P4 | 4 |
| Golden Thread journey breadcrumb | `GoldenThreadJourneyBar.tsx` | task/run state | ✅ implied by 10.1 journey chip | Artboard shows `JOURNEY: gate #1206 awaits you` — parity-check text format | 4 |
| Command palette | in-app (cmd-k) | mixed | ✅ 18.3 (`2RP-0`) | Designed — actions ranked, P-10 first | — |
| Onboarding modal (in-app, 2-step) | `App.tsx` + onboarding component | setup/doctor endpoints | ✅ 18.3 (`2RP-0`) | Designed — provenance markers kept | — |
| Review-changes drawer | `TasksDrawers.tsx` (`ReviewChangesContent`) | diff/keep-revert APIs | ✅ 18.5 (`2WD-0`) | Designed — keep/revert receipt note | — |
| Live execution drawer | `LiveExecutionDrawer.tsx` | SSE execution stream | ✅ 18.5 (`2WD-0`) | Designed — lens on the same ledger | — |
| Mobile companion mode | `App.tsx` (`companionTab`, `effectiveMobileCompanion`) | same | partial (page 08) | Responsive contract needed for workspace surfaces | 3 |

## B. IDE group (rail sections: tasks · files · record · settings)

| Screen | Code | Backend | Paper | Gap | Phase |
|---|---|---|---|---|---|
| Tasks — live agent run lane + P-10 card | `TasksWorkspace.tsx`, `P10ApprovalCard.tsx`, `AgentComposer.tsx` | `/v1/agent` tasks, P-10 approve/deny, SSE | ✅ 18.1 (`2O0-0`) | Designed — run lane + flight tape context | — |
| P-10 approval card — state family | `P10ApprovalCard.tsx` | P-10 gate API | ✅ 18.1 (`2O0-0`) | pending/approved/denied/expired artboarded; allow-once vs allow-always + edited variants fold into approve action copy | — |
| Files — tree + editor + tabs + footer | `FilesWorkspace.tsx`, `FilesExplorerSidebar.tsx`, `FilesDiffAndCommit.tsx` | `/v1/files/*` | ✅ artboard 12.1 | Compare detail (editor chrome, tab bar, footer contract) | 4 |
| Record — audit ledger + inspector + chain banner + Merkle expander | `RecordAuditLedger.tsx`, `RecordEntryInspector.tsx` | audit ledger, inclusion proofs | ✅ artboard 10.2 | Compare detail; keep `data-callout-variant` contract | 4 |
| Settings — overview + IA | `SettingsWorkspace.tsx` | mixed | ✅ 17.1 anatomy (`2AQ-0`) | Rail + panel grammar designed | — |
| Settings · Permissions (manifest table, kill-switch, grant rule) | `settings/SettingsPermissionsPanel.tsx` | `/v1/agents/registry`, toggle | ✅ 17.2 (`2CG-0`) | Designed | — |
| Settings · Models | `settings/SettingsModelsPanel.tsx` | model registry/BYOM | ✅ 17.4 (`2H0-0`) | Designed — local runtime, weights, connectors, 4D simulator | — |
| Settings · Governance (DLP, persistence, key verify) | `settings/SettingsGovernancePanel.tsx`, `SettingsKeyMintModal.tsx` | `/v1/governance/*` | ✅ 17.3 (`2EL-0`) incl. mint modal | Designed | — |
| Settings · Network | `settings/SettingsSystemPanels.tsx` | egress posture | ✅ 17.5 (`2JZ-0`) | Designed — posture, air-gap lock, SC-7 checklist | — |
| Settings · Appearance (theme/density/locale) | `settings/SettingsSystemPanels.tsx` | local prefs | ✅ 17.6 (`2LS-0`) | Designed — combined light-panels board | — |
| Settings · Labs | `settings/SettingsSystemPanels.tsx` | feature flags | ✅ 17.6 (`2LS-0`) | Designed — combined light-panels board | — |
| Settings · General | `settings/SettingsSystemPanels.tsx` | local prefs | ✅ 17.6 (`2LS-0`) | Designed — combined light-panels board | — |
| Settings · Keyboard (shortcuts) | `settings/SettingsSystemPanels.tsx` | local prefs | ✅ 17.6 (`2LS-0`) | Designed — combined light-panels board | — |

## C. Platform views (rail sections 2–10)

| Screen | Code | Backend | Paper | Gap | Phase |
|---|---|---|---|---|---|
| Agents — registry grid + lifecycle + run detail | `AgentsWorkspaceView.tsx` | `/v1/agents/*` | run detail ✅ 12.4; registry grid spec only | Registry list artboard needed | 2/4 |
| Project Manager — kanban/delegation board | `PmAndProductViews.tsx` | PM data | ✅ 18.4 (`2TC-0`) | Designed — lanes + delegated markers | — |
| Product — PRDs / roadmap | `PmAndProductViews.tsx` | product data | ✅ 18.4 (`2TC-0`) | Designed — combined board | — |
| Automation — KFlow DAGs, workflow runs, autopilot | `AutomationAndOpsViews.tsx`, `CyclicKflowAndAutopilotPanel.tsx`, `BidirectionalKflowStudioPanel.tsx` | `/v1/kflow`, autopilot | ✅ 18.4 (`2TC-0`) | Designed — DAG list + P-10-locked node | — |
| Marketplace — catalog, trust, install, publish, settlement | `MarketplaceAndDocsViews.tsx` | `/v1/marketplace/*` | ✅ artboard 12.5 | Compare detail (install/publish RBAC gates shipped SEC-065/066) | 4 |
| Security — permissions surface + safety mesh | `SecurityWorkspaceView.tsx`, `FormalSafetyAndEdgeMeshPanel.tsx`, `VaultAndWebhooksPanel.tsx` | vault, webhooks, safety | ✅ 18.4 (`2TC-0`) | Designed — posture/scan/chain rows | — |
| Documentation — docs browser | `DocumentationWorkspaceView.tsx` | docs index | ✅ 18.4 (`2TC-0`) | Designed — repo-docs list + search index | — |
| Operations — deployments, nodes, tape verify, settlement | `AutomationAndOpsViews.tsx` | ops/cluster APIs | ✅ artboard 12.2 | Compare detail | 4 |
| No-Code Builder — workflow canvas | `NoCodeBuilderView.tsx` | builder APIs | ✅ artboard 12.6 | Compare detail | 4 |

## D. Specialist panels (in-view, designed only if they outgrow current treatment)

`AgentCoharnessAndCiGatePanel`, `FlightTapeDebuggerPanel`,
`FlightTapeScrubberAndRadar`, `GoldenEvalScorecardPanel`, `KBrainMemoryGraphPanel`,
`KHubAirgapMirrorPanel`, `KSpacesCrdtAndKflowPanel`, `LangGraphMigratorPanel`,
`McpInspectorPanel`, `McpLockfileAndBenchPanel`, `QuotaAndPricingSimulatorPanel`,
`ShadowCacheAndDistillationPanel`, `SiemAndObservabilityPanel`,
`StepDebuggerAndBridgePanel`, `StructuredOutputAndSelfHealingPanel`,
`EnterpriseIdentityAndQuorumPanel`, `CycloneDxSbomPanel` — all shipped, all
spec-only or absent in Paper. Phase-2 batch: artboard the parent view first;
panels inherit the section template unless individually flagged.

## E. Missing / net-new surfaces

| Surface | Status | Notes | Phase |
|---|---|---|---|
| Billing / tier management | partial (workspace-bar tier switcher only) | ✅ 18.2 (`2PV-0`) — plan/usage/settlement designed. Open: 4-tier (app) vs 5-tier (website) canonical set resolution | — |
| State matrix — every view × {empty, loading, error, offline, denied, P-10-pending} | ✅ 18.4 (`2TC-0`) — cross-view render contract designed (empty/loading/error/offline/denied/P-10-pending × never-rules) | — |
| Responsive contract — workspace at <1024px | mobile companion exists, undocumented | Define which views collapse to companion vs stay desktop-only | 3 |
| Auth/sign-in inside app context | magic-link stub on website only | App is token-gated today; design the in-app auth surface if it ships | 3+ |
| Dashboard/home inside app | absent | Is there a "home" beyond the 10 views? Open question for Phase-2 IA pass | 2 |

## F. Marketing surfaces (parity check only — already both-sided)

Website v3 routes (`/`, `/about`, `/product`, `/pricing`, `/changelog`,
`/contact`, `/sign-in`, 404) shipped and artboarded on Paper pages 01/03/09.
Phase 4 includes a parity sweep against the live deployment
(`kora-sable.vercel.app`), not a redesign.

## Phase-2 design queue (owner-approved order)

**Phase 2 coverage: complete.** Every shipped screen is artboarded: page 17 Settings (`17.1`–`17.6`), page 18 Missing Surfaces (`18.1` P-10 + run lane, `18.2` billing, `18.3` overlays, `18.4` remaining views + state matrix, `18.5` drawers). Remaining:

1. **4-tier vs 5-tier billing canonical set** — decision needed before implementation
2. **Agents registry grid** — run detail covered (12.4); list artboard optional

## Page 19 — Desktop Completeness additions (KEEL-DSN-003)

| Surface | Component | Artboard | Status |
|---|---|---|---|
| Component primitives spec | all `dev-app` controls | `19.1` (`322-0`) | designed |
| Agent composer deep-dive | `AgentComposer.tsx` | `19.2` (`35J-0`) | designed — pending impl review |
| Workspace switcher + Inbox | `PlatformWorkspaceBar.tsx` + new inbox surface | `19.3` (`35K-0`) | designed — new surface |
| App auth + About & updates | new surfaces | `19.4` (`35L-0`) | designed — new surface |


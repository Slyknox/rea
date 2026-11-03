# MASTER PROMPT: FLUID-FUND SAAS PLATFORM BUILD

Paste everything below the line into Claude Code (Fable 5.1 orchestrating, Opus 5.5 executing, Duet pairing). It is the single source of truth for the build. Nothing outside it is in scope.

---

## 1. ROLE

You are the **Principal FinTech Architect and Systems Engineer** for **Fluid-Fund**, an autonomous business-financing and alternative-funding orchestration platform. You run a virtual organization of 40+ senior executive engineers and marketers, each with 40+ years of experience, grouped into pods. You delegate, integrate, and sign off. You never ship a pod's work unreviewed.

**Model roles**

| Model | Role |
|---|---|
| Claude Fable 5.1 | Orchestrator. Owns architecture, delegation, integration, and sign-off. |
| Claude Opus 5.5 | Pod execution. Writes code, schemas, tests, docs, and marketing assets. |
| Claude Duet | Paired review. The checker is never the maker. Every artifact passes a Duet review before merge. |

**Tooling in the repository**

- `Slyknox/rea` (REA, Reverse Engineer Anything MCP): behavioral and runtime analysis of competitor workflows during R&D. Use it only on software you are licensed to run. Never bypass authentication, rate limits, or terms of service.
- `Slyknox/gstack`: the build loop. Use `/autoplan` for the plan review, `/plan-eng-review` for architecture, `/review` on every diff, `/qa` on every UI surface, and `/ship` for each layer's pull request.

## 2. NON-NEGOTIABLES

1. **Zero drift.** Build only what this prompt specifies. No new features, libraries, or patterns.
2. **Zero fluff.** No placeholder comments, no `// implement here`, no truncated code blocks, no summaries in place of code.
3. **Zero hallucination.** Every API, library version, and regulation you cite must exist. When a requirement is ambiguous, write the assumption into `docs/ASSUMPTIONS.md` and proceed with the most conservative reading. Stop and ask only when every reading would produce unsafe or useless work.
4. **Sequential layering.** Layer N is complete, tested, and merged before Layer N+1 starts. No code clashes between layers.
5. **Source of truth.** `CLAUDE.md` at the repository root holds the architecture, conventions, and decisions. Every pod reads it first and updates it when a durable decision is made. Prior artifacts win over new ideas; the most recent production-ready version wins a conflict.
6. **Legal floor.** Fluid-Fund is not a consumer reporting agency. No product surface may claim credit decisions, criminal records, or identity verification it does not perform. Use only documented APIs with terms that allow commercial automated use. Public registries are read through official APIs or bulk data files, never scraped against their terms. Log every underwriting decision with the inputs that produced it (ECOA and Reg B adverse-action readiness).
7. **Maker is never checker.** Every pod's deliverable is reviewed by a different pod or by Duet before integration.

## 3. ARCHITECTURE: EIGHT STACKED MOAT LAYERS

Build in this order. Each layer names the competitor it re-engineers and the feature it must match or exceed.

| # | Layer | Re-engineers | Core capability |
|---|---|---|---|
| 1 | Data Verification | Middesk, Unit | Omni-source KYC/KYB ingestion, self-healing diagnostic error logs |
| 2 | Ledger Security and Auditing | LoanPro | Double-entry bookkeeping, cryptographically chained compliance log |
| 3 | Multi-Lender Rule Routing | FundedCommon | Dynamic lender underwriting matrix, autonomous risk-shift tracking |
| 4 | Flexible Revolving Asset Core | Peach Finance | Adaptive credit-line configuration, 0% APR stacking logic |
| 5 | Captive Agnostic Cash-Flow Marketplace | Lendflow, Stripe Capital, Shopify Capital, Bluevine, Parafin | Plaid and Stripe webhooks, gateway-agnostic capital arbitrage |
| 6 | Crowdsourced Human-in-the-Loop Network | Deltek GovWin IQ | Broker-sourced telemetry, verified underwriting exceptions |
| 7 | Agnostic Embedded Native Workflow Wrapper | TechnoMile | Modular API distribution into Salesforce, HubSpot, Zoho, and custom CRMs |
| 8 | Autonomous Financial Ontology Engine | Palantir Foundry | Self-service semantic graph, node and edge mapping, real-time ontology score |

**Runtime agent triad** (native Node.js and TypeScript, event-driven):

- **Scout**: registry auditor and mismatch detector (Secretary of State, USPS address validation, business directory records).
- **Guardian**: compliance-certainty enforcer and remedy generator.
- **Healer**: capital-arbitrage underwriter and multi-lender optimizer.

## 4. TECH STACK (FIXED)

- **Frontend**: Next.js 14 App Router, TypeScript, Tailwind CSS, shadcn/ui, dark theme by default.
- **Backend and data**: Supabase PostgreSQL, strict multi-tenant Row-Level Security on every table, migrations in `supabase/migrations/`.
- **Agent engine**: Node.js and TypeScript event-driven multi-agent framework in `lib/agents/`.
- **Integrations**: Plaid, Stripe, Stripe Connect, QuickBooks, Shopify, Adyen. Every webhook is signature-verified and idempotent.
- **Testing**: Jest with TypeScript. Every module ships with unit tests; every API route ships with an integration test.
- **Deployment**: multi-stage `Dockerfile`, `docker-compose.prod.yml`, Nginx reverse proxy, Let's Encrypt TLS, GitHub Actions CI.
- **Security**: edge token-bucket rate limiting, RLS isolation, cryptographic audit chain, secrets only through `process.env`, `.env.example` kept current.

## 5. ORGANIZATION AND DELEGATION

Three divisions, nine pods, 58 seats. Each pod lead reports to you and owns their deliverables end to end.

### Division A: Research and Development

**Pod 1: REA Recon and Behavioral Mapping** (lead plus 6)
Mandate: use REA to map Credit Suite's Business Credit Builder, fundability checklist logic, and tier-unlock conditions; map every competitor in Section 3 to a feature-parity matrix.
Deliverables:
- `docs/research/feature-parity-matrix.md` (all competitors against Fluid-Fund, cell by cell)
- `docs/research/credit-suite-tier-state-machine.md` (7-step tier progression as a state machine with transition guards)
- `docs/research/moat-weakness-analysis.md` (where each competitor's moat is thin and how Fluid-Fund displaces it)
- `docs/research/agent-triad-requirements.md` (technical requirements for Scout, Guardian, Healer)

### Division B: Software Development

**Pod 2: Self-Healing Compliance Engine** (lead plus 8) — Layers 1 and 2
Deliverables: `lib/compliance/EinComplianceEngine.ts`, `lib/agents/FluidAgentCoordinator.ts`, Scout and Guardian agents, `POST /api/compliance/audit`, integration tests, remedy payload schema in `docs/schemas/remedy-payload.md`.

**Pod 3: Gateway-Agnostic Underwriting Matrix** (lead plus 8) — Layers 3 and 4
Deliverables: `lib/underwriting/GatewayAgnosticUnderwriter.ts`, `lib/agents/HealerOptimizer.ts`, `lender_risk_matrix` DDL with RLS, 0% APR stacking optimizer with a documented scoring formula, `POST /api/underwrite`, Jest coverage of every routing branch.

**Pod 4: White-Label Multi-Tenant Platform** (lead plus 6) — Layer 7
Deliverables: `tenant_tenants` DDL with RLS, `middleware.ts` for subdomain and custom-domain routing, `app/[tenant]/TenantWorkspacePage.tsx` with dynamic branding, `lib/integrations/crmWrapper.ts` (Salesforce, HubSpot, Zoho, custom adapter interface), `docs/broker-onboarding.md`.

**Pod 5: Data Ingestion and Webhook Pipeline** (lead plus 6) — Layer 5
Deliverables: `app/api/webhooks/plaid/route.ts`, `app/api/webhooks/stripe/route.ts`, `cash_flow_ledgers` DDL, normalization pipeline in `lib/ingestion/`, replay-safe idempotency keys, `docs/data-normalization.md`.

**Pod 6: Frontend Command Center and UX** (lead plus 6)
Deliverables: `components/FluidFundCommandCenter.tsx` (compliance meters, funding allocation cards, live agent log stream), `components/OntologyGraphDashboard.tsx`, `components/AdminRealTimeHUD.tsx`, shared component library, `docs/ux-flows.md`. Every surface passes `/qa` and `/design-review`.

**Pod 7: QA, Settlement, and Security** (lead plus 6)
Deliverables: `__tests__/engine.test.ts` and the full Jest matrix, `lib/billing/StripeSplitEngine.ts` (Stripe Connect commission splits), `lib/security/RateLimiter.ts`, `Dockerfile`, `docker-compose.prod.yml`, `nginx.conf`, `deploy.sh`, `.github/workflows/ci.yml`, `.env.example`.

**Pod 8: Financial Ontology and Enrichment** (lead plus 6) — Layers 6 and 8
Deliverables: `lib/ontology/FinancialOntologyEngine.ts`, `lib/ontology/EnrichedOntologyEngine.ts`, `lib/ontology/OntologyCoordinator.ts`, DDL for `ontology_nodes`, `ontology_edges`, `analyst_telemetry_ledger`, `crm_wrapper_connections` with RLS, `app/api/ontology/stream/route.ts` (Server-Sent Events).

### Division C: Marketing and Growth

**Pod 9: Go-to-Market** (lead plus 6)
Targets: business-credit consultants, funding brokers, CPA firms, B2B service agencies.
Deliverables in `marketing/`:
- `landing-page.md` (hero, features, pricing, CTA for fluidfund.com)
- `pitch-deck.md` (10 to 12 slides: problem, market sizing with cited sources, moat analysis, financial projections with stated assumptions)
- `content-strategy.md` (10 blog outlines on business credit stacking, fundability, and SBA alternatives)
- `partner-playbook.md` (white-label outreach templates and commission structure)
- `seo-keywords.md` (high-intent fintech queries, grouped by funnel stage)
- `enterprise-angles.md` (GovCon and ontology-driven data-moat positioning)
Every claim is verifiable. No invented testimonials, usage numbers, or guarantees.

## 6. EXECUTION PROTOCOL

1. **Bootstrap.** Create `CLAUDE.md` with Sections 2 through 4 of this prompt, the repository map, and the test and deploy commands. Create `docs/ASSUMPTIONS.md`.
2. **Pod 1 first.** Research artifacts land before any code. Every later pod cites them.
3. **One layer per branch.** Branch `layer/<n>-<name>`. Run `/autoplan` on the plan, `/plan-eng-review` on the design, build, `/review` the diff, `/qa` any UI, `/ship` the PR. Merge only green.
4. **Definition of done for every file.** Compiles under strict TypeScript, has tests that pass, is referenced from `CLAUDE.md` or a doc, has no placeholders, and has been reviewed by a pod other than its author.
5. **Commits.** One logical change per commit. Schema separate from code, code separate from tests, tests separate from docs.
6. **Integration.** After each layer, run the full Jest matrix, the Docker build, and a smoke test against `docker-compose.prod.yml`. Record the result in `docs/LAYER_LOG.md`.
7. **Marketing runs in parallel** with Layers 5 through 8 and is reviewed against the shipped product, not the plan.

## 7. FINAL DELIVERABLE MANIFEST

1. SQL DDL for `core_profiles`, `compliance_ledger`, `cash_flow_ledgers`, `funding_allocation_engine`, `lender_risk_matrix`, `tenant_tenants`, `compliance_certainty_logs`, `ontology_nodes`, `ontology_edges`, `analyst_telemetry_ledger`, `crm_wrapper_connections`, each with RLS policies and indices.
2. TypeScript modules: `EinComplianceEngine`, `FluidAgentCoordinator`, `GatewayAgnosticUnderwriter`, `HealerOptimizer`, `FinancialOntologyEngine`, `EnrichedOntologyEngine`, `OntologyCoordinator`, `StripeSplitEngine`, `RateLimiter`.
3. API routes: Plaid webhook, Stripe webhook, compliance audit, underwriting evaluation, ontology SSE stream.
4. React components: `FluidFundCommandCenter`, `TenantWorkspacePage`, `AdminRealTimeHUD`, `OntologyGraphDashboard`.
5. Jest suite with passing CI.
6. Deployment: `Dockerfile`, `docker-compose.prod.yml`, `nginx.conf`, `deploy.sh`, `.env.example`, GitHub Actions workflow.
7. Marketing kit (Section 5, Pod 9).
8. `docs/DEPLOYMENT.md`: step-by-step Supabase, Docker, and Stripe setup.
9. `docs/LAYER_LOG.md`: per-layer test, build, and review receipts.

## 8. FINAL DIRECTIVE

Begin with the bootstrap, then Pod 1. Proceed through Layers 1 to 8 in order, merging each only when green and reviewed. Deliver the marketing kit alongside Layers 5 through 8. Report completion only when every item in Section 7 exists in the repository, passes its tests, and is logged.

Zero drift. Zero fluff. Zero hallucination.

# Fluid-Fund: Q1 2027 Capital Operating System

**Status:** design document, v1 (November 2026)
**Owner:** Michael Mercado (Fluid-Fund / Fundamentals)
**Purpose:** define what Fluid-Fund becomes by Q1 2027 if it absorbs the best of
Credit Suite Fundability, Lendavo, ROK Financial and Business Wealth Warriors,
and then goes past them with a data-connected scoring engine, a lender and
vendor knowledge graph, and an autonomous inbound + outbound lead-generation
operating system with a native CRM.

This document is written as if a 40+ person senior team (engineering, data
science, advisors, investors, marketing, operations) were delegated the build.
Section 8 is the delegation plan. Section 9 is the sprint plan to Q1 2027.

> Why this lives in the `rea` fork: REA ("Reverse Engineer Anything") is the
> tool we use to study how the competitor web apps are built from the outside
> (feature inventory, data model, API shapes, UX flows) on accounts we own.
> Section 12 describes that workflow and its limits.

---

## 1. Executive summary

Every competitor sells one third of the problem:

| Platform | What it really is | What it sells | What it lacks |
|---|---|---|---|
| **Credit Suite Fundability** (fundability.creditsuite.com / fundability.com) | A guided 7-step business-credit builder with a 0 to 890 Fundability Score, tri-bureau monitoring, filtered vendor matching and a funding explorer | $2,997 one-time or $497 x 8 through a "free strategy call" | Data is typed in by hand, no autonomous fixing, no revenue engine for the member, sales gated behind a phone call |
| **Lendavo** (Credit Suite's newer product) | Same engine plus Funding Ready Score (0 to 200), SBA Readiness Score, 1,000+ lender matching, approval probability, doc vault, Mentor AI, AI Marketer, cashflow and valuation | $2,997 or $497 x 7, coaching upsell | Still a dashboard the owner works; the "AI" is advisory, not operational; matches are not live underwriting |
| **ROK Financial** (rok.biz) | A business-loan broker marketplace: 15-second pre-approval form, six product lines ($10K to $5M, 1 to 45 day funding), human Business Financing Advisors, SEO blog engine | Commission from lenders, lead goes to a human | No credit building, no self-serve path, no readiness feedback; if you do not qualify today the relationship ends |
| **Business Wealth Warriors** (members.businesswealthwarriors.com) | A $1 trial / $29 per month community on the "5 Cs" (Credibility, Capital, Connection, Conversion, Compounding): the Dojo (courses), War Room (weekly hot-seats), Round Table (daily peer support), 9+ courses, 50+ ebooks, 11,000+ members | Recurring membership, upsell into Lendavo | Content is disconnected from the member's data; no score, no funding, no CRM; generic "founding member" scarcity copy |

**Fluid-Fund's thesis:** one platform where the member's business is modelled as
a live **Fundability Graph** (every fact a lender weighs, sourced from APIs not
typed in), scored by a **calibrated, explainable Fundability Score** (trained on
real approval outcomes, not a static rubric), repaired by **autonomous agents**
(that fix red items, open vendor accounts, and submit applications with
consent), funded through a **lender and vendor marketplace with live
underwriting boxes**, and grown through a **Revenue OS** (autonomous lead-gen +
CRM) that the member uses for their own business and that Fluid-Fund uses to
acquire members.

"100x better" is integration: the four products become one object model.
"1000x better" is autonomy plus data: the system does the work, measures the
outcome, and gets smarter from every application it submits.

---

## 2. How each competitor operates (teardown)

### 2.1 Credit Suite Fundability

Observed from the live dashboard (screenshot, Nov 2026) and the public feature
pages.

**Information architecture**

- Left nav: Business Fundability (Foundation, Financials, Business Credit
  Builder, Personal, Application Process), Business Funding, Funding Manager,
  Bureau Insights, Resource Market.
- Business Credit Builder is a 7-step linear track with a progress bar (1/7 to
  7/7): 1 Fundability Foundation, 2 Bureau Profile Verification, 3 Start
  Building: Tier 1, 4 Monitor Business Reports, 5 Building Credit: Tier 2,
  6 Advanced Building: Tier 3, 7 Revolving Accounts: Tier 4.
- Step 1 checklist (the "Foundation"): Business Address, Business Entity,
  Foreign Filing, Ownership, EIN, Business Phone, Website and Email, Business
  Licenses, Business Bank Account, Merchant Account, Business Industry, Time in
  Business (plus NAICS, 411 listing and name-consistency checks on the public
  page).
- Right rail: Fundability Score gauge (0 to 890), Approved Funding ($), Revenue
  vs Funding (%), Trade Vendor Distribution per bureau (D&B, Equifax,
  Experian, "0 of 3 completed" each).

**Scoring model (public description)**

- Five categories feed one number: Foundation, Financials, Business Credit
  Reports (D&B, Experian, Equifax + reporting accounts), Personal Credit (FICO,
  bankruptcies, liens, judgments), Application Process ("right accounts in the
  right order").
- Items are colour-coded green / yellow / red / grey; clicking a red item deep
  links to the fix screen.
- Stage thresholds: 0 to 400 Foundation, 400 to 600 Building, 600 to 750
  Established, 750 to 890 Premium. Funding programs "unlock" in Funding
  Explorer at thresholds.
- Score moves as the member completes steps (their example: 380 to 680 after
  fixing address, adding EIN, verifying D&B, opening six Tier 1 vendors and
  resolving a bureau fraud flag).

**Trade Vendor Match**

- Vendor cards carry badges: reports to D&B / Experian / Equifax, PG or no-PG,
  "approves my profile". Filters: bureau, no-PG, reporting-only.
- The core teaching: three reporting accounts at each of three bureaus beats
  eight at D&B alone, because the lender may pull Equifax Commercial.
- Applications flow into Funding Manager (tracker).

**Go-to-market**

- Every CTA is "Book a Strategy Call, 30 minutes, free". Price is revealed on
  the call ($2,997 one-time or 8 x $497 reported by third parties).
- Content: large blog, "Funding Readiness Checklist", newsletter with a 3-part
  Fundability training as the lead magnet, Fundability Assessment quiz.
- Partner / affiliate / white-label program (Lendavo Partner Login).

**What to take:** the 7-step sequence, the five-category score with item-level
colour status and one-click fix path, bureau-balanced vendor matching with PG
flags, the Funding Manager tracker, the free assessment as lead magnet.

**Cons to beat:** manual data entry; score rubric is opaque and not calibrated
to outcomes; vendor list freshness is a stated problem for the whole industry;
nothing is done for the member; price hidden behind a call; monitoring is a
reseller of bureau feeds.

### 2.2 Lendavo (Credit Suite's "Capital Intelligence System")

**Feature inventory (from the pricing page)**

- Business Health: dashboard, Business Details (EIN, DUNS, NAICS, legal
  address, phone, stored once to kill mismatch denials), revenue and expense
  tracking, cashflow projections, business valuation, 4 business credit scores
  and reports (D&B PAYDEX, Experian Intelliscore Plus, Equifax Delinquency,
  CreditSafe), 2 consumer scores (TransUnion and Experian VantageScore 3.0).
- Business Credit Building: Funding Ready Score (0 to 200, "same criteria
  lenders use": verification, credit strength, time in business, banking
  behaviour, industry risk, credibility), Business Credit Accelerator,
  dynamic Credit Building Recommendations, Business Credit Mentor AI, Business
  Credit Milestones (approved accounts, total credit, tier progression), Smart
  Credit Matches (credit type Net 30 / Net 60 / revolving, issuer, bureaus,
  requirements, apply link).
- Business Funding: SBA Readiness Score (profitability, revenue consistency,
  credit, time in business, collateral, tax history), Get Capital Dashboard,
  New Funding Opportunities feed (unlocks as profile improves), FundSmart AI
  Matches across 1,000+ lenders, Approval Probability Analysis, Document Vault,
  Finance Specialists.
- Growth: AI Marketer (brand, audience, 12-month content, promo and ad
  calendars, knowledgebase), Business Wealth Warriors bundled.
- Pricing: 7 x $497 or $2,997 one payment, concierge coaching add-on, unlimited
  coaching in business hours.

**What to take:** the two-score split (credit readiness vs SBA/bank readiness),
the opportunity feed that unlocks on profile change, approval probability as a
first-class number, the single Business Details record of truth, the doc vault
that is ready before underwriting, a Mentor agent grounded on the member's own
data.

**Cons to beat:** scores are rules, not models; "1,000+ lenders" is a directory,
not live boxes; the member still applies by hand; AI Marketer produces a plan,
not a pipeline; coaching is the real product and does not scale.

### 2.3 ROK Financial

**Funnel**

- Home hero: 3 fields (Amount Requested, Time in Business, Credit Score band)
  with "instant pre-approval". Slider "How much could I qualify for?" ($10K
  monthly sales shows $17K, illustration only).
- Apply Now: name, business name, email, business phone, mobile phone, industry
  (110+ option list, used for risk-tier routing), credit band, time in business,
  annual sales band, product interest (11 options including "Unsure, please
  advise"), website yes/no, and an explicit consent checkbox for SMS, email and
  phone. Submission pairs the lead with a Business Financing Advisor.
- Minimum qualification stated up front: 6 months in business, $10K+ monthly
  sales, 500 credit score.

**Products and promises**

| Product | Range | Term | Funding time |
|---|---|---|---|
| Term loans + working capital | $10K to $5M | 6 months to 10 years | 1 to 3 days |
| Business line of credit | $10K to $5M | 6 months to 10 years | 1 to 3 days |
| SBA | $10K to $5M | 10 to 25 years | 30 to 45 days |
| Equipment financing | $10K to $5M | 1 to 6 years | 2 to 5 days |
| AR + PO financing | $100K+ aged to 90 days | revolving | 2 to 5 days |
| Commercial real estate | $250K to $10M | 10 to 30 years | 25 to 40 days |

**Trust and content**

- Trustpilot, Google, Best Company badges, BBB, SBFA, Inc 5000, "25,000+
  customers", association logos (AACFB, IFA, National Restaurant Association,
  NEFA).
- Daily SEO blog: product x industry long-tail ("Restaurant Equipment
  Financing", "Business Line of Credit EIN Only", calculators). This is a
  programmatic content engine feeding the pre-approval form.

**What to take:** the 15-second pre-qual, explicit qualification floor, the
product matrix with honest ranges and funding times, product x industry
content at scale, advisor pairing with consent captured at the form.

**Cons to beat:** no path for the 60%+ who do not meet the floor today (they
become dead leads instead of a 90-day readiness program); humans do the
matching; no visibility into which lender boxes the lead fits; no credit
building; no ongoing relationship after funding.

### 2.4 Business Wealth Warriors

**Model**

- Entry: $1 for 14 days, then $29 per month ("regularly $47"), "next 100
  founding members" scarcity, 90-day Measurable Progress Guarantee.
- Three rooms: Dojo (execution lab, courses, templates, AI tools), War Room
  (weekly live strategy and hot seats), Round Table (daily peer and expert
  Q&A).
- Library: 9+ courses (funding, startups, investors, crowdfunding, P2P, grants,
  30+ financing options, "$250K in business credit"), 9+ masterclasses (be your
  own bank, buy a business with creative financing, sell your company, grants,
  personal brand), 5+ training series, 50+ ebooks (industry-specific funding
  guides: truckers, real estate agents, restaurateurs).
- The 5 Cs framework: Credibility, Capital, Connection, Conversion, Compounding.
- 11,000+ members, "trusted by 60,000+ businesses" (Credit Suite's customer
  base).

**What to take:** the three-room structure (learn / plan / ask), the 5 Cs as the
member's journey map, the low-ticket recurring entry that feeds the high-ticket
system, industry-specific playbooks, a progress guarantee.

**Cons to beat:** content is static and unlinked to the member's score; the
community is a WordPress membership, not a product; scarcity and "founding
member" copy that cannot be verified (Fluid-Fund's marketing standard is
"honest marketing" as already set in the TRUVO360 canon: no unverifiable
claims, no fake scarcity).

---

## 3. The Fluid-Fund product thesis

Fluid-Fund is a **Capital Operating System** with four coupled engines on one
object model:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                           FLUID-FUND MEMBER                             │
│                                                                         │
│   ┌──────────────┐   ┌──────────────┐   ┌──────────────┐  ┌──────────┐ │
│   │ CREDIBILITY  │──▶│   CAPITAL    │──▶│   GROWTH     │─▶│ COMPOUND │ │
│   │ Fundability  │   │ Marketplace  │   │ Revenue OS   │  │ Portfolio│ │
│   │ Graph+Score  │   │ + One-click  │   │ (lead-gen +  │  │ + Equity │ │
│   │ + Auto-fix   │   │   apply      │   │  CRM)        │  │          │ │
│   └──────┬───────┘   └──────┬───────┘   └──────┬───────┘  └────┬─────┘ │
│          └──────────────────┴──────────────────┴───────────────┘       │
│                       Shared object model + agent runtime               │
└─────────────────────────────────────────────────────────────────────────┘
                                   ▲
            The same Revenue OS, pointed outward, acquires members.
```

Three design laws:

1. **Nothing is typed twice.** Every Foundation fact has a source of truth API
   (Secretary of State, IRS EIN match, D&B, Google Business Profile, domain
   DNS/MX, Plaid, bureau). The member confirms; the system fetches.
2. **Every number is explainable and calibrated.** The score is a model whose
   factor contributions are shown per item, and whose stage thresholds are
   recalibrated monthly against actual approvals and declines flowing through
   the marketplace.
3. **Agents do, humans approve.** Fixes, vendor applications, lender
   submissions and outreach are executed by agents under explicit consent
   scopes, with a human gate wherever money, credit pulls or legal consent is
   involved.

---

## 4. Architecture

### 4.1 Planes

```
┌────────────────────────────── CONTROL & COMPLIANCE PLANE ──────────────────────────────┐
│ Consent ledger · Policy engine (TCPA/CAN-SPAM/DNC/ECOA/FCRA/state CFDL) · Audit log     │
│ Feature flags · Human-approval gates · Observability (Sentry, PostHog) · Cost router     │
└──────────────────────────────────────────────────────────────────────────────────────────┘
┌──────────────── PRODUCT SURFACES ────────────────┐  ┌──────────── REVENUE OS ───────────────┐
│ Web app (Next.js 15) · Mobile (Expo) · Partner    │  │ Prospecting · Enrichment · Sequencing │
│ white-label · Public widgets · Mentor chat · MCP  │  │ Omnichannel inbox · Voice/chat SDR    │
│ server (so members' own agents can act)          │  │ Native CRM · Attribution · Payouts    │
└──────────────────────────────────────────────────┘  └───────────────────────────────────────┘
┌──────────────────────────────── INTELLIGENCE PLANE ─────────────────────────────────────┐
│ Fundability Score 2.0 (calibrated) · SBA/Bank Readiness · Approval Probability per box   │
│ Vendor & Lender Knowledge Graph · Recommendation engine · Mentor agent · Agent relay      │
└──────────────────────────────────────────────────────────────────────────────────────────┘
┌──────────────────────────────────── DATA PLANE ─────────────────────────────────────────┐
│ Postgres (Supabase, RLS, pgvector) · Event store (append-only) · Object storage (vault)  │
│ Redis (Upstash) · Queue (QStash) · Connectors: SoS, Middesk, D&B, Experian, Equifax,     │
│ CreditSafe, Plaid, QuickBooks/Xero, Google Business, DNS/MX, 411, Stripe, Twilio, Resend │
└──────────────────────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Stack (chosen to match the team's existing fluency)

| Layer | Choice | Reason |
|---|---|---|
| App | Next.js 15 App Router, React 19, TypeScript | Same as KMOS and TRUVO360; one hiring profile |
| Data | Supabase Postgres with RLS, pgvector, Realtime, Storage | Multi-tenant by row, vector search for the knowledge graph and Mentor |
| Jobs | Upstash QStash + Redis, Vercel cron, n8n for long-running ops | Proven in KMOS agent relay |
| AI | Anthropic Claude (Opus for synthesis and underwriting narratives, Sonnet for scoring explanations and copy, Haiku for classification at volume) through one cost-routed call path | Every call logged to a cost table |
| Payments | Stripe (subscriptions, Connect for partner payouts) | |
| Comms | Twilio (SMS, voice), Resend (email), a warmed multi-domain sending pool for outbound | |
| Observability | Sentry, PostHog, OpenTelemetry traces per agent run | |
| Infra | Vercel + Supabase, Docker image for self-host or acquirer separation | |

**Entity rule:** Fluid-Fund is its own repo, its own Supabase project, its own
npm-only dependencies. No imports from KMOS, TRUVO360, RelayOS or any other
Fundamentals entity (the same M&A separability rule KMOS enforces). Shared
vendors are fine; shared code is not.

### 4.3 Object model (the thing the four competitors never unify)

```
Tenant (agency / partner / Fluid-Fund itself)
 └─ Workspace (one per member business)
     ├─ Business            legal name, DBA, entity type, EIN(hash), DUNS, NAICS, SoS id, formation date
     ├─ Owner[]             person, ownership %, consent scopes, consumer-credit authorisation
     ├─ FoundationItem[]    kind (address, entity, EIN, phone, web, email, license, bank, merchant, 411, GBP…)
     │                      status (green/yellow/red/grey), source, evidence, last_verified_at, fix_plan
     ├─ Financials          Plaid accounts, balances (daily), revenue series, NSF events, accounting sync
     ├─ CreditFile[]        bureau (D&B, Experian, Equifax, CreditSafe, SBFE-aware), score, tradelines[]
     ├─ Tradeline[]         vendor/issuer, bureau, opened_at, limit, balance, reporting_confirmed_at
     ├─ FundabilityScore    value 0..1000, stage, factor contributions[], model_version, computed_at
     ├─ Readiness           sba_readiness, bank_readiness, revenue_lending_readiness
     ├─ Opportunity[]       vendor | card | line | term | SBA | equipment | AR/PO | CRE; box_id; p_approve; status
     ├─ Application[]       opportunity, submitted_by (member|agent), packet, lender decision, terms, funded_at
     ├─ Document[]          vault: tax returns, statements, P&L, IDs; hashed, versioned, expiring share links
     ├─ Plan                12-week roadmap generated from the graph; tasks with owner (member|agent)
     └─ Membership          tier, community role, coaching entitlements
Catalog (global)
 ├─ Vendor[]               criteria, bureaus_reported (verified by tradeline appearance), PG?, apply_method
 ├─ Lender[] / Box[]       product, min TIB, min revenue, min FICO, industries excluded, max amount, speed,
 │                         docs required, submission channel (API | portal | email), commission schedule
 └─ OutcomeEvent[]         every decision (approve/decline/terms) → training data for calibration
Revenue OS
 ├─ Prospect → Lead → Contact → Deal (funding deal or membership deal) → Account
 ├─ Sequence, Message, Conversation (omnichannel), Task, Meeting, Attribution
 └─ ConsentRecord          channel, basis, captured_at, evidence (form snapshot, call recording id)
```

---

## 5. Core modules (what "100x" means, module by module)

### 5.1 Fundability Graph and Auto-Foundation

Credit Suite makes the member tick twelve boxes. Fluid-Fund verifies them.

| Foundation item | Source of truth (API) | Auto-fix the agent can run (with consent) |
|---|---|---|
| Entity, status, formation date, registered agent | State SoS APIs via Middesk (or direct state feeds) | File annual report reminder; flag "not in good standing" with the exact filing |
| EIN match | IRS TIN match via Middesk | Request EIN letter upload to vault |
| Business address (commercial vs residential vs CMRA) | USPS CASS + Middesk address intelligence | Recommend and provision a compliant virtual office; update SoS, GBP, bureaus |
| Business phone (listed, toll-free, carrier type) | Twilio Lookup + 411 listing check | Provision number, submit 411 listing, forward to mobile |
| Website and email | DNS/MX/SPF/DKIM, SSL, domain age | Set up domain email, SPF/DKIM, basic site if absent |
| Licenses | State and municipal license datasets, NAICS-driven requirement map | Checklist with filing links; track expiry |
| Bank account and merchant account | Plaid (institution, account age, balances, NSFs) + Stripe/merchant detection | Bank-balance coaching; merchant account referral |
| Google Business Profile | GBP API | Create or claim, sync NAP consistency |
| NAP consistency across all records | Diff engine across SoS, GBP, bureaus, website | One-click propagate corrections |
| D-U-N-S, Experian BIN, Equifax ID | Bureau APIs | Request DUNS; submit profile updates |

Every item carries **evidence** (the API response snapshot) so a member or
lender can see why it is green.

### 5.2 Fundability Score 2.0 (0 to 1000, explainable, calibrated)

- **Inputs:** the same five categories as Credit Suite (Foundation, Financials,
  Business Credit, Personal Credit, Application History) plus banking behaviour
  (average daily balance, deposits, NSFs), industry risk (NAICS), and
  consistency score.
- **Model:** a gradient-boosted or monotonic-constrained model trained on
  OutcomeEvents (approve / decline / terms) from the marketplace, initialised
  from lender-published boxes until outcome volume exists. Factor
  contributions (SHAP-style) are rendered per item: "Business phone not listed
  in 411: minus 18 points. Fix in 4 minutes."
- **Stages:** published as score bands tied to live boxes, not a fixed rubric:
  a band is "Established" when 70%+ of term-loan boxes in the catalog accept
  that profile.
- **Two readiness scores** (from Lendavo) kept distinct: Credit Readiness
  (vendor and card tiers) and Bank/SBA Readiness (profitability, tax history,
  collateral, DSCR).
- **Approval Probability per opportunity**, not per member: p(approve | box,
  graph). Shown as a range with the three strongest reasons.
- **Projection:** "If you open 3 Experian-reporting Tier 1 accounts and keep
  ADB above $4,000 for 60 days, projected score 712 by 15 Jan, unlocking 11 new
  boxes." The 12-week Plan is generated from this projection.

### 5.3 Vendor and Lender Knowledge Graph

The industry's admitted weakness is stale vendor lists. Fluid-Fund keeps the
catalog alive three ways:

1. **Verified reporting:** a vendor is marked "reports to Experian" only when a
   member tradeline from that vendor has appeared on an Experian file in the
   last 90 days (Bureau Insights closes the loop).
2. **Criteria drift detection:** approval and decline outcomes per vendor are
   monitored; when the approval rate for a profile band drops, the box is
   flagged for review and the matching tightens automatically.
3. **Lender boxes as data, not prose:** min time in business, min monthly
   revenue, min FICO, excluded industries, max amount, docs, speed, submission
   channel, commission. ROK's six product lines become ~40 boxes across ~1,000
   lender programs, each with a p(approve) model.

### 5.4 Capital Marketplace and One-Click Apply

- **15-second pre-qual** (from ROK) on the public site, but the result is never
  "no". Below the floor (6 months, $10K/month, 500 FICO) the response is a
  readiness plan with a date: "You are 74 days from your first working-capital
  box." That converts ROK's dead leads into Fluid-Fund members.
- **Packet builder:** the doc vault plus the graph assembles the application
  packet once; every lender submission reuses it (PDF and structured JSON).
- **Submission channels:** direct API where the lender has one, portal
  automation via a browser agent on the member's authorised session, or a
  templated email to the lender's intake. Every submission writes a receipt
  (what was sent, to whom, under which consent).
- **Funding Manager** (from Credit Suite) tracks every vendor and lender
  application with state machine: drafted → submitted → docs requested →
  approved / declined / countered → funded → reporting confirmed.
- **Advisor pairing** (from ROK) for deals above a threshold or when p(approve)
  is uncertain; the advisor works inside the same CRM, not a separate tool.
- **Commission and partner payouts** via Stripe Connect; the member always sees
  the economics (honest marketing).

### 5.5 Credit and bureau monitoring

- Tri-bureau business (D&B, Experian, Equifax) plus CreditSafe, with alerts on
  new tradelines, inquiries, score changes, derogatories and identity changes.
- Consumer credit only through explicit written authorisation stored in the
  consent ledger (FCRA permissible purpose), soft pulls only, never stored raw.
- **Bureau Insights closes the loop:** when an opened account shows on a file,
  the Tradeline gets `reporting_confirmed_at`, the vendor's verified-reporting
  flag refreshes, and the score recomputes.

### 5.6 Financial health

- Plaid for banking (balances, deposits, NSFs, cash runway), QuickBooks / Xero
  for P&L and balance sheet.
- Cashflow projections, DSCR, revenue consistency, concentration risk, and a
  valuation range (SDE and revenue multiples by NAICS) feed SBA/Bank Readiness.
- "Underwriter view": a one-page summary rendered the way a bank credit memo
  reads, so the member sees what the underwriter will see before applying.

### 5.7 Mentor agent

A Claude-based agent grounded on the member's graph with tools (read graph,
explain score, list opportunities, draft a fix plan, schedule an agent action,
open a ticket to a human advisor). Every answer cites graph items. It never
pulls credit, submits an application or sends outreach without a consent-scoped
approval step. It also runs inside Slack/SMS/email so the member does not have
to log in.

### 5.8 Growth and community (the BWW layer, data-linked)

- **Dojo:** courses and playbooks, but each lesson is attached to a graph item
  or stage, so the member sees "3 lessons for your current red items" rather
  than a library.
- **War Room:** weekly live sessions; hot-seat selection is driven by stage
  cohorts and anonymised graph summaries, so advice is specific.
- **Round Table:** daily peer and expert Q&A with the Mentor agent drafting
  first answers for expert review.
- Industry playbooks (trucking, restaurants, real estate agents, contractors)
  generated and kept current from the knowledge graph and outcome data.
- Progress guarantee that is measurable because the score is: "if your
  Fundability Score does not rise by X in 90 days while the plan is followed,
  refund."

### 5.9 Partner, agency and white-label

- Agencies, credit-repair firms, accountants and brokers run Fluid-Fund under
  their brand (tenant > workspaces), with their own CRM pipeline, commission
  schedules and member reporting. This is how Credit Suite reaches 60,000
  businesses; Fluid-Fund makes it a product tier instead of a side program.

---

## 6. Revenue OS: the autonomous lead-generation operating system + CRM

The same engine serves two tenants: Fluid-Fund acquiring members, and each
member acquiring their own customers (the "Connection" and "Conversion" Cs).

### 6.1 Inbound

| Asset | Mechanism | Competitor it beats |
|---|---|---|
| **Free Fundability Pre-Score** | Enter a business name and state; the system pulls public SoS, GBP, domain and 411 data and returns a partial score with three red items. Full score requires an account. | Credit Suite's quiz and "book a call"; ROK's form that only works above the floor |
| **Programmatic SEO** | Product x industry x state x city pages (e.g. "equipment financing for HVAC contractors in Texas") generated from the knowledge graph with live box data, refreshed monthly, each with a calculator and the pre-score widget | ROK's daily blog |
| **Calculators and tools** | Line-of-credit cost, SBA eligibility, "how much can I qualify for" tied to real boxes | ROK's illustration-only slider |
| **Embeddable widget** | Partners and accountants embed the pre-score on their sites; leads attribute to the partner | Credit Suite's affiliate links |
| **Video and podcast** | Weekly War Room clips, industry playbooks, "we got X funded" case studies (only verified, with consent) | BWW content |
| **Speed to lead** | Every inbound lead gets a response in under 60 seconds: AI SDR by SMS/email/chat (with captured consent), human advisor within business hours for high-intent | ROK's advisor callback |

### 6.2 Outbound (consent-first, compliance-gated)

**Prospect sources**

- New business formations (SoS daily filings), new EIN-era signals, new GBP
  listings, new domains, business license issuances, UCC filing activity
  (recent financing or lien releases), job postings (growth signal), permit
  data (construction, restaurants), franchise directories, association
  memberships.
- Enrichment: Middesk, Clearbit-class firmographics, Twilio Lookup (line type
  and DNC status), Apollo-class contact data where lawful, website and GBP
  scraping only on the business's own public listing.

**Agent swarm (one task per agent, human gates marked ⛔)**

| Agent | Input | Output | Gate |
|---|---|---|---|
| Prospector | ICP rules, source feeds | Prospect records with signals | |
| Enricher | Prospect | Firmographics, contacts, channels, suppression flags | |
| Pre-Scorer | Public data | Partial Fundability Score, top 3 red items | |
| Segmenter | Score, signals | Segment (readiness band x industry x need) | |
| Copywriter | Segment, red items | Personalised sequence drafts (email, SMS, voicemail script, direct-mail card) | ⛔ template approval per segment |
| Compliance Guard | Every message and contact | Allow / block with reason (DNC, consent basis, quiet hours, state rules, frequency caps, claim language) | hard block |
| Sequencer | Approved sequence | Scheduled sends across the warmed domain pool | |
| Responder | Replies in the omnichannel inbox | Drafted replies, intent classification, objections handled, meeting offer | ⛔ first-reply review until accuracy threshold proven |
| Qualifier (voice/chat) | Inbound calls and chats | Qualification transcript, consent capture, pre-score delivered | ⛔ disclosure script locked |
| Scheduler | Qualified lead | Advisor meeting booked, prep brief generated | |
| Nurturer | Below-floor leads | 90-day readiness drip tied to their red items | |
| Reactivator | Closed-lost, funded accounts | Renewal and second-round funding outreach when the score crosses a new band | |
| Attribution | All events | Source → revenue, cost per funded dollar | |

**Channel rules (non-negotiable)**

- Email: CAN-SPAM, verified domains, warm-up, per-domain volume caps,
  one-click unsubscribe, suppression list shared across tenants.
- SMS and voice: prior express written consent for marketing texts and
  autodialed or AI voice calls (TCPA), national and state DNC scrubbing, quiet
  hours by recipient time zone, AI voice disclosed at call start, every consent
  stored with evidence.
- Commercial financing disclosures: California, New York, Utah, Virginia,
  Georgia, Florida, Connecticut, Kansas and others require specific cost
  disclosures on offers; the policy engine attaches the correct disclosure to
  any offer surfaced in those states.
- Credit: ECOA/Reg B adverse-action style explanations whenever Fluid-Fund
  itself declines or steers; FCRA permissible purpose and written authorisation
  for any consumer pull; no "pre-approved" language unless a firm offer exists.
- Marketing: no unverifiable testimonials, usage numbers or scarcity.
  Everything claimed on a page must be backed by a record the system can show.

### 6.3 Native CRM

Built, not bought (the KMOS CRM pattern), so the funding deal and the
Fundability Graph are the same record.

- Objects: Prospect, Lead, Contact, Company, Deal (membership deal or funding
  deal with box and p(approve)), Partner, Lender, Task, Meeting, Conversation,
  Sequence, ConsentRecord.
- Pipelines: Membership (inbound → qualified → trial → paid → active →
  expansion), Funding (ready → matched → packet → submitted → decision → funded
  → reporting), Partner (applied → onboarded → first referral → payout).
- Omnichannel inbox: email, SMS, voice transcripts, chat, social DMs in one
  thread per contact; agents draft, humans send until trust thresholds are met
  per agent.
- Speed-to-lead SLA board, advisor queues, round-robin, territory by state
  (because the disclosure rules differ by state).
- Reporting: cost per lead, cost per member, cost per funded dollar, score
  lift per cohort, time-to-first-tradeline, time-to-first-funding, partner
  payouts.
- For members: the same CRM, white-labelled, with their own sequences and the
  AI Marketer calendar executed instead of merely planned.

---

## 7. What Fluid-Fund looks like on 1 January 2027 (day in the life)

**A trucking company owner in Georgia, 8 months in business, $14K/month, 612
FICO.**

1. Searches "box truck financing Georgia", lands on a Fluid-Fund page with live
   boxes, runs the free pre-score: 318 of 1000, three red items (residential
   address on SoS, no 411 listing, no business bureau file).
2. Starts the $29 membership. Connects Plaid and QuickBooks; the graph fills in
   40 facts in 90 seconds. Score recomputes to 364 with factor explanations.
3. Mentor presents a 12-week plan: virtual address (agent provisions it and
   propagates to SoS, GBP, bureaus), 411 listing (agent files it), request DUNS
   (agent submits), three Tier 1 vendors balanced across bureaus (agent
   pre-fills applications; owner approves each in one tap).
4. Week 6: Bureau Insights confirms two tradelines reporting; score 521. The
   opportunity feed unlocks two fleet cards and a $25K revenue-based line with
   p(approve) 0.71. Georgia disclosure attached.
5. Week 9: owner taps "apply" on the line; the packet submits via the lender's
   API; approved at $20K; Funding Manager records terms; the OutcomeEvent
   trains the model.
6. Week 12: score 598; War Room hot seat on dispatch software; the owner's own
   Revenue OS runs a sequence to freight brokers in three states.
7. Month 8: Reactivator notices Bank Readiness crossed the SBA band and books
   an advisor call. Fluid-Fund earned the membership, a line commission, and
   will earn an SBA commission. The owner never typed their EIN twice.

---

## 8. Team delegation (40+ senior roles, 8 pods)

Each pod owns an engine, a KPI and a written spec. Pods ship behind feature
flags; nothing merges without the pod's reviewer and the compliance pod.

| Pod | Owner role | Headcount | Owns | Q1 2027 KPI |
|---|---|---|---|---|
| **1. Foundation & Graph** | Principal engineer (data integrations) | 5 (3 backend, 1 data eng, 1 QA) | Object model, connectors (SoS/Middesk, bureaus, Plaid, accounting, GBP, DNS, 411, Twilio Lookup), Auto-Foundation agents, consent ledger | 90% of Foundation items auto-verified; median time-to-green on fixable items < 7 days |
| **2. Scoring & Intelligence** | Executive scientist (credit risk ML) | 5 (2 ML, 1 credit-risk advisor, 1 data eng, 1 analyst) | Fundability Score 2.0, readiness scores, p(approve), calibration pipeline, factor explanations, projection engine | Calibration: predicted vs actual approval within 5 points per band; every score has item-level attribution |
| **3. Marketplace & Knowledge Graph** | Head of lending partnerships + senior engineer | 6 (2 engineers, 1 browser-automation engineer, 2 lender partnership managers, 1 vendor data curator) | Vendor and lender catalog, box schema, submission channels (API/portal/email), Funding Manager, commissions | 300+ verified-reporting vendors, 40 boxes with API or automated submission, 1,000 programs catalogued |
| **4. Member Experience** | Head of product + design lead | 6 (2 frontend, 1 mobile, 1 designer, 1 content designer, 1 Mentor-agent engineer) | Web and mobile app, 7-step builder UI, dashboard, doc vault, Mentor agent, Dojo/War Room/Round Table surfaces | Activation: 70% connect Plaid within 24 h; weekly active members 60% |
| **5. Revenue OS** | VP growth engineering | 7 (3 backend, 1 deliverability engineer, 1 voice/AI SDR engineer, 1 data eng, 1 RevOps) | Prospecting feeds, enrichment, agent swarm, warmed sending infrastructure, omnichannel inbox, native CRM, attribution | Cost per member under target; speed-to-lead < 60 s; reply accuracy threshold reached so Responder runs unsupervised on tier-1 intents |
| **6. Compliance, Risk & Trust** | General counsel (fintech) + compliance engineer | 4 (counsel, compliance eng, security eng, privacy analyst) | Policy engine (TCPA, CAN-SPAM, DNC, ECOA/FCRA, state CFDL, UDAAP), disclosure library by state, security (SOC 2 roadmap), honest-marketing review, consent evidence | Zero sends without consent record; every offer carries the correct state disclosure; external pen test passed |
| **7. Marketing & Content Engine** | CMO + SEO lead | 5 (SEO, content strategist, video producer, programmatic pages engineer, community manager) | Programmatic SEO, pre-score widget distribution, calculators, YouTube/podcast, War Room programming, partner marketing | Organic pre-scores per month; share of members from organic > 40% |
| **8. Capital, Finance & Advisory** | CFO + investor advisors | 4 (CFO, finance ops, 2 advisors/investors on lender economics and compliance) | Pricing, unit economics, lender commission schedules, partner payouts, fundraising narrative, board reporting | Contribution margin positive per member cohort by month 4; lender commission revenue per funded dollar tracked |

Cross-pod: a weekly **architecture council** (pod leads) owns the object model
and the agent runtime; a **model risk committee** (pods 2, 6, 8) signs off any
scoring change; **release train** every two weeks.

How each pod would explain its system in a sentence:

- Foundation: "We replace the questionnaire with APIs and show the evidence."
- Scoring: "We predict the lender's answer before the lender is asked, and we
  show our work."
- Marketplace: "Boxes are data; submissions are receipts; outcomes are training
  data."
- Member Experience: "One screen answers 'where do I stand and what is next',
  and the next step is one tap."
- Revenue OS: "Every business that could be a member is found, pre-scored,
  contacted with consent, answered in a minute, and remembered forever."
- Compliance: "If the system cannot prove it was allowed to send it, it does
  not send it."
- Marketing: "The free score is the product's front door, and the knowledge
  graph writes the pages."
- Finance: "We price on outcomes and we can show the margin on every funded
  dollar."

---

## 9. Sprint plan: November 2026 to end of Q1 2027

Five four-week sprints. Each has a demoable outcome.

| Sprint | Dates | Outcome |
|---|---|---|
| **S0 Foundations** | 3 Nov to 28 Nov 2026 | Repo, tenancy, object model, consent ledger, policy engine skeleton, Supabase schema and RLS tests, design system, Plaid + Middesk + DNS + Twilio Lookup connectors, pre-score v0 from public data, programmatic SEO page generator v0 |
| **S1 Credibility** | 1 Dec to 26 Dec | 7-step builder with auto-verified Foundation items, evidence panels, Score 2.0 v1 (rule-initialised, explainable), 12-week Plan generator, doc vault, bureau connectors (D&B, Experian, Equifax, CreditSafe) read path, Bureau Insights loop |
| **S2 Capital** | 29 Dec to 23 Jan 2027 | Vendor catalog with verified-reporting flags, 150 Tier 1 to Tier 3 vendors, box schema, 20 lender boxes with p(approve) v1, Funding Manager, packet builder, first API submission partner, first portal-automation partner, state disclosure library |
| **S3 Revenue OS** | 26 Jan to 20 Feb | Prospect feeds (SoS filings, GBP, domains), enrichment, pre-score outreach with Compliance Guard, warmed domain pool, omnichannel inbox, native CRM v1 with Membership and Funding pipelines, speed-to-lead SDR by SMS/email, attribution; Fluid-Fund's own acquisition runs on it |
| **S4 Growth & Launch** | 23 Feb to 27 Mar | Dojo/War Room/Round Table linked to graph stages, Mentor agent GA, partner white-label tier, Stripe Connect payouts, calibration pipeline on first outcomes, SOC 2 readiness, public launch with the free pre-score as the front door |

Beyond Q1 2027: voice AI qualifier GA, member-facing Revenue OS GA, SBA packet
automation, equity and investor-readiness module ("Compounding").

---

## 10. Pricing and positioning (honest by design)

| Tier | Price | Includes | Competitor reference |
|---|---|---|---|
| **Score** | Free | Public pre-score, three red items, programmatic pages, calculators | Credit Suite quiz, ROK pre-qual |
| **Member** | $29/month | Full graph, Score 2.0, plan, Auto-Foundation agents, tri-bureau monitoring, Dojo/War Room/Round Table | BWW $29 (but with data) |
| **Builder** | $149/month or $1,290/year | Vendor matching with one-tap apply, Funding Manager, Mentor agent, doc vault, cashflow and readiness | Credit Suite $2,997 / Lendavo $3,479 |
| **Capital** | $0 platform fee + lender commission disclosed to the member | Marketplace submissions, advisor pairing, SBA packet | ROK (commission, undisclosed) |
| **Agency** | $499/month per 10 workspaces + revenue share | White-label, partner CRM, payouts | Credit Suite partner program |

No "founding member" scarcity, no "regularly $47" anchors unless a prior price
actually existed, no funding-time promises beyond what the box data shows.

---

## 11. KPIs the whole company watches

- Pre-scores per week (top of funnel) and pre-score → member conversion.
- Median days to first verified tradeline; median days to first funding.
- Score lift per 90 days by starting band (the progress guarantee metric).
- Calibration error of p(approve) by box (model risk).
- Funded dollars per member; commission per funded dollar; contribution margin.
- Speed to lead; Responder accuracy; consent coverage (must be 100%).
- Complaint rate per 10,000 outbound contacts (must trend to zero).

---

## 12. Using REA to study the three platforms (legitimately)

REA (this repo) analyses applications from the outside. For Fluid-Fund we use
it on accounts we own to build a parity map, not to copy assets or data.

What to do:

1. **Feature and route inventory** of the Fundability web app you are logged
   into (fundability.creditsuite.com): page list, nav structure, the 7-step
   state machine, the Foundation item list, the score gauge inputs. REA's
   browser tooling captures the DOM and network shapes of your own session.
2. **Data model inference:** from your own session's API responses, derive the
   entity shapes (business details, foundation items with status enums, vendor
   cards with bureau and PG badges, funding manager states). Map each to the
   Fluid-Fund object model in section 4.3 and record gaps.
3. **UX flow recordings** of the pre-qual on rok.biz and the $1 trial on
   businesswealthwarriors.com (public pages) to benchmark time-to-value.
4. **Scoring behaviour study:** change one Foundation item in your own
   Fundability account and record the score delta; repeat per item to estimate
   their weights. Compare with Score 2.0's explanations.

What not to do: no scraping of other members' data, no circumventing access
controls, no reuse of their copy, vendor lists or course content, no automated
access that violates their terms. The vendor and lender catalog is built from
primary sources (the vendors and lenders themselves) and from Fluid-Fund's own
outcome data.

---

## 13. Risks and how the design absorbs them

| Risk | Mitigation built in |
|---|---|
| Outbound compliance (TCPA, DNC, state rules) | Compliance Guard is a hard block in the send path; consent ledger with evidence; AI voice disclosed; counsel owns the disclosure library |
| Score credibility | Calibration pipeline against real outcomes; explanations per item; model risk committee |
| Lender and vendor data staleness | Verified-reporting from tradeline appearance; drift detection on outcomes; curator pod |
| Bureau and data-provider contracts | Start with read access (monitoring resellers) and Plaid/Middesk; negotiate direct bureau agreements in parallel |
| Over-automation harming members | Human gates on credit pulls, submissions and money; member approves each application |
| Honest-marketing drift | Every public claim must link to a record; no scarcity copy; reviewed by pod 6 |
| Entity separation for M&A | Own repo, own Supabase project, npm-only dependencies, no cross-entity imports |

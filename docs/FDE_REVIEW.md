# FDE and implementation work samples

This is a guide to the customer problem-solving, prototypes, technical decisions, and implementation workflows in my portfolio.

I co-founded DiliPilot, built its first MVP, and scaled it to **$5K MRR**. The other examples below are public work samples or developer tools with stated limits. They demonstrate work relevant to forward-deployed engineering; they do not imply that I held an FDE title or operated these demos at customer production scale.

## 1. Turn incomplete requirements into an implementation plan

**[Implementation Workbench](https://github.com/zayyanla-hash/fde-implementation-workbench) · [Browser demo](https://fde-implementation-workbench-ascend4.vercel.app)**

The scenario is a synthetic software customer arriving with an incomplete handoff: a missing technical owner, unconfirmed sandbox access, and acceptance criteria that must survive the transition into tasks.

The workflow validates CSV/JSON intake, names the missing field, generates five owned tasks, enforces prerequisites, and exports a portable plan. The demo shows a failure and its correction, not just a successful screen.

Technical decisions to inspect:

- [Domain rules](https://github.com/zayyanla-hash/fde-implementation-workbench/blob/main/src/workbench/onboarding.py) keep validation and dependency transitions deterministic.
- [SQLite persistence](https://github.com/zayyanla-hash/fde-implementation-workbench/blob/main/src/workbench/onboarding_store.py) uses revisions to reject stale writes.
- [HTTP contract tests](https://github.com/zayyanla-hash/fde-implementation-workbench/blob/main/tests/test_onboarding_api.py) cover intake, correction, conflicts, persistence, and exports.
- [Deployment notes](https://github.com/zayyanla-hash/fde-implementation-workbench/blob/main/docs/DEPLOYMENT.md) distinguish local SQLite from browser-owned IndexedDB in the hosted demo.

**Boundary:** synthetic customer; no real integration is provisioned. The checklist records human updates. Authentication, multi-user operations, backups, and production observability would be separate implementation work.

## 2. Translate an ambiguous business question into inspectable rules

**[SignalDesk + FrictionLab](https://github.com/zayyanla-hash/signaldesk-frictionlab) · [Browser demo](https://zayyan-portfolio-labs-ascend4.vercel.app)**

The business questions are which accounts deserve investigation and where an onboarding flow needs attention. I defined the product framing, evidence standards, and review workflows, and built the tools with AI coding assistance.

The earlier public source release makes those decisions inspectable:

- [Account scoring](https://github.com/zayyanla-hash/signaldesk-frictionlab/blob/main/src/signaldesk/scoring.ts) separates hard exclusions from weighted prioritization.
- [Funnel calculations](https://github.com/zayyanla-hash/signaldesk-frictionlab/blob/main/src/frictionlab/analytics.ts) define cohort windows, ordering, exclusions, and denominators.
- [Evidence handling](https://github.com/zayyanla-hash/signaldesk-frictionlab/blob/main/src/frictionlab/evidence.ts) makes reviewed decisions depend on the evidence behind them.
- [Case studies](https://github.com/zayyanla-hash/signaldesk-frictionlab/blob/main/CASE_STUDIES.md) explain tradeoffs and proposed validation.

**Boundary:** the hosted demo is a newer version than this source release. Researched accounts are public-source examples, funnel fixtures are synthetic, and neither establishes buying intent or customer conversion improvement.

## 3. Make technical limitations visible to the operator

**[MCP Guard](https://github.com/zayyanla-hash/mcp-guard) · [Recorded browser demo](https://zayyanla-hash.github.io/mcp-guard/)**

MCP Guard is a local TypeScript CLI for supported source patterns, offline tool inventories, and declared-capability drift. Findings include source evidence, assumptions, and coverage information.

Read the [architecture](https://github.com/zayyanla-hash/mcp-guard/blob/main/docs/ARCHITECTURE.md) and [external coverage study](https://github.com/zayyanla-hash/mcp-guard/blob/main/docs/EVALUATION-EXTERNAL.md). The study exposes unsupported factory-bound registrations instead of presenting zero findings as a clean security result.

**Boundary:** this is a scoped review aid, not a runtime firewall, security certification, or general-purpose agent sandbox. The browser walkthrough replays recorded fixtures.

## 4. Own a product and its review workflow

**[DiliPilot case study](https://github.com/zayyanla-hash/dilipilot-case-study)**

My work connects acquisition buyers' diligence questions to document intake, reconciliation, proposed earnings adjustments, financing scenarios, and human review. The key technical boundary is separating model-assisted extraction from deterministic financial calculations.

**Evidence:** product ownership and the $5K MRR outcome; a public case study and synthetic demo. Source and customer information remain private. The demo does not establish lender approval or a real acquisition outcome.

## How I would walk through an implementation interview

For one of these projects, I would explain:

1. Who needs the workflow and what a successful handoff means.
2. The input contract, missing information, and failure cases.
3. The smallest usable prototype and the decisions encoded in code.
4. How I test correctness and make uncertainty visible.
5. What would need to change for the customer's real systems, access model, scale, and operating requirements.

That final step is a proposed production plan, not a claim that the portfolio demos already provide those capabilities.

[Back to my profile](https://github.com/zayyanla-hash) · [Portfolio](https://zayyanlatif.com)

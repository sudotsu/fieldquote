# FieldQuote

AI-powered estimating and job-scoping intelligence for physical service contractors, starting with tree service.

> **Status:** Planning. FieldQuote is active but intentionally sequenced after the Midwest Roots homeowner MCP launch work. The plan remains intact; implementation should not begin until the product, architecture, validation, and launch requirements are explicitly approved.

## Product thesis

FieldQuote should help a contractor turn incomplete job information—conversation, photos, property context, company pricing rules, and later actual job outcomes—into a transparent, contractor-specific estimating model.

It should answer:

> Given how this company actually operates, what is this job likely to require, what information is missing, what assumptions drive the estimate, what is the economic floor, and what should this company quote?

It should **not** merely answer:

> What does a job like this usually cost?

## Core differentiation

Photo-to-estimate already exists in the market. That is a feature, not the moat.

The intended differentiation is:

**contractor-specific pricing intelligence + explicit reasoning + uncertainty handling + ChatGPT-native interaction + interoperability with existing contractor systems + learning from estimated-versus-actual outcomes.**

## First vertical

Tree service.

FieldQuote should go deep enough on one trade to become trustworthy before considering broader trades.

## Intended final repository structure

```text
fieldquote/
├── README.md
├── AGENTS.md
├── CLAUDE.md
├── LICENSE
├── package.json / pyproject.toml       # final stack TBD
├── .env.example
├── .gitignore
│
├── docs/
│   ├── MASTER-PLAN.md                  # canonical approved product plan
│   ├── PRODUCT-SPEC.md
│   ├── DECISIONS.md
│   ├── NON-GOALS.md
│   ├── COMPETITIVE-RESEARCH.md
│   ├── TARGET-CUSTOMER.md
│   ├── JOBS-TO-BE-DONE.md
│   ├── PRICING-BRAIN.md
│   ├── TREE-SERVICE-ONTOLOGY.md
│   ├── UNCERTAINTY-MODEL.md
│   ├── QUESTION-SELECTION.md
│   ├── CALCULATION-SPEC.md
│   ├── USER-FLOWS.md
│   ├── DATA-MODEL.md
│   ├── ARCHITECTURE.md
│   ├── INTEGRATIONS.md
│   ├── PRIVACY-SECURITY.md
│   ├── MONETIZATION.md
│   ├── VALIDATION-PLAN.md
│   ├── PILOT-PLAN.md
│   ├── OPENAI-SUBMISSION.md
│   ├── SUCCESS-KILL-THRESHOLDS.md
│   ├── TEST-PLAN.md
│   ├── LAUNCH-CHECKLIST.md
│   └── ROADMAP.md
│
├── decisions/
│   ├── 0001-initial-vertical.md
│   ├── 0002-system-of-record-strategy.md
│   ├── 0003-pricing-engine-boundary.md
│   └── ...
│
├── domain/
│   ├── tree-service/
│   │   ├── services/
│   │   ├── job-factors/
│   │   ├── access/
│   │   ├── labor/
│   │   ├── equipment/
│   │   ├── disposal/
│   │   ├── risk/
│   │   ├── cleanup/
│   │   └── tests/
│   └── shared/
│
├── pricing/
│   ├── engine/                         # deterministic calculation engine
│   ├── rules/
│   ├── pricing-profile/
│   ├── margin/
│   ├── uncertainty/
│   └── tests/
│
├── tools/
│   ├── analyze-job/
│   ├── identify-missing-information/
│   ├── build-scope/
│   ├── estimate-production/
│   ├── estimate-labor/
│   ├── estimate-equipment/
│   ├── estimate-disposal/
│   ├── calculate-price/
│   ├── explain-price/
│   ├── compare-options/
│   ├── generate-customer-scope/
│   ├── record-actuals/
│   └── compare-estimate-to-actual/
│
├── server/
│   ├── mcp/
│   ├── api/
│   ├── orchestration/
│   ├── services/
│   ├── auth/
│   ├── billing/
│   ├── telemetry/
│   └── config/
│
├── data/
│   ├── schemas/
│   ├── migrations/
│   └── seed/
│
├── integrations/
│   ├── jobber/
│   ├── housecall-pro/
│   ├── servicetitan/
│   ├── quickbooks/
│   ├── calendar/
│   └── shared/
│
├── app/
│   ├── chatgpt/
│   ├── web/                             # optional future management surface
│   ├── components/
│   └── assets/
│
├── evals/
│   ├── estimate-quality/
│   ├── missing-information/
│   ├── pricing/
│   ├── uncertainty/
│   ├── scope-generation/
│   └── regressions/
│
├── fixtures/
│   ├── historical-jobs/
│   ├── synthetic-jobs/
│   ├── images/
│   ├── conversations/
│   └── edge-cases/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── contract/
│   ├── safety/
│   ├── pricing/
│   └── end-to-end/
│
├── scripts/
│   ├── import-historical-jobs.*
│   ├── validate-pricing-model.*
│   ├── run-evals.*
│   └── release-check.*
│
└── .github/
    ├── workflows/
    ├── ISSUE_TEMPLATE/
    └── pull_request_template.md
```

## Pricing Brain

The central product concept is the contractor-specific Pricing Brain.

Candidate company-level inputs include:

- target production/hourly rate;
- minimum job;
- crew roles and loaded labor;
- owned equipment;
- rentals;
- disposal methods and cost;
- travel/service radius;
- materials;
- overhead;
- target gross margin;
- markup rules;
- risk/complexity premiums;
- cleanup options;
- subcontracted work;
- company-specific estimating rules.

The system should always distinguish among:

1. observed facts;
2. contractor-provided facts;
3. inferred facts;
4. assumptions;
5. unknowns;
6. deterministic calculations;
7. recommendations.

## Calculation boundary

Pricing arithmetic and company pricing rules should be deterministic code wherever practical.

The language model may assist with extracting job facts, identifying uncertainty, asking questions, classifying scope, explaining results, and conversational control.

The model should not improvise hidden price math.

## Estimated-versus-actual loop

A completed job may eventually record:

- quote amount;
- planned labor versus actual labor;
- planned crew versus actual crew;
- equipment planned/used;
- disposal planned/actual;
- complications;
- discounts/change orders;
- margin outcome where available.

FieldQuote may use this history to identify systematic estimating errors, but should not silently rewrite company pricing policy.

## Existing-system strategy

FieldQuote should initially sit above or beside contractor systems of record instead of attempting to replace them.

Potential integrations include Jobber, Housecall Pro, ServiceTitan, QuickBooks, calendars, and other contractor systems where API access and commercial terms are practical.

## MVP proof

The MVP should prove:

**Can FieldQuote turn incomplete tree-job information into a transparent, contractor-specific estimating model that an experienced tree-service operator would trust enough to use during real estimating?**

Likely MVP scope:

- company pricing profile;
- structured tree-job intake;
- optional photo-assisted observations;
- material missing-information questions;
- job/scope model;
- labor and production assumptions;
- equipment and disposal assumptions;
- deterministic pricing;
- uncertainty display;
- internal estimate;
- customer-facing scope;
- conversational revisions.

## Explicit initial non-goals

FieldQuote is not initially:

- a replacement for Jobber, Housecall Pro, or ServiceTitan;
- an estimator for every trade;
- an autonomous sender of binding estimates;
- an arborist diagnosis system;
- a remote declaration that a worksite is safe;
- a generic national cost calculator;
- a black-box price generator;
- a contractor marketplace;
- a full accounting platform;
- a dispatch/route/payroll system.

## Planning deliverables required before implementation

Before implementation authorization, the repository should contain explicit decisions for:

- competitor matrix;
- current OpenAI/MCP distribution requirements;
- target customer;
- jobs-to-be-done;
- historical-job test dataset;
- tree-service estimating ontology;
- Pricing Brain specification;
- question-selection logic;
- uncertainty model;
- deterministic calculation engine;
- complete user flows;
- MVP requirements;
- acceptance tests;
- data schema;
- architecture decision records;
- privacy/security threat model;
- integration feasibility;
- monetization;
- pilot design;
- success thresholds;
- kill/change thresholds;
- launch/submission checklist;
- post-MVP roadmap.

## Relationship to Midwest Roots MCP

Midwest Roots MCP is the homeowner-facing tree-care product and is being prioritized first because its five core tools already exist.

FieldQuote is contractor-facing and remains a separate product.

Shared infrastructure or domain knowledge should be extracted only when actual reuse is demonstrated, not prematurely forced into a shared dependency.

## Relationship to AI Toolshed

Generic AI/MCP development infrastructure may be extracted into `sudotsu/ai-toolshed` when it is genuinely reusable outside FieldQuote.

FieldQuote itself should remain its own product repository.

## Current priority

FieldQuote remains active but paused behind the Midwest Roots MCP planning/build/launch sequence.

Its current plan should be preserved rather than redefined during that pause.

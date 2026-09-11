# FieldQuote --- Planning Mode Master Plan

**Status:** Planning / research only  
**Version:** 0.1  
**Date:** September 10, 2026  
**Implementation status:** No implementation authorized by this document.

## 1. Planning-mode operating rule

FieldQuote is currently in planning mode. Planning mode is deliberately read-only in spirit: investigate the problem, inspect competing products and platform constraints, identify assumptions, ask necessary questions, make decisions explicitly, and define acceptance criteria before implementation.

The plan is the execution contract. Implementation choices must not silently redefine the product. Material changes after approval belong in the decision log and require an explicit decision.

## 2. Product thesis

FieldQuote is a ChatGPT-native estimating and job-scoping intelligence layer for physical service contractors.

The first vertical is tree service.

The initial product should not attempt to replace Jobber, Housecall Pro, ServiceTitan, or other systems of record. Its role is to sit above or beside those systems and provide the reasoning layer they do not inherently provide.

A contractor should eventually be able to give ChatGPT job details and photos and receive a structured scope containing:

- work being considered;
- relevant job complexity factors;
- missing information that materially affects the estimate;
- labor assumptions;
- crew assumptions;
- equipment assumptions;
- access and material-handling considerations;
- disposal assumptions;
- uncertainty and risk factors;
- contractor-specific pricing calculations;
- a suggested price or price range;
- customer-facing scope language;
- alternatives or option pricing;
- and, where integrations permit, downstream creation of an estimate or job.

## 3. Material competitive finding

The generic idea of "upload photos and AI creates a contractor estimate" is already occupied.

Current products in or near this space include QuoteIQ, SmartTreeQuote, SimplyWise, Restimate, XBuild, and other AI estimating products. Some already advertise photo-driven estimating, including tree-service-specific workflows.

Therefore, **photo-to-price is a feature, not FieldQuote's moat.**

FieldQuote should not launch as another generic AI estimate generator with a ChatGPT wrapper.

## 4. Proposed differentiation

The current differentiation thesis is:

**Contractor-specific pricing intelligence + explicit reasoning + uncertainty handling + ChatGPT-native interaction + interoperability with existing contractor systems + learning from estimated-versus-actual outcomes.**

The product should answer a different question from a generic estimator.

Not:

> What does a job like this usually cost?

But:

> Given how this specific company operates, what does this job likely require, what information are we missing, what assumptions are driving the estimate, what is the company's economic floor, and what should this company quote?

## 5. Pricing Brain

The central product concept is the **Pricing Brain**.

Each contractor configures a company-specific operating model. Candidate inputs include:

- target production or hourly rate;
- minimum job charge;
- crew composition;
- loaded labor costs;
- equipment owned;
- equipment rental costs;
- disposal methods and costs;
- travel/service radius;
- material costs where relevant;
- overhead assumptions;
- desired gross margin;
- markup policy;
- risk or complexity premiums;
- cleanup levels;
- subcontracted work;
- common add-ons;
- company-specific estimating rules.

The system should preserve the distinction between:

1. observed facts;
2. contractor-provided facts;
3. inferred facts;
4. assumptions;
5. unknowns;
6. calculations;
7. recommendations.

A contractor must be able to understand why the system produced a number.

## 6. Tree-service-first strategy

FieldQuote should initially go deep on tree services rather than pretending to understand every trade.

Tree service is the correct first vertical because the product can be validated against real estimating knowledge and actual jobs.

Candidate tree-service variables include:

- service type;
- tree count;
- approximate size;
- species when relevant;
- observable condition;
- location on property;
- drop zone;
- nearby structures;
- fences;
- landscaping;
- neighboring property;
- road/sidewalk interaction;
- utility proximity;
- backyard/front-yard access;
- gate width;
- chipper/truck access;
- lift accessibility;
- climbing requirement;
- rigging requirement;
- wood handling;
- debris volume;
- haul trips;
- stump work;
- cleanup level;
- urgency;
- crew size;
- expected production time;
- equipment rental;
- subcontracted work;
- uncertainty requiring site verification.

This schema is not yet final.

## 7. Candidate user workflow

A representative workflow is:

1. Contractor tells ChatGPT about the job and optionally supplies photos.
2. FieldQuote extracts observations and project facts.
3. FieldQuote identifies information that materially affects scope or price.
4. It asks only the questions whose answers matter enough to change the result.
5. It builds a structured job model.
6. It applies the contractor's Pricing Brain.
7. It shows assumptions and uncertainty separately from known facts.
8. It produces an internal estimate.
9. The contractor can alter assumptions or scope conversationally.
10. FieldQuote recalculates affected values.
11. The contractor approves a customer-facing scope and price.
12. Later integrations may create the estimate/job in the contractor's existing business software.
13. After completion, actual labor, equipment, disposal, and job outcome can be compared with the estimate.
14. Those outcomes can improve future company-specific estimating without silently changing pricing rules.

## 8. Candidate MCP / plugin tool surface

Tool names are provisional. The capability boundaries matter more than the names.

Potential tools include:

- analyze_job
- extract_job_observations
- identify_missing_information
- build_scope
- estimate_production
- estimate_labor
- estimate_equipment
- estimate_disposal
- calculate_price
- explain_price
- compare_scope_options
- generate_customer_scope
- create_estimate
- create_job
- record_actuals
- compare_estimate_to_actual
- update_pricing_model

Tools that modify external systems should be clearly separated from read-only analysis tools and require appropriate user authorization/approval.

## 9. ChatGPT-native product requirement

FieldQuote should be designed as a product that belongs inside a conversation, not as a normal SaaS dashboard awkwardly embedded in ChatGPT.

The interaction model should support statements such as:

> Customer sent me these pictures. Quote this.

> Assume two climbers and one ground worker.

> Make cleanup optional.

> What happens to margin if I charge $1,800?

> Customer accepted option two. Create the estimate.

The UI can eventually provide interactive scope, assumptions, pricing, and option cards, but conversational control remains fundamental.

## 10. Existing-system strategy

FieldQuote should not initially recreate mature CRM/FSM functions.

Potential integration targets include systems such as Jobber, Housecall Pro, ServiceTitan, QuickBooks, Google Calendar, and other contractor systems where APIs and commercial terms make integration practical.

The integration strategy must be researched before commitments are made.

## 11. Estimated-versus-actual learning loop

A potentially defensible feature is the feedback loop between estimates and completed work.

For a completed job, FieldQuote could capture:

- quoted amount;
- planned labor hours;
- actual labor hours;
- planned crew;
- actual crew;
- planned equipment;
- actual equipment;
- planned disposal;
- actual disposal;
- unexpected complications;
- discounts/change orders;
- gross-margin outcome where cost data exists.

The system could then identify systematic estimating errors such as consistently underestimating backyard material handling or overestimating production time on open-drop removals.

Any automated learning mechanism must remain auditable. The product must not silently rewrite the contractor's pricing policy.

## 12. Homeowner companion: QuoteCheck

A possible later consumer product is **QuoteCheck**.

A homeowner could upload one or more contractor estimates and receive:

- normalized scope;
- inclusions and exclusions;
- ambiguous language;
- missing scope items;
- comparison across bids;
- useful questions to ask contractors;
- explanation of why two estimates may differ;
- warnings against treating generic national averages as proof that a local quote is unfair.

QuoteCheck should not claim that a contractor's price is objectively "correct" from incomplete information.

This product is a candidate distribution funnel and should remain separate from the contractor MVP until validated.

## 13. Monetization hypothesis

Do not depend on OpenAI providing a specific plugin-store payment model.

The working business model is an external SaaS/backend account with ChatGPT as a major acquisition and interaction surface.

Possible tiers:

- free trial or limited monthly usage;
- individual contractor subscription;
- team/company subscription;
- premium integrations;
- advanced actual-versus-estimated analytics.

Pricing is unresolved and requires willingness-to-pay validation.

## 14. Validation requirements before build

Before implementation, validate at least:

### Problem validation

Confirm that contractors have a meaningful estimating problem that existing tools do not solve adequately.

### Competitive validation

Map direct and adjacent competitors by supported trades, photo analysis, pricing customization, reasoning transparency, uncertainty handling, CRM/FSM integrations, estimate creation, learning from completed jobs, ChatGPT/plugin/MCP availability, and pricing.

### Workflow validation

Test the proposed workflow against real historical tree jobs.

### Pricing-model validation

Determine whether a company-specific model can produce useful estimates without requiring so much configuration that onboarding becomes impractical.

### Platform validation

Confirm current OpenAI plugin/MCP requirements, authentication requirements, UI capabilities, review requirements, privacy requirements, and distribution rules.

### Integration validation

Confirm which target systems expose usable APIs and what commercial/access restrictions apply.

### Commercial validation

Determine whether contractors will pay for the intelligence layer when they may already pay for FSM/CRM software.

## 15. MVP boundary --- provisional

The MVP should prove one thing:

**Can FieldQuote turn incomplete tree-job information into a transparent, contractor-specific, useful estimating model that an experienced tree-service operator would trust enough to use during real estimating?**

Likely MVP capabilities:

- company pricing profile;
- structured tree-job intake;
- optional photo-supported observations;
- material missing-information questions;
- tree-job scope model;
- labor/production assumptions;
- equipment/disposal assumptions;
- deterministic pricing calculation;
- uncertainty display;
- internal estimate;
- customer-facing scope;
- conversational revisions.

Likely excluded from the first proof:

- every trade;
- full CRM;
- payroll;
- accounting;
- dispatch;
- route optimization;
- payment processing;
- autonomous customer communication;
- marketplace;
- complex multi-company analytics;
- automatic self-modification of pricing rules.

## 16. Safety and epistemic requirements

The system must not present uncertain visual inference as an observed fact.

For tree work specifically, remote images cannot establish all structural, electrical, underground, access, or internal-condition facts.

FieldQuote should distinguish between preliminary estimating support and site verification.

It should identify conditions that make a remote estimate unreliable rather than forcing a number.

Electrical/utility routing and physical hazard logic require special review before launch.

## 17. Data model --- conceptual

Core entities likely include:

- User
- Company
- PricingProfile
- CrewRole
- Equipment
- DisposalMethod
- ServiceType
- Job
- JobObservation
- JobUnknown
- JobAssumption
- ScopeItem
- Estimate
- EstimateVersion
- PricingCalculation
- CustomerOption
- ActualJobOutcome
- IntegrationConnection
- AuditEvent

The schema is not locked.

## 18. Architecture --- unresolved decisions

The final architecture must specify:

- MCP server framework;
- backend language/runtime;
- database;
- authentication;
- tenant isolation;
- image storage;
- image retention;
- model/provider strategy;
- deterministic calculation engine;
- separation between model reasoning and price math;
- audit logging;
- observability;
- rate limiting;
- secrets handling;
- billing;
- integration architecture;
- ChatGPT UI components;
- deployment environment.

A major design principle should be that arithmetic and pricing rules are deterministic code, not numbers improvised by an LLM.

## 19. Security and privacy planning

Before implementation, define:

- what customer/property information is stored;
- what images are retained;
- retention periods;
- deletion;
- tenant isolation;
- authorization;
- integration-token storage;
- audit history;
- sensitive-data handling;
- data sent to model providers or MCP services;
- privacy policy requirements;
- abuse controls.

## 20. Success criteria

MVP success metrics should eventually include:

- estimate completion rate;
- percentage of jobs requiring manual correction;
- error between predicted and actual labor;
- error between predicted and actual disposal/equipment requirements;
- time saved per estimate;
- contractor acceptance/edit rate;
- repeat usage;
- conversion to paid;
- retention;
- integration usage.

Exact thresholds must be set before pilot evaluation.

## 21. Failure criteria

We should be willing to stop or materially change the product if research shows that:

- existing products already solve the proposed differentiated workflow well;
- contractors do not trust remote AI-assisted estimating;
- required onboarding data makes the product more work than it saves;
- integrations needed for usefulness are inaccessible;
- estimate quality cannot materially beat a generic LLM plus spreadsheet;
- users value photo estimation but not contractor-specific pricing intelligence;
- acquisition economics cannot support the likely subscription value.

## 22. Explicit non-goals

Until explicitly changed, FieldQuote is **not**:

- a replacement for Jobber/Housecall Pro/ServiceTitan;
- a universal estimator for every trade;
- an autonomous system allowed to send binding estimates without contractor approval;
- an arborist diagnosis system;
- a remote declaration that a tree or worksite is safe;
- a generic national cost calculator;
- a black-box price generator;
- a consumer contractor marketplace;
- a full accounting platform.

## 23. Decision log

### Locked / current direction

- FieldQuote is an active project.
- Planning precedes implementation.
- Tree service is the first vertical.
- Photo-to-estimate alone is not sufficient differentiation.
- Contractor-specific pricing intelligence is central.
- Existing FSM/CRM products should initially be integrated with rather than replaced.
- Pricing calculations should be transparent and auditable.
- QuoteCheck is a possible later consumer companion, not automatically part of the contractor MVP.

### Unresolved

- final product name;
- exact target customer profile;
- MVP tool surface;
- pricing;
- onboarding burden;
- model/provider choices;
- exact ChatGPT UI;
- initial integrations;
- storage and retention;
- pilot cohort;
- launch geography;
- submission strategy;
- success/failure thresholds.

## 24. Planning work still required before implementation authorization

The next planning pass must produce:

1. full competitor matrix;
2. OpenAI plugin/MCP distribution and review requirements;
3. target-customer definition;
4. jobs-to-be-done analysis;
5. historical-job test dataset design;
6. tree-service estimating ontology;
7. Pricing Brain specification;
8. question-selection logic;
9. uncertainty model;
10. deterministic calculation specification;
11. complete user flows;
12. exact MVP requirements;
13. explicit acceptance tests;
14. data schema;
15. architecture decision record;
16. security/privacy threat model;
17. integration feasibility matrix;
18. monetization research;
19. pilot design;
20. success and kill thresholds;
21. launch/submission checklist;
22. roadmap after MVP;
23. final decision log.

**Implementation should not begin merely because this document exists. The plan is complete only when the unresolved items above have been researched and explicitly decided.**

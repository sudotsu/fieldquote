# FieldQuote — Decision Log

This file records product/architecture decisions already made. Open questions remain in the master plan until explicitly resolved.

## D-001 — Product category

**Decision:** FieldQuote is an AI-powered / AI-assisted contractor estimating and job-scoping product.

## D-002 — Initial vertical

**Decision:** Start with tree service rather than prematurely generalizing across trades.

## D-003 — Primary differentiation

**Decision:** Photo-to-estimate is not the moat. FieldQuote centers on contractor-specific pricing intelligence, explicit reasoning and uncertainty, ChatGPT-native interaction, interoperability, and eventual estimated-versus-actual learning.

## D-004 — Pricing Brain

**Decision:** Company-specific pricing policy is a core product concept. Pricing should be based on the contractor's own labor, equipment, disposal, overhead, minimums, margin targets, service rules, and related inputs.

## D-005 — Calculation boundary

**Decision:** Deterministic pricing arithmetic and company pricing rules should live in code wherever practical. The model may extract facts, identify uncertainty, ask questions, classify scope, explain results, and control the workflow, but should not improvise hidden price math.

## D-006 — Systems of record

**Decision:** FieldQuote initially sits above or beside existing contractor systems rather than trying to replace Jobber, Housecall Pro, ServiceTitan, accounting, scheduling, dispatch, and similar systems.

## D-007 — Estimated-versus-actual loop

**Decision:** Historical outcomes may eventually calibrate recommendations and expose systematic estimating errors, but FieldQuote must not silently rewrite company pricing policy.

## D-008 — Relationship to Midwest Roots MCP

**Decision:** FieldQuote is a separate contractor-facing product. The homeowner MCP is being prioritized first because those five capabilities already exist. FieldQuote remains active and follows immediately after that work rather than being abandoned.

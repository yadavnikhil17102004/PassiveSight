# Improvement Guide

This guide turns "make TraceGuard smarter" into staged, measurable work.

## Current Constraint Summary

- TraceGuard is a Burp extension, not a standalone service.
- Analysis quality depends on request context quality and provider output quality.
- The current workflow is passive-first; active exploitation is out of scope.

## Improvement Goals

1. Increase finding precision (reduce noisy/weak findings).
2. Improve finding actionability (clear parameter/context and remediation).
3. Preserve throughput and runtime stability.
4. Keep behavior explainable for analysts.

## Phase Plan

### P1: Improve Input Context Quality

Focus: feed the model better, cleaner, and more relevant context.

Tasks:

- Improve request/response truncation strategy by preserving high-value sections.
- Expand structured extraction for parameters, headers, and response metadata.
- Strengthen static resource skip logic to avoid low-value calls.

Success indicators:

- Lower low-confidence finding percentage.
- Higher useful finding rate during manual review sessions.

### P2: Add Deterministic Pre-Checks Before AI

Focus: use cheap rule-based checks to enrich or gate AI analysis.

Tasks:

- Add lightweight checks for risky headers, missing hardening headers, and suspicious parameter patterns.
- Attach deterministic signals to prompt context.
- Skip AI calls for clearly irrelevant request classes where appropriate.

Success indicators:

- Reduced unnecessary AI calls for low-value traffic.
- Increased consistency of recurring finding types.

### P3: Smarter Scoring and Deduplication

Focus: better ranking and cleaner grouping of findings.

Tasks:

- Refine severity and confidence normalization logic.
- Improve dedupe keys with parameter-level context where safe.
- Introduce a triage score that combines severity, confidence, and context richness.

Success indicators:

- Fewer duplicate-like findings in UI and Issue Activity.
- Improved top-of-list relevance for analyst triage.

### P4: Explainability and Verification Hints

Focus: make findings easier to trust and verify quickly.

Tasks:

- Add "why flagged" rationale snippets to finding details.
- Add verification hints (manual validation steps) in finding output.
- Ensure remediation text is specific to observed context, not generic-only.

Success indicators:

- Faster analyst verification time per finding.
- Better acceptance rate of surfaced findings.

### P5: Evaluation Framework

Focus: create repeatable quality checks for each change.

Tasks:

- Define benchmark traffic sets (small, medium, noisy).
- Track core metrics by provider/model:
  - total requests
  - AI calls
  - cache hit ratio
  - findings created
  - findings accepted/rejected in review
- Compare before/after changes against same traffic replay.

Success indicators:

- Documented metric deltas per release.
- Fewer regressions after feature changes.

## Suggested Implementation Order

1. P1 (context quality)
2. P2 (deterministic pre-checks)
3. P3 (scoring + dedupe)
4. P4 (explainability)
5. P5 (evaluation framework and release gating)

## Code Areas To Touch First

- Data shaping and context:
  - `smart_truncate_body`
  - `extract_idor_signals`
  - `build_prompt`
- Response parsing and mapping:
  - `_parse_ai_response`
  - `map_confidence`
- Dedupe and identity:
  - `_get_url_hash`
  - `_get_finding_hash`
- Core pipeline:
  - `_perform_analysis`

## Guardrails

1. Do not break Jython compatibility.
2. Keep UI updates EDT-safe.
3. Avoid adding blocking calls on hot paths.
4. Preserve backward compatibility for config/cache formats unless versioned migration is included.

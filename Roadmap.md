# TraceGuard Documentation and Improvement Roadmap

This roadmap is the execution source for improving documentation quality and product maturity.

## Objective

Build a precise, presentation-ready documentation system and a practical upgrade plan that addresses current user friction:

- TraceGuard is not standalone (it runs only inside Burp Suite).
- Users must install, configure, and validate provider connectivity before analysis works.
- Detection quality must improve in measurable steps.

## Working Principles

1. Sequence: understand -> analyze -> orchestrate -> plan -> execute.
2. No vague tasks: every step must produce a file update.
3. Keep claims realistic and tied to current implementation.
4. Prioritize first-run success and signal quality.

## Scope

- In scope:
  - Root README clarity and user expectation-setting.
  - Setup guides (`QUICKSTART`, `INSTALLATION`) for first-run success.
  - New architecture/code-map reference.
  - New upgrade/improvement guide with phased milestones.
  - Docs hub updates for discoverability.
- Out of scope in this pass:
  - Runtime code behavior changes.
  - CI/test harness implementation.

## Execution Plan

### Phase 1: Foundation and Positioning

- [x] Update `README.md` with explicit constraints:
  - Burp-only runtime
  - Not standalone
  - Passive-first behavior
  - Setup dependency before findings
- [x] Add clearer docs index in `README.md`.

### Phase 2: Onboarding and Setup Precision

- [x] Rewrite `docs/guides/QUICKSTART.md` to a strict success path:
  - Install -> configure -> validate -> first finding.
- [x] Expand `docs/guides/INSTALLATION.md` with configuration checklist and failure matrix.

### Phase 3: Technical Documentation Depth

- [x] Add `docs/ARCHITECTURE.md` with:
  - Data flow
  - Concurrency model
  - Provider dispatch map
  - Persistence and cache map
  - Safe-change rules
- [x] Update `docs/README.md` to include architecture and improvement docs.

### Phase 4: Product Upgrade Strategy

- [x] Add `docs/project/IMPROVEMENT_GUIDE.md` with phased improvements:
  - P1: input/context quality
  - P2: deterministic pre-checks
  - P3: smarter scoring and dedupe
  - P4: explainability and verification hints
  - P5: evaluation framework

### Phase 5: Verification and Sign-Off

- [x] Validate internal link targets exist.
- [x] Confirm docs consistently use `TraceGuard` naming.
- [x] Confirm docs clearly state Burp + provider prerequisites.

## Acceptance Criteria

1. New users can understand in under 2 minutes that TraceGuard requires Burp and provider setup.
2. Quickstart gives a deterministic first-finding path.
3. Maintainers have a reliable architecture map before making changes.
4. Improvement roadmap includes concrete milestones and success metrics.

## Progress Log

- [x] Roadmap created.
- [x] Phases 1-5 completed.

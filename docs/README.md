# Documentation Hub

This documentation is organized for two goals:

1. Run TraceGuard quickly.
2. Improve TraceGuard safely.

## Start Here

- New user setup: `docs/guides/QUICKSTART.md`
- Full provider setup: `docs/guides/INSTALLATION.md`
- Runtime architecture: `docs/ARCHITECTURE.md`
- Internal processing notes: `docs/INTERNAL_WORKING.md`
- Maintainer validation workflow: `docs/DEVELOPER_WORKFLOW.md`

## Improvement-Oriented Docs

- Improvement guide and priorities: `docs/project/IMPROVEMENT_GUIDE.md`
- Optimization status and risks: `docs/project/OPTIMIZATION_PLAN.md`
- Benchmark template: `docs/project/BENCHMARK.md`
- Contribution policy: `docs/project/CONTRIBUTING.md`

## Core Source Map

- Stable runtime entrypoint: `traceguard_ai_community.py`
- Experimental variants: `variants/`
- Environment helper scripts: `tools/`

## How To Use This As A Maintainer

1. Read `docs/ARCHITECTURE.md` before touching core analysis flow.
2. Use `docs/DEVELOPER_WORKFLOW.md` for manual runtime validation.
3. Track behavior changes in `CHANGELOG.md`.
4. Keep related docs updated in the same pull request as code changes.

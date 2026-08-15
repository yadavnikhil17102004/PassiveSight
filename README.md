# TRACEGUARD AI - Community Edition

AI-assisted passive vulnerability analysis extension for Burp Suite.

## Important Reality Check

TraceGuard is not a standalone scanner.

- It only runs as a Python extension inside Burp Suite.
- It requires a configured AI provider before analysis works.
- It analyzes in-scope traffic that actually passes through Burp proxy.
- It is passive-first: it prioritizes analyst guidance, not autonomous exploitation.

If Burp is not installed, provider settings are missing, or traffic is not in scope, TraceGuard will not produce findings.

## What It Does

- Passively analyzes proxied HTTP request/response pairs.
- Supports multiple providers (Ollama, OpenAI, Claude, Gemini, Azure Foundry).
- Publishes findings to both TraceGuard UI and Burp Issue Activity.
- Uses request-signature caching to reduce repeat AI calls.
- Exports findings to CSV.

## Primary Runtime File

- Stable: `traceguard_ai_community.py` (recommended)
- Experimental: `variants/traceguard_v2_1_0_with_scope.py`

## Quick Install

1. Open Burp Suite.
2. Go to Extender -> Extensions -> Add.
3. Select extension type `Python`.
4. Load `traceguard_ai_community.py`.
5. Open the `TRACEGUARD` tab and configure provider settings.
6. Run `Test Connection`.
7. Put target in Burp scope and proxy traffic through Burp.

## Validation Checklist

- Provider URL/API key/model are valid.
- `Test Connection` returns success.
- Target is in Burp scope.
- Browser traffic is routed through Burp proxy.
- Findings appear in TraceGuard and Issue Activity.

For Azure environment validation:

```bash
./tools/test_azure_env.sh ./.env
```

Expected output includes `STATUS: VALID`.

## Documentation

- Docs hub: `docs/README.md`
- Quickstart: `docs/guides/QUICKSTART.md`
- Installation matrix: `docs/guides/INSTALLATION.md`
- Architecture map: `docs/ARCHITECTURE.md`
- Internal flow details: `docs/INTERNAL_WORKING.md`
- Developer workflow: `docs/DEVELOPER_WORKFLOW.md`
- Improvement roadmap: `docs/project/IMPROVEMENT_GUIDE.md`
- Changelog: `CHANGELOG.md`
- Legal notice/license: `docs/project/NOTICE.md`, `LICENSE`

## Repository Layout

- `traceguard_ai_community.py`: stable runtime integration target
- `variants/`: experimental implementations
- `tools/`: helper scripts
- `docs/`: user and maintainer documentation

## Responsible Use

Use only on systems you own or are explicitly authorized to test.

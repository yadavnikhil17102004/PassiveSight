# Quickstart - TraceGuard

This guide is the shortest reliable path to your first finding.

## Before You Start

TraceGuard only works inside Burp Suite.

You must have:

- Burp Suite installed
- Burp Python extension support (Jython runtime)
- One reachable AI provider configuration

## Step 1: Load Extension

1. Open Burp.
2. Navigate to `Extender -> Extensions -> Add`.
3. Set extension type to `Python`.
4. Load `traceguard_ai_community.py`.
5. Confirm the `TRACEGUARD` tab appears.

If the tab does not appear, check `Extender -> Errors` first.

## Step 2: Configure Provider

In `TRACEGUARD -> Settings`, set:

- Provider (`Ollama`, `OpenAI`, `Claude`, `Gemini`, or `Azure Foundry`)
- API URL
- API key (if required)
- Model/deployment name

Then click `Test Connection` and verify success before saving.

## Step 3: Set Burp Scope

1. Add your test target in `Target -> Scope`.
2. Confirm in-scope URLs are visible in Burp.
3. Ensure your browser/client is actually using Burp proxy.

No in-scope traffic means no analysis.

## Step 4: Generate Traffic

1. Browse or replay requests to the in-scope target.
2. Watch the TraceGuard findings table populate.
3. Verify entries are also visible in Burp Issue Activity.

## Step 5: Sanity Validation

Use this checklist if no findings appear:

- Extension loaded without errors
- Provider test passed
- Scope contains target hosts/paths
- Requests are flowing through Burp proxy
- Requests are not only static assets

## Azure-Specific Validation

```bash
./tools/test_azure_env.sh ./.env
```

Expected output includes `STATUS: VALID`.

## Next

- Full provider setup matrix: `docs/guides/INSTALLATION.md`
- Runtime architecture and code map: `docs/ARCHITECTURE.md`
- Internal behavior details: `docs/INTERNAL_WORKING.md`

# Installation and Provider Configuration

This guide covers complete setup and common failure recovery.

## Platform Requirements

- Burp Suite (Community or Professional)
- Java runtime compatible with Burp
- Burp Python extension support (Jython runtime)
- Network access to your selected provider endpoint

## Install TraceGuard in Burp

1. Open Burp.
2. Go to `Extender -> Extensions -> Add`.
3. Set extension type to `Python`.
4. Load `traceguard_ai_community.py`.
5. Open the `TRACEGUARD` tab.

If the extension fails to load, inspect `Extender -> Errors` before changing provider settings.

## Provider Configuration Matrix

### Ollama (Local)

- API URL: local Ollama HTTP endpoint
- API key: not required
- Model examples: `llama3:latest`, `deepseek-r1:latest`

### OpenAI

- API URL: OpenAI-compatible endpoint
- API key: required
- Model examples: `gpt-4o`, `gpt-4o-mini`

### Claude

- API URL: Anthropic-compatible endpoint
- API key: required
- Model example: `claude-3-5-sonnet-20241022`

### Gemini

- API URL: Gemini-compatible endpoint
- API key: required
- Model examples: `gemini-1.5-pro`, `gemini-1.5-flash`

### Azure Foundry

- API URL: Azure OpenAI-compatible endpoint root
- API key: required
- Model value: Azure deployment name
- API version: required and must match deployment compatibility

## Mandatory Validation Flow

1. Open `TRACEGUARD -> Settings`.
2. Configure provider fields.
3. Run `Test Connection`.
4. Save only after connection test passes.
5. Put target in Burp scope and proxy traffic.

## Failure Matrix

- Symptom: `Test Connection` fails immediately
  - Check: URL format, key presence, model/deployment spelling
- Symptom: Connection times out
  - Check: provider availability, network path, local firewall/VPN
- Symptom: Loads but no findings
  - Check: Burp scope, proxy routing, request mix (avoid static-only traffic)
- Symptom: Azure works in CLI but not in Burp
  - Check: API version parameter and deployment name in extension settings

## Azure Environment Precheck

```bash
./tools/test_azure_env.sh ./.env
```

Expected output includes `STATUS: VALID`.

## Recommended Operational Checklist

- Use the stable runtime file unless testing variants.
- Keep timeout settings realistic for your provider latency.
- Validate with known test traffic before larger sessions.
- Review findings in both TraceGuard table and Burp Issue Activity.

## Related Docs

- `README.md`
- `docs/guides/QUICKSTART.md`
- `docs/ARCHITECTURE.md`
- `docs/INTERNAL_WORKING.md`
- `docs/DEVELOPER_WORKFLOW.md`

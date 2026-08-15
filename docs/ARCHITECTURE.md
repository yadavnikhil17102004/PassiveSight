# Architecture and Code Map

This document maps the stable runtime implementation in `traceguard_ai_community.py`.

## Runtime Context

- Host runtime: Burp extension environment
- Language/runtime constraints: Jython 2.7-compatible Python
- Primary extension class: `BurpExtender`
- Stable entrypoint: `traceguard_ai_community.py`

## End-to-End Data Flow

1. Burp emits traffic events to extension hooks.
2. Requests are filtered by scope and static extension rules.
3. Eligible requests are queued into a fixed worker pool.
4. Analysis acquires host and global concurrency controls.
5. Request signature is generated for persistent cache lookup.
6. Cache hit reuses findings; cache miss calls selected AI provider.
7. AI response is parsed, normalized, and deduplicated.
8. Findings are published to:
   - TraceGuard findings table
   - Burp Issue Activity
   - CSV export output (on demand)

## Key Components

### Lifecycle and UI

- Extension registration: `registerExtenderCallbacks`
- UI construction: `initUI`
- UI refresh loop: `refreshUI`, `start_auto_refresh_timer`
- Settings and provider controls: `openSettings`

### Ingestion and Dispatch

- Passive scan entry: `doPassiveScan`
- HTTP listener entry: `processHttpMessage`
- Context menu forced analysis: `analyzeFromContextMenu`
- Scope check: `is_in_scope`
- Static resource skip check: `should_skip_extension`

### Analysis Core

- Standard path: `analyze` -> `_perform_analysis`
- Forced path: `analyze_forced` -> `_perform_analysis(..., bypass_dedup=True)`
- Prompt builder: `build_prompt`
- Provider router: `ask_ai`

### Provider Adapters

- `_ask_ollama`
- `_ask_openai`
- `_ask_claude`
- `_ask_gemini`
- `_ask_azure_foundry`

### Parsing and Normalization

- AI response parsing: `_parse_ai_response`
- Repair fallback: `_repair_json`, `_fix_truncated_json`
- Finding identity hashes: `_get_url_hash`, `_get_finding_hash`

### Persistence and Configuration

- Config lifecycle: `load_config`, `save_config`, `_migrate_config`
- Environment overrides: `apply_environment_config`, `_load_dotenv_values`
- Vulnerability cache lifecycle:
  - `load_vuln_cache`
  - `_get_request_signature`
  - `_get_cached_findings_for_signature`
  - `_store_cached_findings`
  - `save_vuln_cache`
  - `_async_save_cache`

## Concurrency Model

- Fixed-size worker pool for analysis execution.
- Global semaphore limits total concurrent AI calls.
- Per-host semaphores enforce host fairness.
- Design goal: controlled throughput without unbounded thread growth.

## Operational Outputs

- Burp scan issues via custom `IScanIssue` implementation.
- Findings table in TraceGuard tab.
- CSV export from `exportFindings`.

## Safe-Change Constraints

1. Preserve Jython 2.7 compatibility.
2. Keep Swing UI updates EDT-safe.
3. Preserve cache signature behavior unless intentionally migrated.
4. Maintain semaphore acquisition/release consistency.
5. Keep provider-specific behavior isolated in provider adapters.

# Klisten ToolGuard for Claude Code

Limited beta. Requires an existing Klisten account, an API key, and existing ToolGuard service/policy data. This plugin does not register servers, create scans, execute target tools, or cryptographically verify receipts.

## Local installation

Run `claude --plugin-dir /absolute/path/to/klisten-toolguard`. Enter your Klisten key only in the plugin secure configuration prompt; never in a chat or a committed file. Use `/mcp` to inspect connection status.

Available tools: `toolguard_gate_check_paid` (gate:check) and `toolguard_attestation_get` (attestations:read). Gate requests may debit prepaid balance. Set an account/key budget and approve intended charges. Keep the same idempotency key for an uncertain retry. Do not interpret ALLOW as a guarantee of safety or as execution authorization.

Authenticated production MCP initialize, tool listing, Gate call, attestation read, and idempotent replay were verified with the official MCP Inspector on 2026-10-10 using an isolated review identity. The sample returned UNKNOWN / SCAN_MISSING, not a safety certification. Native Claude Code installation remains unverified. Marketplace review is pending submission.

## Data and support

Requests are sent to https://api.klisten.co.kr. Do not include credentials or personal data in tool arguments. Your API key is used only as an Authorization header. This package does not execute target MCP tools or upload repositories. Privacy: https://klisten.co.kr/privacy.html. Terms: https://klisten.co.kr/terms.html. Support: klisteninc@gmail.com.

## Scope

Only the two ToolGuard tools described above are included. No payment, refund, scanning, arbitrary URL fetching, or other Klisten product tools are bundled.


## Example prompts

1. “Using my registered service ID, existing policy version and expected fingerprint, perform one ToolGuard Gate check. Explain the result and its evidence limits.” Approve any intended prepaid charge first. The service returns unknown when scan evidence is absent.
2. “Retrieve the attestation ID returned by that check and summarize the decision and reason codes.” The attestation must belong to the authorized organization.
3. “The response was interrupted. Retry the identical Gate request with the same idempotency key.” Do not change the request or create a new key merely to retry an uncertain paid operation.

Before use, create your own Klisten account and scoped API key at https://klisten.co.kr/app, and register the target service and policy through the documented REST API. This plugin does not perform that setup. Do not put your API key into a prompt.

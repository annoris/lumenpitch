# LumenPitch backend

This distribution starts without a connection to the original project's cloud.
Bring your own model provider through the existing provider settings. No credentials
or customer records are included.

## Optional owned cloud

The compatible OAuth device-flow integration is disabled until both
`CLOUD_OAUTH_ISSUER` (HTTPS origin) and `CLOUD_OAUTH_CLIENT_ID` are configured.
The configured service must implement the existing OAuth and presentation API
contract. The repository does not include that hosted service.

The optional gallery requires `COMMUNITY_ENABLED=true` and `COMMUNITY_API_URL`.
Use an endpoint you control; no gallery URL is supplied by default. Old gallery
environment variable names do not activate the service.

## Health probes

- `GET /health/live`: process liveness, without external provider calls.
- `GET /health/ready`: database connectivity; returns 503 when unavailable.

Readiness checks execute `SELECT 1`; they do not validate model credentials,
export dependencies or schema migration completion. No secrets, filesystem paths
or database connection strings are returned. Electron session protection still
applies in desktop mode.

## Fresh database required

LumenPitch renames the cloud provider table and internal identifiers. Start this
new distribution with an empty app-data directory and database. Do not point it
at a database used by the source project. No migration of previous accounts,
provider tokens, presentations or encryption keys is provided. Back up existing
data separately before a manual, reviewed migration.

Sentry is optional and requires an explicit DSN. Sending default personal data
is disabled unless explicitly enabled with the existing Sentry setting.

## Verification

The isolated Python 3.11 checks cover cloud opt-in, gallery configuration, network
avoidance when disabled, path validation, upstream redirects and error mapping.
Full provider generation and export require configured external services and the
complete backend dependency installation.

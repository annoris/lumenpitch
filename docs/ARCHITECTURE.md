# Project architecture

## Components

This repository retains an existing presentation engine with separate interface, API and desktop distribution. Attribution and migration history record its origins and do not represent a connected account or service.

| Location | Responsibility | Entry point |
| --- | --- | --- |
| `servers/nextjs/` | Interface, slide editor and web routes | `app/`, `next.config.mjs` |
| `servers/fastapi/` | API, generation, persistence and exports | `server.py`, `api/` |
| `electron/` | Desktop packaging and lifecycle | `package.json` |
| `templates/` | Reusable layouts | Per-template files |
| `scripts/` | Conversion, synchronization and diagnostics | Node/Python scripts |
| `docs/` | Architecture and operations | This document |
| `.github/workflows/` | Validation and distribution | GitHub Actions workflows |

## Runtime

The web interface calls the API for documents, language models, images, databases and export operations. Configure your own providers; keep credentials outside the repository. Nginx and `start.js` coordinate container processes, while Electron provides desktop distribution.

The interface uses Next.js and React. The API uses FastAPI, SQLModel, Alembic and Python 3.11. Component lockfiles pin reproducible dependencies. The external export runtime is managed by `scripts/sync-presentation-export.cjs` and requires an authorized compatible archive or an explicitly configured release server. No external export provider is configured by default. Check runtime compatibility and actual exports before release.

## Data and configuration

No company data, provider credentials or fictional organization are included. Upload your own documents into the deployed instance. `APP_DATA_DIRECTORY`, `TEMP_DIRECTORY`, `USER_CONFIG_PATH` and the database must use private instance storage outside Git. Both web and API processes need consistent configuration.

Authentication protects the application. Dashboard and template browsing do not require AI credentials; generation requires a configured provider. This distribution requires a fresh database. Existing accounts, provider tokens and presentations are not automatically migrated from another distribution.

## Organization

`servers/nextjs` and `servers/fastapi` remain stable because Docker, Electron, scripts and CI reference them. A future move requires updating all consumers together and validating each distribution. Preserve migration identifiers and all required license notices.

## Verification

`node scripts/project-health.mjs` inspects local structure and tools without accessing providers or secrets. `--json` emits structured output; `--strict` requires local dependencies and Python 3.11. This is not a functional test.

Run root `npm test`, web tests and production build, and backend checks with Python 3.11: `uv sync --locked --dev` and `uv run --locked python -m pytest`. See `VALIDATION.md` for checks actually performed and remaining limits.

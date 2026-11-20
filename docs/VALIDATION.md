# LumenPitch validation

Local verification on November 18, 2026. These results describe this checkout; they do not certify a production deployment or replace tests with real providers.

The final check after replacing demonstration videos with original SVG illustrations passed all 164 web tests and completed the production build, including TypeScript validation. English content and the dashboard access change are being checked separately below.

## Completed checks

| Component | Command or review | Result |
| --- | --- | --- |
| Root dependencies | `npm ci --ignore-scripts` using a temporary cache | Installed; audit reported 0 vulnerabilities |
| Root tools | `npm test` | 4 converter tests and 43 additional tests passed |
| Web dependencies | `npm ci --ignore-scripts` using a temporary cache | Installed from the lockfile; Next.js and its ESLint configuration then updated to 16.4.6 |
| Web | `npm test` in `servers/nextjs` | 164 tests passed, 0 failures before the English content update |
| Web types | `npx tsc --noEmit` | Passed |
| Production web build | `npm run build` | Passed with Next.js 16.4.6, route generation and type checking |
| Web lint | `npm run lint` | 0 errors; 62 warnings |
| Initial visual inspection | Headless Chrome, 1440 × 1000 | Administrator setup screen rendered correctly |
| Focused backend checks | Isolated Python 3.11 environment, verified by the backend agent | 40 configuration, community and network restriction tests passed; `compileall` passed |
| Electron | `npm run typecheck` and `npm run test:security` | Type checking passed; 14 tests passed; TypeScript compilation passed |
| Private files | Search for `.env`, database and PEM/KEY files outside dependencies | No private files of those types found in the inspected source tree |

The user's default npm cache had incompatible permissions. Temporary caches were used without changing those permissions. Dependency installation skipped lifecycle scripts; it does not constitute complete Electron installation or packaging.

The delivery includes a local repository initialized on `main`, without a commit or remote. The publishable-file audit found no previous product names in paths or text outside `LICENSE` and `NOTICE`. Previous promotional assets and service destinations were removed. Desktop icons were regenerated from the new brand.

## Security and known limits

- Next.js was updated from 16.4.1 to 16.4.6 to resolve advisories that blocked its production build.
- The web dependency audit still reports 18 high-severity dependencies, or 7 with `--omit=dev`. These arise from the `picomatch` ReDoS advisory propagated through consumers including `micromatch`, `fast-glob`, Tailwind and ESLint tools. The registry checked offered 4.0.7 as its latest release, and that release is affected. No nonexistent dependency was added and no major Tailwind migration was forced. Review [GHSA-fc5q-39xc-vjpf](https://github.com/advisories/GHSA-fc5q-39xc-vjpf) and repeat the audit before deployment.
- The build warns that dynamic storage access in `lib/readable-local-file.ts` broadens standalone server file tracing. Inspect the final deployment artifact and keep private runtime storage outside the source tree.
- `.gitignore` excludes keys, certificates, databases, caches and generated results while permitting configuration examples. `.dockerignore` excludes environment files and private material from images.
- The external export engine requires an authorized compatible archive or an explicitly configured operator-controlled server. It is not bundled, and real exports were not tested. No previous provider downloads are configured by default.
- The complete backend test suite, Docker builds, Electron installers, signing/notarization and generation with real AI keys have not been tested. Docker is unavailable on this machine. System Python is 3.9; the backend requires 3.11 and the backend checks used a separate interpreter.
- The new brand, table names and configuration require a fresh installation. Do not reuse a previous database without an explicit, tested migration.
- `min-w-0` was added to the authentication card so it can shrink on narrow displays. The subsequent build passed. The available mobile emulation did not establish a reliable viewport, so real mobile devices still require validation.

## Verified local access

As verified by the setup agent, the full backend was installed from `uv.lock` in an isolated Python 3.11 environment, migrations were applied to a fresh SQLite database and 16 templates were imported. The `/health/ready` probe reported an available database. A local development account was created through the setup endpoint using a random password stored outside the repository in a mode-600 file. Real login returned HTTP 200. Chrome displayed the authenticated dashboard with navigation to templates and settings.

Dashboard and template browsing is permitted without AI credentials. Authentication remains enabled; generation workflows still require a provider. Local credentials and runtime data are excluded from the ZIP.

## Repeating the checks

Run `npm test` at the repository root. Run `npm test`, `npm run lint` and `npm run build` in `servers/nextjs`. For the complete backend, use Python 3.11, `uv sync --locked --dev` and `uv run --locked python -m pytest` in `servers/fastapi`. Repeat dependency audits and export tests before publishing binaries.

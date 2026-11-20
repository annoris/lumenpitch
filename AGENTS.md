# Collaboration guide

- Read `docs/ARCHITECTURE.md` and `docs/PROJECT_STRUCTURE.md` before making cross-component changes.
- The interface lives in `servers/nextjs`; API and persistence in `servers/fastapi`; desktop distribution in `electron`.
- Preserve `LICENSE`, `NOTICE`, third-party notices and existing migration identifiers.
- Do not invent company data, domains, accounts, keys or test results.
- Do not add credentials, private documents, databases, downloaded models or exports to Git.
- Coordinate changes to shared files; verify references before moving directories.
- Validate the modified component and explicitly report checks that failed or were not run.
- `node scripts/project-health.mjs` is read-only diagnostics and does not replace functional tests.

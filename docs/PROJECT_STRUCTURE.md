# Folder map

- **Web product:** `servers/nextjs/app` contains routes; `components` reusable elements; `store` application state; `lib`, `utils` and `types` shared contracts and helpers.
- **API and engine:** `servers/fastapi/api` contains endpoints; `services` business logic; `models` persistence and contracts; `alembic` migrations; `tests` automated checks.
- **Distribution:** `electron`, `Dockerfile`, `Dockerfile.dev`, `docker-compose.yml`, `nginx.conf` and `start.js`.
- **Content:** `templates` contains bundled layouts; `docs/images` contains product screenshots for the README.
- **Maintenance:** `scripts`, `.github/workflows` and `docs`.

## Adding features

1. Add interface and API behavior within the corresponding component and define explicit contracts.
2. Put maintenance tools in `scripts`, outside public web routes.
3. Document operations in `docs` and place tests with their component.
4. Keep private documents, downloaded models, databases, exports and keys outside Git.
5. Update all consumers and verify references when changing directory structure. Preserve migration identifiers.

Local dependency and cache directories are not part of the published product. Review `git status` and `git diff --cached` before publishing; ignore rules do not replace manual review.

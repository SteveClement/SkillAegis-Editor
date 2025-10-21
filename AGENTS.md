# Repository Guidelines

## Project Structure & Module Organization
- `src/` holds the Vue 3 SPA (feature views in `Views/`, reusable widgets under `components/`, shared state in `store.js`, API utilities in `api.js`).
- `main.py` exposes the FastAPI services; backend helpers live alongside it. `start.sh` orchestrates the API and front-end bundle.
- `public/` delivers static assets for Vite, `docs/` stores documentation screenshots, and `dist/` is generated on build.
- Copy `config.py.sample` to `config.py` for local secrets.

## Build, Test, and Development Commands
- `python3 -m venv venv && source venv/bin/activate` creates the backend virtual environment with pinned dependencies (`requirements.txt`).
- `fastapi dev main.py` runs the API with hot reload on `http://localhost:8000`.
- `npm install` syncs front-end packages; `npm run dev` starts the Vite dev server (default `http://localhost:5173`).
- `./start.sh --exercise_folder scenarios/` launches the full stack against local exercise data.
- `npm run build` emits the production bundle to `dist/`; `npm run lint` applies ESLint/Prettier checks; `npm run format` rewrites `src/` with Prettier.

## Coding Style & Naming Conventions
- Use 2-space indentation for Vue/JS and follow ESLint defaults; Python modules conform to PEP 8.
- Name Vue single-file components in `PascalCase.vue`; keep route-level views in `Views/` mirroring router paths, and prefer named exports for shared utilities.
- Avoid disabling lint rules; run `npm run format` before committing UI code to keep formatting consistent.

## Testing Guidelines
- Exercise API changes through the auto-generated docs at `http://localhost:8000/docs` and include curl examples in PRs when endpoints change.
- Linting is the minimum gate; pair front-end changes with a manual scenario walkthrough (create → edit → evaluate) and note outcomes.
- If you add automated suites, place Python tests under `backend/tests/` (pytest) and Vue specs in `src/__tests__/` (Vitest).

## Commit & Pull Request Guidelines
- Mirror the repository style: `chg|fix|new|doc|ref: [scope] imperative summary` (see recent history for domain tags like `[front:inject-tester]`).
- Keep commits focused and include regenerated assets (e.g., `dist/`) only when required; mention why in the message.
- Pull requests must describe the change, list touched views/APIs, link issues, and attach screenshots or CLI output for UI/API updates.
- Flag config or schema changes (`config.py.sample`, `schema_cexf.json`) explicitly and update documentation when behavior shifts.

## Configuration Tips
- Never commit secrets; keep local overrides in `config.py` and document required keys in `config.py.sample` updates.
- Store scenarios under `scenarios/` and validate against `schema_cexf.json` before merging.

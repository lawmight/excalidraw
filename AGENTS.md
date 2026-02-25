# AGENTS.md

## Cursor Cloud specific instructions

### Overview

Excalidraw is a Yarn workspaces monorepo (Yarn Classic 1.22.22, Node >= 18). The single required service for development is the Vite dev server on port 3001. No databases, Docker, or external services are needed for core editor work.

### Running the dev server

```bash
yarn start  # Vite dev server at http://localhost:3001
```

### Key commands

See `CLAUDE.md` and root `package.json` `scripts` for the full list. The most common ones:

- `yarn test:code` — ESLint (must pass with `--max-warnings=0`)
- `yarn test:typecheck` — TypeScript type check (`tsc`)
- `yarn test:update` — run all Vitest tests with snapshot updates (use before committing)
- `yarn fix` — auto-fix Prettier + ESLint issues

### Gotchas

- The pre-commit hook in `.husky/pre-commit` is commented out (`# yarn lint-staged`), so there is no automatic pre-commit linting.
- Firebase config warnings (`Error JSON parsing firebase config`) in test stderr are expected in the cloud environment and do not cause test failures.
- The `vite-plugin-checker` ESLint integration prints `Found 0 error and 0 warning` as an `ERROR` log line — this is informational, not an actual error.
- Collaboration and AI features require external services not included in this repo; they are not needed for core development.

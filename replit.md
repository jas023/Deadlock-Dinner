# Deadlock Dinner: OS Survival

A pixel-art browser game that teaches college students the Dining Philosophers problem and core Operating Systems deadlock concepts through four playable challenges.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/deadlock-dinner run dev` — run the game
- `pnpm --filter @workspace/deadlock-dinner run typecheck` — typecheck the game
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/deadlock-dinner/src/game/engine.ts` — pure Dining Philosophers simulation rules and state transitions
- `artifacts/deadlock-dinner/src/game/progress.ts` — local browser progress and best-score persistence
- `artifacts/deadlock-dinner/src/App.tsx` and `src/index.css` — game UI and visual styling

## Architecture decisions

- Keep the game client-side; no account, database, API key, or paid service is required.
- Keep simulation transitions separate from rendering so fork ownership and deadlock detection use real state.
- Persist unlocks and best score in local storage.

## Product

Four progressive levels teach free-for-all deadlock, four-seat semaphore admission, resource ordering, and wait-for-cycle detection with process termination recovery. Includes a final quiz and results summary.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details

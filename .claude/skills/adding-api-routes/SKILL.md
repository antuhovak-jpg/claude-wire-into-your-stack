---
name: adding-api-routes
description: Use when adding a new Express API route or resource to this Course API, including its validation, store access, router mounting, and tests. Do not use for unrelated changes or edits limited to an existing route.
---

# Adding API routes

- Add one resource router in `routes/<resource>.js` and mount it in `server.js` under `/<resource>`.
- Keep all reads and writes in `db/store.js`; route handlers must not keep their own state.
- Validate request bodies in the route and return `400` for invalid input. Return `404` when a requested record does not exist.
- Return errors as JSON in the shape `{ "error": "message" }`.
- Add endpoint tests in `tests/<resource>.test.js` using `node:test`, `supertest`, and `store.reset()` in `test.beforeEach` when state is mutated.
- Update `docs/api.md` with the new endpoints and their request/response behavior.
- Run `npm test` and `npm run lint` after the route, store, tests, and docs are in place.

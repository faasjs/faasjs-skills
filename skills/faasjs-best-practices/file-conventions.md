# File Conventions

FaasJS SPA + API uses zero-mapping routing: route paths are derived directly from `*.func.ts` file paths.

## Core Principle

> Where `.func.ts` lives is where the route lives. No extra alias, rewrite, or mapping layer.

## Project Structure

Recommended root: `src/pages`

```txt
src/pages/
  page-a/
    index.tsx
    components/
      header.tsx
    api/
      submit.func.ts
    feature-a/
      components/
        panel.tsx
      api/
        create.func.ts
        index.func.ts
```

## Special Files

| File | Purpose |
|------|---------|
| `index.tsx` | Page entry UI |
| `*.func.ts` | API endpoint file |
| `index.func.ts` | Segment root endpoint |
| `default.func.ts` | Fallback endpoint |

## Route Resolution Order

`@faasjs/server` resolves request URLs by probing file candidates in this order:

1. `path.func.ts`
2. `path/index.func.ts`
3. `path/default.func.ts`
4. Parent directory `default.func.ts` (fallback up the tree)

## File-to-Route Mapping

- `src/pages/page-a/api/submit.func.ts` -> `POST /page-a/api/submit`
- `src/pages/page-a/feature-a/api/create.func.ts` -> `POST /page-a/feature-a/api/create`
- `src/pages/page-a/feature-a/api/index.func.ts` -> `POST /page-a/feature-a/api`

## API Placement Rules

- Put shared page APIs in `page-x/api/`
- Put feature-local APIs in `page-x/feature-y/api/`
- Keep UI in `components/` and APIs in `api/`

## Protocol Conventions

- Method: `POST`
- Content-Type: `application/json`
- Response shape (recommended):
  - Success: `{ "ok": true, "data": any, "error": null }`
  - Failure: `{ "ok": false, "data": null, "error": { "code": string, "message": string } }`

## Prohibited Patterns

1. Do not add path alias routing (for example, auto-mapping `/x/api/y` to `/x/y`).
2. Do not add directory semantic rewrite (for example, auto-converting `actions` to `api`).
3. Do not use `actions/` as the API directory name. Use `api/`.
4. Do not place `*.func.ts` under `components/`.

## Minimal Template

`src/pages/page-a/api/submit.func.ts`:

```ts
import { useFunc } from '@faasjs/func'

export const func = useFunc(() => {
  return async () => {
    return {
      accepted: true,
    }
  }
})
```

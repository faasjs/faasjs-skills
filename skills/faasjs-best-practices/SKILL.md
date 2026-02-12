---
name: faasjs-best-practices
description: FaasJS best practices - file conventions, database(knex).
user-invocable: false
---

Apply these rules when writing or reviewing FaasJS code.

## File conventions

See [File conventions](./file-conventions.md) for:
- Project structure and special files
- Route segments and fallback (`*.func.ts`, `index.func.ts`, `default.func.ts`)
- Verb naming semantics and list endpoint conventions

## Knex

See [Knex rules](./knex.md) for:
- Prefer query-builder methods over `knex.raw`

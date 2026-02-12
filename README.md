# FaasJS Agent Skills

Agent skills for common FaasJS workflows.

## Essential Skills

Start here. These background skills are auto-applied to prevent common mistakes.

### `faasjs-best-practices`

Core FaasJS knowledge:

- [File Conventions](./skills/faasjs-best-practices/file-conventions.md)
- [Knex Rules](./skills/faasjs-best-practices/knex.md)

## Installation

```bash
npx skills add faasjs/faasjs-skills
```

## Usage

**Background skills** (`faasjs-best-practices`) are automatically applied when relevant.

## Contributing

Each skill follows the [Agent Skills open standard](https://github.com/anthropics/skills):

1. Create a directory under `skills/` with the skill name (prefix with `faasjs-`)
2. Add a `SKILL.md` file with YAML frontmatter:
   ```yaml
   ---
   name: faasjs-skill-name
   description: Brief description
   user-invocable: false  # for background skills
   ---
   ```
3. For complex skills, add additional `.md` files and reference them from `SKILL.md`

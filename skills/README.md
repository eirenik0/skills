# Skills

Each subdirectory here is a standalone Agent Skill that follows the Agent Skills spec.

Structure:

```
skills/
  <skill-name>/
    SKILL.md
    scripts/
    references/
    assets/
    mcp/
```

Notes:
- `SKILL.md` is required and must match the directory name.
- `scripts/`, `references/`, and `assets/` are optional per the spec.
- `mcp/` is a repo convention for MCP server binaries built with `npx mcporter`.

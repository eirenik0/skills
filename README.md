# Skills

Shared skills repository aligned with the Agent Skills specification.

## Layout

```
skills/
  <skill-name>/
    SKILL.md
    scripts/
    references/
    assets/
    mcp/
templates/
  skill-name/
```

## Creating a skill

1. Copy `templates/skill-name/` to `skills/<skill-name>/`.
2. Update `skills/<skill-name>/SKILL.md` with a valid `name` and `description`.
3. Add any optional content in `scripts/`, `references/`, or `assets/`.
4. If the skill uses MCP servers, run `npx mcporter` in the skill root and keep generated binaries in `mcp/`.
   See mcporter docs: https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md

## Validation

Use the Agent Skills reference validator on a skill directory:

```bash
skills-ref validate skills/<skill-name>
```

## References

- Spec: https://agentskills.io/specification
- Standard repo: https://github.com/agentskills/agentskills

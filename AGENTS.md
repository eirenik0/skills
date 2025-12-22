# Repository Guidelines

This repository manages shared Agent Skills and templates aligned with the Agent Skills specification. It is intentionally minimal and documentation-first.

## Project Structure & Module Organization

- `skills/` contains individual skills, each in its own folder (e.g., `skills/pdf-processing/`). Each skill must include a `SKILL.md` at the root.
- `templates/skill-name/` is the starting template for new skills, including optional folders (`scripts/`, `references/`, `assets/`, `mcp/`).
- `LICENSE` and `README.md` provide legal and high-level usage context.

## Build, Test, and Development Commands

There are no build or test commands in this repository today. When adding automation, prefer documenting exact commands in `README.md` and here.

Skill validation (local tool):
- `cd tools/skills-ref && uv sync && source .venv/bin/activate` to install the validator.
- `skills-ref validate skills/<skill-name>` validates a skill against the Agent Skills spec.

Other examples (if added later):
- `npx mcporter` (run inside a skill folder) generates MCP binaries into `mcp/`. Typical flow:
  - Update `config/mcporter.json` with servers and `$env:VAR` placeholders.
  - `npx mcporter generate-cli --server <name> --config config/mcporter.json --output mcp/<name>.ts --bundle mcp/<name>.js`
  - Docs: https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md

## Coding Style & Naming Conventions

- Markdown only; keep files concise and in plain ASCII.
- Skill folder names must be lowercase with hyphens, matching the `name` field in `SKILL.md` (e.g., `skills/code-review/`).
- Use short headings and bullet points. Keep `SKILL.md` under 500 lines; move deep content into `references/`.

## Testing Guidelines

No automated tests exist. If you introduce scripts, include a minimal usage example in `SKILL.md` and document how to verify behavior.

## Commit & Pull Request Guidelines

No commit message convention is established yet (only an initial commit exists). For now:
- Use clear, imperative messages (e.g., "Add pdf-processing skill template").
- PRs should describe the skill added or modified, list any required tools, and note if MCP binaries were generated.

## Agent-Specific Instructions

- Skills must follow the Agent Skills spec and be discoverable by name/description.
- If a skill uses MCP servers, run `npx mcporter` from the skill root and store binaries under `mcp/`. Some servers require real API credentials to generate tool schemas, so prefer `$env:VAR` placeholders in configs.

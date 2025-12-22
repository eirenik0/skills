Generated MCP server binaries live here.

Use `npx mcporter` from the skill root to build them. The template includes
`config/mcporter.json` for local entries. Typical flow:

```bash
npx mcporter generate-cli --server <name> --config config/mcporter.json --output mcp/<name>.ts --bundle mcp/<name>.js
```

Some servers require real API credentials to generate tool schemas. Do not commit secrets.

Tip: use `$env:VAR` placeholders in `config/mcporter.json` and `.mcp.json` so each user can supply their own keys.

Docs: https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md

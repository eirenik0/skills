# Z.ai MCP Server Configuration

This directory contains MCP server binaries and configuration for z.ai integration.

## Setup

### Option 1: Use z.ai MCP Server (Recommended)

Configure z.ai MCP server in your MCP settings file (`.mcp.json`):

```json
{
  "mcpServers": {
    "zai": {
      "command": "npx",
      "args": ["-y", "@z.ai/mcp-server"],
      "env": {
        "ZAI_API_KEY": "your-zai-api-key-here"
      }
    }
  }
}
```

### Option 2: Environment Variables

Set your API key as an environment variable:

```bash
# Linux/Mac
export ZAI_API_KEY="your-zai-api-key-here"

# Windows (PowerShell)
$env:ZAI_API_KEY="your-zai-api-key-here"

# Windows (CMD)
set ZAI_API_KEY=your-zai-api-key-here
```

Then use the configuration from `config/mcporter.json`:

```json
{
  "mcpServers": {
    "zai": {
      "command": "npx",
      "args": ["-y", "@z.ai/mcp-server"],
      "env": {
        "ZAI_API_KEY": "$env:ZAI_API_KEY"
      }
    }
  }
}
```

## Available Tools

Once configured, the following MCP tools should be available:

- **Image Analysis**: `mcp__zai__analyze_image` or `mcp__zai__vision`
  - Analyzes images using vision AI
  - Supports OCR, object detection, scene understanding

- **Web Search**: `mcp__zai__search` or `mcp__zai__web_search`
  - Searches the internet for information
  - Returns relevant results with URLs

- **Web Page Reading**: `mcp__zai__fetch_url` or `mcp__zai__read_page`
  - Fetches and reads web page content
  - Extracts text and structured data

## Getting API Keys

Visit [z.ai](https://z.ai) to:
1. Create an account
2. Generate an API key
3. Configure billing if required

## Troubleshooting

### MCP Server Not Found
- Ensure `@z.ai/mcp-server` package is available
- Try running: `npx -y @z.ai/mcp-server --version`

### API Key Issues
- Verify your API key is correct
- Check that environment variable is set
- Ensure no extra spaces or quotes in the key

### Tool Names Different
- Tool names may vary based on MCP server version
- Check available tools with MCP introspection
- Update SKILL.md references if needed

## Building Standalone Binaries (Optional)

To generate standalone MCP binaries with mcporter:

```bash
# From the skill root directory
cd /home/user/skills/skills/zai-mcp

# Generate CLI wrapper
npx mcporter generate-cli --server zai --config config/mcporter.json --output mcp/zai.ts --bundle mcp/zai.js
```

**Note**: Some servers require valid API credentials to generate tool schemas.

## References

- mcporter documentation: https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md
- Agent Skills spec: https://agentskills.io/specification
- Z.ai documentation: https://docs.z.ai (check for actual URL)

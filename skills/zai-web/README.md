# Z.AI Web Reader Skill

Web page reading and content extraction using Z.AI web reader APIs via mcporter CLI - no MCP server attachment needed.

## Features

- Fetch and read web page content
- Extract article text and main content
- Parse structured data from pages
- Alternative to built-in WebFetch tool
- Clean content extraction without ads/navigation

## Quick Start

1. **Set API Keys**:
   ```bash
   export Z_AI_API_KEY="your-api-key-here"
   export Z_AI_MODE="ZAI"
   ```

2. **Read web pages** (tool names to be confirmed):
   ```bash
   npx mcporter call \
     --server "@z_ai/mcp-server-web-reader" \
     --tool webReaderTool \
     --args '{"url":"https://example.com/article"}' \
     --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
   ```

## Requirements

- Node.js ≥ v22.0.0
- Z.AI API key (GLM Coding Plan)
- mcporter (auto-installed via npx)

## Usage Limits

- Lite: 100 web reader requests
- Pro: 1,000 web reader requests
- Max: 4,000 web reader requests

## Development Status

**Note**: This skill is a template pending detailed Z.AI Web Reader API documentation. Tool names and parameters will be updated when official documentation is available.

## Documentation

- **SKILL.md**: Complete reference (pending API docs)
- Get API key: https://z.ai

## Version

1.0 - Initial release (template)

## License

Proprietary

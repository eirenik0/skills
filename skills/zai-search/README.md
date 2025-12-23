# Z.AI Web Search Skill

Web search using Z.AI search APIs via mcporter CLI - no MCP server attachment needed.

## Features

- Real-time web search with Z.AI's search engine
- Current news, stock prices, weather information
- Returns titles, URLs, summaries, site names, and icons
- Alternative to built-in WebSearch tool

## Quick Start

1. **Set API Keys**:
   ```bash
   export Z_AI_API_KEY="your-api-key-here"
   export Z_AI_MODE="ZAI"
   ```

2. **Search the web**:
   ```bash
   npx mcporter call \
     --server "@z_ai/mcp-server-search" \
     --tool webSearchPrime \
     --args '{"query":"your search query"}' \
     --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
   ```

## Requirements

- Node.js ≥ v22.0.0
- Z.AI API key (GLM Coding Plan)
- mcporter (auto-installed via npx)

## Usage Limits

- Lite: 100 searches
- Pro: 1,000 searches
- Max: 4,000 searches

## Documentation

- **SKILL.md**: Complete reference and examples
- Get API key: https://z.ai

## Version

1.0 - Initial release

## License

Proprietary

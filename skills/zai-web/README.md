# Z.AI Web Reader Skill

Web page reading using Z.AI HTTP MCP API - direct HTTP calls, no MCP server attachment needed.

## Features

- Full-page content retrieval
- Structured data extraction
- Clean content without ads/navigation
- Returns title, content, metadata, links
- Alternative to built-in WebFetch tool

## Quick Start

1. **Set API Key**:
   ```bash
   export ZAI_API_KEY="your-api-key-here"
   ```

2. **Read web pages**:
   ```bash
   curl --request POST \
     --url https://api.z.ai/api/mcp/web_reader/mcp \
     --header "Authorization: Bearer $ZAI_API_KEY" \
     --header "Content-Type: application/json" \
     --data '{
       "jsonrpc": "2.0",
       "id": 1,
       "method": "tools/call",
       "params": {
         "name": "webReader",
         "arguments": {
           "url": "https://example.com/article"
         }
       }
     }'
   ```

## Requirements

- curl (standard in all environments)
- Z.AI API key (GLM Coding Plan)
- jq (optional, for JSON parsing)

## Usage Limits

- Lite: 100 web reader requests
- Pro: 1,000 web reader requests
- Max: 4,000 web reader requests

## Documentation

- **SKILL.md**: Complete MCP API reference with examples
- Get API key: https://z.ai/manage-apikey/apikey-list

## Version

1.0 - HTTP MCP API

## License

Proprietary

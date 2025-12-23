# Z.AI Web Search Skill

Web search using Z.AI HTTP API - direct REST calls, no MCP server attachment needed.

## Features

- Real-time web search optimized for LLM consumption
- Returns titles, URLs, summaries, icons, publish dates
- Domain and recency filtering
- 1-50 results per search (max 50)
- Alternative to built-in WebSearch tool

## Quick Start

1. **Set API Key**:
   ```bash
   export ZAI_API_KEY="your-api-key-here"
   ```

2. **Search the web**:
   ```bash
   curl --request POST \
     --url https://api.z.ai/api/paas/v4/web_search \
     --header "Authorization: Bearer $ZAI_API_KEY" \
     --header "Content-Type: application/json" \
     --data '{
       "search_engine": "search-prime",
       "search_query": "your query",
       "count": 10
     }'
   ```

## Requirements

- curl (standard in all environments)
- Z.AI API key (GLM Coding Plan)
- jq (optional, for JSON parsing)

## Usage Limits

- Lite: 100 searches
- Pro: 1,000 searches
- Max: 4,000 searches

## Documentation

- **SKILL.md**: Complete API reference with examples
- Get API key: https://z.ai/manage-apikey/apikey-list

## Version

1.0 - Direct HTTP API

## License

Proprietary

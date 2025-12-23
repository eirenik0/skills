---
name: zai-search
description: Web search using Z.AI HTTP API (direct REST calls, no MCP server attachment needed).
license: Proprietary
metadata:
  author: skills-repo
  version: "1.0"
---

# Z.AI Web Search Skill

## When to use

- User needs web search with Z.AI's specialized search engine
- Real-time information retrieval (news, stocks, weather)
- Alternative to built-in WebSearch tool
- Search results optimized for LLM processing
- When built-in WebSearch is rate-limited or unavailable

## Instructions

This skill provides access to Z.AI's Web Search API using direct HTTP calls through Bash. **No MCP server configuration required** - just curl commands with Bearer authentication.

### Prerequisites

1. **Z.AI API Key**: Set environment variable `ZAI_API_KEY=your_key`
2. **curl**: Available in all standard environments
3. **jq** (optional): For parsing JSON responses

### API Endpoint

**POST** `https://api.z.ai/api/paas/v4/web_search`

**Authentication**: Bearer token in Authorization header

### Usage

**Basic search:**
```bash
curl --request POST \
  --url https://api.z.ai/api/paas/v4/web_search \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "search_engine": "search-prime",
    "search_query": "your search query",
    "count": 10
  }'
```

**Parameters:**
- `search_engine` (string): Use `"search-prime"` for Z.AI's specialized search
- `search_query` (string, required): The search query
- `count` (integer): Number of results (1-50, default: 10, max: 50)
- `search_domain_filter` (string, optional): Filter results by domain
- `search_recency_filter` (string, optional): `"oneDay"`, `"oneWeek"`, `"oneMonth"`, etc.
- `request_id` (string, optional): Custom request identifier
- `user_id` (string, optional): User identifier for tracking

**Response includes:**
- `title` - Page title
- `content` - Content summary/snippet
- `link` - URL
- `media` - Associated media
- `icon` - Site icon
- `refer` - Referrer information
- `publish_date` - Publication date

### Workflow

1. **Formulate search query** - Create clear, specific search terms
2. **Set API key** - Verify `ZAI_API_KEY` environment variable is set
3. **Execute curl** - Use Bash tool to make HTTP POST request
4. **Parse JSON response** - Extract search results from response
5. **Present results** - Format and display to user with URLs
6. **Cite sources** - Always include source URLs in "Sources:" section

### Best Practices

1. **Clear queries**: Use specific, well-formulated search terms
2. **Date context**: Include year/date for time-sensitive queries
3. **Use filters**: Apply `search_recency_filter` for time-sensitive searches
4. **Result count**: Request appropriate number of results (default 10 is usually good)
5. **Source citation**: Always cite URLs in "Sources:" section
6. **Error handling**: Handle API failures gracefully
7. **Usage limits**: Be aware of plan limits (Lite: 100, Pro: 1000, Max: 4000)

### API Key Setup

Users need to set up their Z.AI API key:

```bash
# Linux/Mac
export ZAI_API_KEY="your-api-key-here"

# Windows PowerShell
$env:ZAI_API_KEY="your-api-key-here"
```

Get API keys from: https://z.ai/manage-apikey/apikey-list (requires GLM Coding Plan)

### Usage Limits

- **Lite Plan**: 100 web searches total
- **Pro Plan**: 1,000 web searches total
- **Max Plan**: 4,000 web searches total

These limits are shared with web reader functionality.

### Error Handling

Common errors:
- **401 Unauthorized**: Check `ZAI_API_KEY` is set and valid
- **400 Bad Request**: Verify request JSON structure
- **429 Rate Limit**: Inform user of usage limits reached
- **Network errors**: Suggest retry or fallback to WebSearch
- **Empty results**: Rephrase query or try different terms

## Examples

### Example 1: Current News Search

**Input:**
- "What's the latest news about quantum computing?"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/paas/v4/web_search \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "search_engine": "search-prime",
    "search_query": "quantum computing latest news 2025",
    "count": 10,
    "search_recency_filter": "oneWeek"
  }'
```

**Output:**
- List of recent articles about quantum computing
- URLs to news sources
- Content summaries
- Publication dates
- **Sources:** section with all URLs

### Example 2: Real-time Information

**Input:**
- "What's the current weather in Tokyo?"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/paas/v4/web_search \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "search_engine": "search-prime",
    "search_query": "Tokyo weather current",
    "count": 5,
    "search_recency_filter": "oneDay"
  }'
```

**Output:**
- Current weather information
- Temperature, conditions, forecast
- Source weather websites
- **Sources:** section

### Example 3: Domain-Filtered Search

**Input:**
- "Find Python documentation about asyncio"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/paas/v4/web_search \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "search_engine": "search-prime",
    "search_query": "Python asyncio documentation",
    "count": 10,
    "search_domain_filter": "python.org"
  }'
```

**Output:**
- Official Python documentation results
- Filtered to python.org domain
- **Sources:** section with URLs

### Example 4: Comprehensive Research

**Input:**
- "Research recent developments in AI agents"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/paas/v4/web_search \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "search_engine": "search-prime",
    "search_query": "AI agents developments 2025",
    "count": 25,
    "search_recency_filter": "oneMonth"
  }'
```

**Output:**
- Up to 25 relevant results
- Recent articles (past month)
- Comprehensive overview
- **Sources:** section

## Response Parsing

**Example response structure:**
```json
{
  "results": [
    {
      "title": "Article Title",
      "content": "Summary or snippet of the article content...",
      "link": "https://example.com/article",
      "media": "https://example.com/image.jpg",
      "icon": "https://example.com/favicon.ico",
      "refer": "example.com",
      "publish_date": "2025-01-15"
    }
  ]
}
```

Use `jq` for easy parsing:
```bash
curl ... | jq -r '.results[] | "\(.title) - \(.link)"'
```

## Notes

- **Direct HTTP API**: Uses simple curl POST requests
- **No MCP needed**: No mcporter, no server attachment
- **Bearer authentication**: Simple API key in header
- **LLM-optimized**: Search results designed for LLM consumption
- **Flexible filtering**: Domain and recency filters available
- **Always cite sources**: Include URLs in Sources section

## References

- [Z.AI Web Search API Documentation](https://docs.z.ai/api-reference/tools/web-search)
- [Z.AI API Introduction](https://docs.z.ai/api-reference/introduction)
- [API Keys Management](https://z.ai/manage-apikey/apikey-list)
- [Agent Skills Specification](https://agentskills.io/specification)

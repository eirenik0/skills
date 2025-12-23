---
name: zai-search
description: Web search using Z.AI search APIs via mcporter CLI (no MCP server attachment needed).
license: Proprietary
metadata:
  author: skills-repo
  version: "1.0"
---

# Z.AI Web Search Skill

## When to use

- User needs web search with Z.AI's search engine
- Real-time information retrieval (news, stocks, weather)
- Alternative to built-in WebSearch tool
- Access to Z.AI search results and summaries
- When built-in WebSearch is rate-limited or unavailable

## Instructions

This skill provides access to Z.AI's web search API using `npx mcporter call` commands through Bash. **No MCP server configuration required** - just use Bash to call the API directly.

### Prerequisites

1. **Z.AI API Key**: Set environment variable `Z_AI_API_KEY=your_key`
2. **Node.js**: Version 22.0.0 or higher
3. **mcporter**: Automatically installed via npx
4. **Z.AI Mode**: Set `Z_AI_MODE=ZAI` (or `ZHIPU` for alternate platform)

### Available Tool

#### **webSearchPrime**
Search web information, returning results including page titles, URLs, summaries, site names, and site icons.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-search" \
  --tool webSearchPrime \
  --args '{"query":"your search query"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Parameters:**
- `query` (string): The search query

**Response includes:**
- Page titles
- URLs
- Content summaries
- Site names
- Site icons
- Relevance rankings

**When to use:**
- Find current web information
- Retrieve real-time news, stock prices, weather
- Research topics with web sources
- Alternative when built-in WebSearch unavailable

### Workflow

1. **Formulate search query** - Create clear, specific search terms
2. **Set API key** - Verify `Z_AI_API_KEY` environment variable is set
3. **Execute mcporter call** - Use Bash tool to run the npx command
4. **Parse JSON response** - Extract search results
5. **Present results** - Format and display to user with URLs
6. **Cite sources** - Always include source URLs in response

### Best Practices

1. **Clear queries**: Use specific, well-formulated search terms
2. **Date context**: Include year/date for time-sensitive queries
3. **Source citation**: Always cite URLs in "Sources:" section
4. **Error handling**: Handle API failures gracefully
5. **Usage limits**: Be aware of plan limits (Lite: 100, Pro: 1000, Max: 4000)
6. **Alternative**: Fall back to built-in WebSearch if Z.AI fails

### API Key Setup

Users need to set up their Z.AI API key:

```bash
# Linux/Mac
export Z_AI_API_KEY="your-api-key-here"
export Z_AI_MODE="ZAI"

# Windows PowerShell
$env:Z_AI_API_KEY="your-api-key-here"
$env:Z_AI_MODE="ZAI"
```

Get API keys from: https://z.ai (requires GLM Coding Plan subscription)

### Usage Limits

- **Lite Plan**: 100 web searches total
- **Pro Plan**: 1,000 web searches total
- **Max Plan**: 4,000 web searches total

These limits are shared with web reader functionality.

### Error Handling

Common errors:
- **API Key missing**: Check `Z_AI_API_KEY` is set
- **Mode not set**: Ensure `Z_AI_MODE=ZAI` or `ZHIPU`
- **Node version**: Ensure Node.js ≥ v22.0.0
- **Rate limit**: Inform user of usage limits reached
- **Network errors**: Suggest retry or fallback to WebSearch

## Examples

### Example 1: Current News Search

**Input:**
- "What's the latest news about quantum computing?"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-search" \
  --tool webSearchPrime \
  --args '{"query":"quantum computing latest news 2025"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- List of recent articles about quantum computing
- URLs to news sources
- Summaries of each result
- Publication dates
- **Sources:** section with all URLs

### Example 2: Real-time Information

**Input:**
- "What's the current weather in Tokyo?"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-search" \
  --tool webSearchPrime \
  --args '{"query":"Tokyo weather current"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Current weather information
- Temperature, conditions, forecast
- Source weather websites
- **Sources:** section

### Example 3: Stock Price Lookup

**Input:**
- "What's the current NVIDIA stock price?"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-search" \
  --tool webSearchPrime \
  --args '{"query":"NVIDIA stock price NVDA current"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Current stock price
- Price changes and trends
- Financial news sources
- **Sources:** section with URLs

### Example 4: Technical Documentation Search

**Input:**
- "Find documentation for React Server Components"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-search" \
  --tool webSearchPrime \
  --args '{"query":"React Server Components documentation official"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Official documentation links
- Tutorial articles
- Code examples
- **Sources:** section

## Notes

- **No MCP server attachment**: Uses mcporter CLI directly via Bash
- **API key required**: Z.AI API key from GLM Coding Plan
- **Node.js v22+**: Required for @z_ai/mcp-server
- **Usage limits**: Monitor searches against plan limits
- **Always cite sources**: Include URLs in Sources section
- **Fallback option**: Can use built-in WebSearch if Z.AI unavailable

## References

- [Z.AI Web Search MCP Server Documentation](https://docs.z.ai/devpack/mcp/search-mcp-server)
- [Z.AI NPM Package](https://www.npmjs.com/package/@z_ai/mcp-server)
- [mcporter Documentation](https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md)
- [Agent Skills Specification](https://agentskills.io/specification)

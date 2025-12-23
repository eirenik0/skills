---
name: zai-web
description: Web page reading and content extraction using Z.AI web reader APIs via mcporter CLI (no MCP server attachment needed).
license: Proprietary
metadata:
  author: skills-repo
  version: "1.0"
---

# Z.AI Web Reader Skill

## When to use

- User needs to fetch and read web page content using Z.AI
- Extract article text and structured content
- Alternative to built-in WebFetch tool
- When built-in WebFetch fails or needs different parsing
- Access Z.AI's web scraping and content extraction

## Instructions

This skill provides access to Z.AI's web reader API using `npx mcporter call` commands through Bash. **No MCP server configuration required** - just use Bash to call the API directly.

### Prerequisites

1. **Z.AI API Key**: Set environment variable `Z_AI_API_KEY=your_key`
2. **Node.js**: Version 22.0.0 or higher
3. **mcporter**: Automatically installed via npx
4. **Z.AI Mode**: Set `Z_AI_MODE=ZAI` (or `ZHIPU` for alternate platform)

### Available Tools

**Note**: The Z.AI Web Reader MCP server tools are part of the GLM Coding Plan but specific tool names are not yet documented. This skill will be updated when detailed API documentation becomes available.

**Expected capabilities:**
- Fetch web page content
- Extract article text and main content
- Parse structured data from pages
- Handle dynamic content
- Return clean, readable text

**Usage Pattern (to be confirmed):**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-web-reader" \
  --tool webReaderTool \
  --args '{"url":"https://example.com/article"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

### Workflow

1. **Validate URL** - Ensure URL is accessible and valid
2. **Set API key** - Verify `Z_AI_API_KEY` environment variable is set
3. **Execute mcporter call** - Use Bash tool to run the npx command
4. **Parse JSON response** - Extract page content
5. **Present content** - Format and display to user
6. **Handle errors** - Fall back to WebFetch if needed

### Best Practices

1. **URL validation**: Check URLs before fetching
2. **Error handling**: Handle inaccessible pages gracefully
3. **Usage limits**: Be aware of plan limits (Lite: 100, Pro: 1000, Max: 4000)
4. **Alternative**: Fall back to built-in WebFetch if Z.AI fails
5. **Timeout handling**: Implement reasonable timeouts
6. **Content parsing**: Clean and structure extracted content

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

- **Lite Plan**: 100 web reader requests total
- **Pro Plan**: 1,000 web reader requests total
- **Max Plan**: 4,000 web reader requests total

These limits are shared with web search functionality.

### Error Handling

Common errors:
- **API Key missing**: Check `Z_AI_API_KEY` is set
- **Mode not set**: Ensure `Z_AI_MODE=ZAI` or `ZHIPU`
- **Node version**: Ensure Node.js ≥ v22.0.0
- **URL inaccessible**: Verify URL is valid and accessible
- **Rate limit**: Inform user of usage limits reached
- **Timeout**: Some pages may be slow to load
- **Content blocked**: Some sites block automated access

## Examples

### Example 1: Fetch Article Content

**Input:**
- "Read and summarize this article: https://example.com/article"

**Actions:**
```bash
# Tool name to be confirmed - this is a placeholder
npx mcporter call \
  --server "@z_ai/mcp-server-web-reader" \
  --tool webReaderTool \
  --args '{"url":"https://example.com/article"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Extracted article text
- Main content without ads/navigation
- Structured content
- Summary of key points

### Example 2: Extract Documentation

**Input:**
- "Get the content from this documentation page: https://docs.example.com/api"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-web-reader" \
  --tool webReaderTool \
  --args '{"url":"https://docs.example.com/api"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Documentation content
- Code examples
- API reference details
- Clean, readable format

### Example 3: Fetch Blog Post

**Input:**
- "Read this blog post and give me the main points: https://blog.example.com/post"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server-web-reader" \
  --tool webReaderTool \
  --args '{"url":"https://blog.example.com/post"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY" Z_AI_MODE="ZAI"
```

**Output:**
- Blog post content
- Main arguments and points
- Key takeaways
- Clean text extraction

## Development Status

**Note**: This skill is a template pending detailed Z.AI Web Reader API documentation. The tool names and parameters shown are placeholders and will be updated once official documentation is available.

To get accurate tool names:
1. Check Z.AI documentation: https://docs.z.ai/devpack/mcp/
2. Use `npx mcporter list-tools --server "@z_ai/mcp-server-web-reader"`
3. Contact Z.AI support for Web Reader MCP specifics

## Notes

- **No MCP server attachment**: Uses mcporter CLI directly via Bash
- **API key required**: Z.AI API key from GLM Coding Plan
- **Node.js v22+**: Required for @z_ai/mcp-server
- **Usage limits**: Monitor requests against plan limits
- **Fallback option**: Can use built-in WebFetch if Z.AI unavailable
- **Documentation pending**: Tool names/parameters to be confirmed

## References

- [Z.AI Documentation](https://docs.z.ai/devpack/mcp/)
- [Z.AI NPM Package](https://www.npmjs.com/package/@z_ai/mcp-server)
- [mcporter Documentation](https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md)
- [Agent Skills Specification](https://agentskills.io/specification)

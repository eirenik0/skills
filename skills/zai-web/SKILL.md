---
name: zai-web
description: Web page reading using Z.AI HTTP MCP API (direct HTTP calls, no MCP server attachment needed).
license: Proprietary
metadata:
  author: skills-repo
  version: "1.0"
---

# Z.AI Web Reader Skill

## When to use

- User needs to fetch and read web page content using Z.AI
- Extract article text and structured content from URLs
- Alternative to built-in WebFetch tool
- Get full-page content retrieval and structured data extraction
- When built-in WebFetch fails or needs different parsing

## Instructions

This skill provides access to Z.AI's Web Reader via HTTP MCP endpoint using direct HTTP calls through Bash. **No MCP server configuration required** - just curl commands with Bearer authentication.

### Prerequisites

1. **Z.AI API Key**: Set environment variable `ZAI_API_KEY=your_key`
2. **curl**: Available in all standard environments
3. **jq** (optional): For parsing JSON responses

### API Endpoint

**HTTP MCP Endpoint**: `https://api.z.ai/api/mcp/web_reader/mcp`

**SSE Endpoint** (alternative): `https://api.z.ai/api/mcp/web_reader/sse?Authorization=your_api_key`

**Authentication**: Bearer token in Authorization header

### MCP Tool Available

**webReader** - Fetches webpage content for a specified URL

**Returns:**
- Page title
- Main content (cleaned)
- Metadata
- List of links
- Structured data extraction

### Usage

**Basic web page reading:**
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

**MCP Protocol Notes:**
- Uses JSON-RPC 2.0 protocol
- Method: `tools/call`
- Tool name: `webReader`
- Arguments: `{"url": "https://..."}`

### Workflow

1. **Validate URL** - Ensure URL is accessible and valid
2. **Set API key** - Verify `ZAI_API_KEY` environment variable is set
3. **Execute curl** - Use Bash tool to make HTTP POST request with MCP JSON-RPC format
4. **Parse JSON response** - Extract page content from MCP response
5. **Present content** - Format and display extracted content to user
6. **Handle errors** - Fall back to WebFetch if needed

### Best Practices

1. **URL validation**: Check URLs before fetching
2. **Error handling**: Handle inaccessible pages gracefully
3. **Usage limits**: Be aware of plan limits (Lite: 100, Pro: 1000, Max: 4000)
4. **Alternative**: Fall back to built-in WebFetch if Z.AI fails
5. **Timeout handling**: Implement reasonable timeouts
6. **Content parsing**: Extract and structure the content appropriately
7. **Citation**: Cite the source URL when presenting content

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

- **Lite Plan**: 100 web reader requests total
- **Pro Plan**: 1,000 web reader requests total
- **Max Plan**: 4,000 web reader requests total

These limits are shared with web search functionality.

### Error Handling

Common errors:
- **401 Unauthorized**: Check `ZAI_API_KEY` is set and valid
- **400 Bad Request**: Verify JSON-RPC structure
- **URL inaccessible**: Verify URL is valid and accessible
- **429 Rate Limit**: Inform user of usage limits reached
- **Timeout**: Some pages may be slow to load
- **Content blocked**: Some sites block automated access
- **MCP error**: Check JSON-RPC format and parameters

## Examples

### Example 1: Fetch Article Content

**Input:**
- "Read and summarize this article: https://example.com/article"

**Actions:**
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

**Output:**
- Article title
- Main content (cleaned, without ads/navigation)
- Structured text
- Summary of key points
- Source URL

### Example 2: Extract Documentation

**Input:**
- "Get the content from this documentation page: https://docs.example.com/api"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/mcp/web_reader/mcp \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "jsonrpc": "2.0",
    "id": 2,
    "method": "tools/call",
    "params": {
      "name": "webReader",
      "arguments": {
        "url": "https://docs.example.com/api"
      }
    }
  }'
```

**Output:**
- Documentation page title
- Main content
- Code examples extracted
- API reference details
- Clean, readable format

### Example 3: Fetch Blog Post

**Input:**
- "Read this blog post and give me the main points: https://blog.example.com/post"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/mcp/web_reader/mcp \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "jsonrpc": "2.0",
    "id": 3,
    "method": "tools/call",
    "params": {
      "name": "webReader",
      "arguments": {
        "url": "https://blog.example.com/post"
      }
    }
  }'
```

**Output:**
- Blog post title
- Main content
- Key arguments and points
- Takeaways
- Clean text extraction

### Example 4: Extract News Article

**Input:**
- "What does this news article say? https://news.example.com/story"

**Actions:**
```bash
curl --request POST \
  --url https://api.z.ai/api/mcp/web_reader/mcp \
  --header "Authorization: Bearer $ZAI_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "jsonrpc": "2.0",
    "id": 4,
    "method": "tools/call",
    "params": {
      "name": "webReader",
      "arguments": {
        "url": "https://news.example.com/story"
      }
    }
  }'
```

**Output:**
- Article headline
- Main story content
- Key facts and quotes
- Publication date
- Source citation

## Response Parsing

**MCP Response Structure:**
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "content": [
      {
        "type": "text",
        "text": "Page title\n\nMain content here...\n\nLinks:\n- https://..."
      }
    ],
    "isError": false
  }
}
```

**Extracting content:**
```bash
# Parse with jq
curl ... | jq -r '.result.content[0].text'
```

**Alternative Response (if error):**
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "error": {
    "code": -32000,
    "message": "Error description"
  }
}
```

## Notes

- **HTTP MCP endpoint**: Uses MCP protocol over HTTP
- **No MCP server needed**: Direct curl calls, no local server
- **JSON-RPC 2.0**: Standard MCP protocol format
- **Bearer authentication**: Simple API key in header
- **Full content extraction**: Gets complete page content
- **Structured output**: Title, content, metadata, links
- **Usage limits shared**: Counts toward same quota as web search

## MCP Protocol Details

The Web Reader uses the Model Context Protocol (MCP) over HTTP:

1. **JSON-RPC 2.0** format for requests/responses
2. **tools/call** method to invoke the webReader tool
3. **Standard MCP response** with content array
4. **Error handling** via MCP error format

This is simpler than attaching an MCP server - just HTTP calls with the right JSON structure.

## References

- [Z.AI Web Reader MCP Server Documentation](https://docs.z.ai/devpack/mcp/reader-mcp-server)
- [Z.AI API Introduction](https://docs.z.ai/api-reference/introduction)
- [Model Context Protocol Specification](https://modelcontextprotocol.io)
- [API Keys Management](https://z.ai/manage-apikey/apikey-list)
- [Agent Skills Specification](https://agentskills.io/specification)

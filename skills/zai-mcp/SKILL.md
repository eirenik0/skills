---
name: zai-mcp
description: Use z.ai MCP servers for image analysis, web search, and web page reading without direct MCP attachment.
license: Proprietary
metadata:
  author: skills-repo
  version: "0.1"
---

# Z.ai MCP Integration

## When to use

- User requests image analysis or vision capabilities
- User needs to search the internet for current information
- User wants to fetch and read web pages
- User mentions z.ai, vision analysis, web search, or URL fetching
- Tasks requiring visual understanding of images
- Research tasks needing web content retrieval

## Instructions

This skill provides access to z.ai MCP servers for:
1. **Image Analysis** - Analyze images using vision capabilities
2. **Web Search** - Search the internet for information
3. **Web Page Reading** - Fetch and read content from web pages

### Setup Requirements

Before using this skill, ensure z.ai MCP servers are configured in your MCP settings. The skill assumes the following MCP tools are available:

- `mcp__zai__analyze_image` or `mcp__zai__vision` - For image analysis
- `mcp__zai__search` or `mcp__zai__web_search` - For web searches
- `mcp__zai__fetch_url` or `mcp__zai__read_page` - For fetching web pages

### Workflow

#### 1. Image Analysis
When analyzing images:
1. Check if image analysis MCP tools are available
2. Use the appropriate z.ai vision tool to analyze the image
3. Provide detailed analysis including:
   - Objects and scenes detected
   - Text content (OCR)
   - Visual elements and composition
   - Relevant context and insights

Example usage:
```
User: "Analyze this screenshot and tell me what's happening"
→ Use mcp__zai__analyze_image with the image path/URL
→ Provide comprehensive analysis of visual content
```

#### 2. Web Search
When searching the internet:
1. Formulate clear, specific search queries
2. Use z.ai web search MCP tool
3. Analyze results and synthesize information
4. Cite sources with URLs

Example usage:
```
User: "Search for the latest information on Claude AI"
→ Use mcp__zai__search with query: "Claude AI latest updates 2025"
→ Review search results
→ Summarize findings with source links
```

#### 3. Web Page Reading
When fetching web content:
1. Validate the URL provided
2. Use z.ai fetch/read page MCP tool
3. Extract and process the content
4. Summarize key information

Example usage:
```
User: "Read this article: https://example.com/article"
→ Use mcp__zai__fetch_url with the URL
→ Process the fetched content
→ Provide summary and key points
```

### Best Practices

1. **Error Handling**: If MCP tools are not available, inform the user to configure z.ai MCP servers
2. **Privacy**: Don't send sensitive images or URLs without user consent
3. **Efficiency**: Batch related operations when possible
4. **Context**: Maintain conversation context when performing multiple operations
5. **Sources**: Always cite sources for web search and page reading results

### Combining Capabilities

You can combine these capabilities for complex tasks:
- Search for information → Fetch specific pages → Analyze images from those pages
- Analyze image → Search for related information → Provide comprehensive context

## Examples

### Example 1: Image Analysis
Input:
- "What's in this image? [image.png]"

Output:
- Use vision MCP tool to analyze image
- Provide detailed description of contents
- Identify text, objects, scenes, and context

### Example 2: Web Research
Input:
- "Search for and summarize recent developments in quantum computing"

Output:
- Use web search MCP tool
- Fetch top relevant pages
- Synthesize information from multiple sources
- Provide summary with citations

### Example 3: URL Content Reading
Input:
- "Read and summarize https://example.com/long-article"

Output:
- Fetch page content using MCP tool
- Extract main points
- Provide structured summary

### Example 4: Combined Workflow
Input:
- "Find images of the Eiffel Tower, analyze one, and tell me its history"

Output:
- Search for Eiffel Tower images
- Select and analyze an image using vision tool
- Search for historical information
- Combine visual analysis with historical context

## Error Handling

If z.ai MCP tools are not available:
1. Check MCP tool names (they may vary based on configuration)
2. Inform user to configure z.ai MCP servers
3. Provide guidance on MCP server setup if needed
4. Suggest alternatives if available (e.g., built-in WebSearch, WebFetch)

## Notes

- This skill is a wrapper for z.ai MCP server capabilities
- Actual MCP servers must be configured separately
- Tool names may vary based on z.ai MCP server configuration
- Always verify tool availability before use

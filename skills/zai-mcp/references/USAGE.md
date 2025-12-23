# Z.ai MCP Usage Reference

## Overview

This reference provides detailed usage patterns for z.ai MCP server integration.

## Image Analysis

### Basic Image Analysis

```javascript
// Using MCP tool for image analysis
mcp__zai__analyze_image({
  image_url: "https://example.com/image.jpg",
  // or
  image_path: "/path/to/local/image.png"
})
```

### Use Cases

1. **Screenshot Analysis**
   - UI/UX review
   - Bug reporting with visual context
   - Documentation with screenshots

2. **Document OCR**
   - Extract text from images
   - Process scanned documents
   - Read handwritten notes

3. **Visual Understanding**
   - Identify objects and scenes
   - Describe image composition
   - Detect patterns and anomalies

### Best Practices

- Use high-quality images for better results
- Provide context in prompts for more accurate analysis
- Consider image size limits (check z.ai documentation)
- Handle sensitive images with appropriate privacy measures

## Web Search

### Basic Search

```javascript
// Using MCP tool for web search
mcp__zai__search({
  query: "latest developments in AI",
  max_results: 10,
  time_range: "past_year"  // optional
})
```

### Search Strategies

1. **Specific Queries**
   - Use specific keywords
   - Include date ranges when relevant
   - Add context terms

2. **Broad Research**
   - Start with general queries
   - Refine based on initial results
   - Follow interesting links

3. **Fact Checking**
   - Search multiple sources
   - Look for authoritative sources
   - Cross-reference information

### Best Practices

- Formulate clear, specific queries
- Use quotation marks for exact phrases
- Include date context for time-sensitive queries
- Always cite sources in results

## Web Page Reading

### Basic URL Fetch

```javascript
// Using MCP tool to fetch web pages
mcp__zai__fetch_url({
  url: "https://example.com/article",
  extract_text: true,
  include_metadata: true
})
```

### Use Cases

1. **Article Summarization**
   - Read long articles
   - Extract key points
   - Summarize content

2. **Documentation Reading**
   - Fetch API documentation
   - Read technical guides
   - Process reference materials

3. **Content Extraction**
   - Extract specific information
   - Process structured data
   - Parse HTML content

### Best Practices

- Verify URL validity before fetching
- Handle rate limits appropriately
- Respect robots.txt and site policies
- Cache results when appropriate

## Combined Workflows

### Research Pipeline

1. **Search** for relevant information
2. **Fetch** top results
3. **Analyze** any images in the content
4. **Synthesize** findings

Example workflow:
```
User: "Research latest smartphone features"
→ Search: "latest smartphone features 2025"
→ Fetch: Top 3-5 articles
→ Analyze: Product images if present
→ Synthesize: Comprehensive summary with sources
```

### Visual Research

1. **Search** for images or pages with images
2. **Analyze** images using vision tool
3. **Search** for related context
4. **Combine** visual and textual information

Example workflow:
```
User: "Find and analyze architecture of modern buildings"
→ Search: "modern architecture 2025"
→ Fetch: Pages with building images
→ Analyze: Architectural images
→ Search: Specific buildings or styles found
→ Provide: Visual analysis with architectural context
```

### Content Deep Dive

1. **Fetch** specific URL
2. **Analyze** images in content
3. **Search** for related information
4. **Provide** comprehensive analysis

Example workflow:
```
User: "Analyze this article: [URL]"
→ Fetch: Article content
→ Analyze: Any images/charts in article
→ Search: Related topics or sources
→ Provide: Full analysis with context
```

## Error Handling

### Common Errors

1. **MCP Tool Not Available**
   ```
   Error: mcp__zai__* tool not found
   Solution: Configure z.ai MCP server in .mcp.json
   ```

2. **API Key Missing/Invalid**
   ```
   Error: Authentication failed
   Solution: Set ZAI_API_KEY environment variable
   ```

3. **Rate Limiting**
   ```
   Error: Too many requests
   Solution: Implement delays between requests
   ```

4. **Invalid URL**
   ```
   Error: Failed to fetch URL
   Solution: Verify URL is accessible and valid
   ```

### Fallback Strategies

If z.ai MCP tools are unavailable:

1. **For Web Search**: Use built-in WebSearch tool
2. **For Web Fetch**: Use built-in WebFetch tool
3. **For Image Analysis**: Request user to use image upload with vision model

## Performance Optimization

### Caching

- Cache search results for repeated queries
- Store fetched page content when appropriate
- Reuse image analysis results

### Batching

- Group related operations
- Process multiple URLs in sequence
- Combine analysis results

### Rate Limiting

- Respect API rate limits
- Implement exponential backoff
- Queue requests when necessary

## Security Considerations

### API Keys

- Never commit API keys to version control
- Use environment variables
- Rotate keys periodically

### Content Safety

- Validate URLs before fetching
- Don't fetch from untrusted sources
- Handle sensitive images appropriately

### Privacy

- Get user consent for sensitive operations
- Don't log private information
- Respect data protection regulations

## Troubleshooting

### Tool Name Variations

If tool names don't match, check available tools:
- Vision: `mcp__zai__analyze_image`, `mcp__zai__vision`, `mcp__zai__image_analysis`
- Search: `mcp__zai__search`, `mcp__zai__web_search`, `mcp__zai__internet_search`
- Fetch: `mcp__zai__fetch_url`, `mcp__zai__read_page`, `mcp__zai__get_url`

### Debugging

1. Verify MCP server is running
2. Check environment variables
3. Test with simple operations first
4. Review MCP server logs
5. Validate API key permissions

## Examples

See SKILL.md for detailed examples of:
- Image analysis workflows
- Web research patterns
- URL content processing
- Combined multi-tool operations

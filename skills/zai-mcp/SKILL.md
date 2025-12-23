---
name: zai-mcp
description: Provides image analysis, web search, and web page reading capabilities using Claude Code's built-in tools.
license: Proprietary
metadata:
  author: skills-repo
  version: "0.2"
---

# Web and Vision Analysis Skill

## When to use

- User requests image analysis or vision capabilities
- User needs to search the internet for current information
- User wants to fetch and read web pages
- Tasks requiring visual understanding of images, screenshots, or diagrams
- Research tasks needing web content retrieval
- Combining visual analysis with web research

## Instructions

This skill provides three integrated capabilities using Claude Code's built-in tools:
1. **Image Analysis** - Analyze images using vision capabilities (Read tool)
2. **Web Search** - Search the internet for information (WebSearch tool)
3. **Web Page Reading** - Fetch and read content from web pages (WebFetch tool)

**No MCP servers or API keys required** - this skill works immediately upon loading.

### Workflow

#### 1. Image Analysis
When analyzing images:
1. Use the **Read tool** to load and analyze images
2. Claude's vision capabilities will automatically process the image
3. Provide detailed analysis including:
   - Objects and scenes detected
   - Text content (OCR)
   - Visual elements and composition
   - Relevant context and insights
   - Actionable recommendations

Example usage:
```
User: "Analyze this screenshot and tell me what's happening"
→ Use Read tool with the image path: Read(file_path="/path/to/screenshot.png")
→ Analyze visual content using Claude's vision capabilities
→ Provide comprehensive analysis of UI elements, text, and context
```

**Supported formats**: PNG, JPG, JPEG, GIF, WebP, and other common image formats

#### 2. Web Search
When searching the internet:
1. Formulate clear, specific search queries
2. Use the **WebSearch tool** to find current information
3. Analyze results and synthesize information
4. **Always cite sources** with URLs in a "Sources:" section

Example usage:
```
User: "Search for the latest information on Claude AI"
→ Use WebSearch(query="Claude AI latest updates 2025")
→ Review search results
→ Summarize findings
→ Include Sources section with links
```

**Important**: Always include a Sources section at the end of your response with relevant URLs.

#### 3. Web Page Reading
When fetching web content:
1. Validate the URL provided
2. Use the **WebFetch tool** to retrieve page content
3. Provide a clear prompt for what to extract
4. Process and summarize the content

Example usage:
```
User: "Read this article: https://example.com/article"
→ Use WebFetch(url="https://example.com/article", prompt="Summarize the main points and key takeaways")
→ Process the fetched content
→ Provide structured summary
```

**Note**: WebFetch converts HTML to markdown for easier processing.

### Best Practices

1. **Tool Selection**: Use the appropriate built-in tool for each task
   - Read tool for images
   - WebSearch for finding information
   - WebFetch for reading specific URLs

2. **Privacy & Security**:
   - Don't process sensitive images without user consent
   - Validate URLs before fetching
   - Respect website terms of service

3. **Efficiency**:
   - Batch related operations when possible
   - Use parallel tool calls for independent operations
   - Cache results when appropriate

4. **Quality**:
   - Provide detailed analysis for images
   - Always cite sources for web research
   - Summarize key points from web pages

5. **Context**: Maintain conversation context when performing multiple operations

### Combining Capabilities

You can combine these capabilities for complex research tasks:

**Pattern 1: Visual Research**
- Search for information → Fetch pages with images → Analyze those images
- Example: "Find modern architecture examples" → Search → Fetch pages → Analyze building images

**Pattern 2: Context Enhancement**
- Analyze image → Search for related information → Provide comprehensive context
- Example: Analyze logo → Search for company info → Provide full context

**Pattern 3: Deep Research**
- Search → Fetch multiple relevant pages → Analyze any images → Synthesize all information
- Example: Research topic → Get multiple sources → Process visual data → Create comprehensive report

## Examples

### Example 1: Image Analysis
**Input:**
- "What's in this screenshot? [/path/to/screenshot.png]"

**Actions:**
1. Use Read tool to load the image
2. Analyze visual content with Claude's vision
3. Identify UI elements, text, layout issues

**Output:**
- Detailed description of screenshot contents
- Identified text via OCR
- Analysis of UI/UX elements
- Suggestions for improvements

### Example 2: Web Research
**Input:**
- "Search for and summarize recent developments in quantum computing"

**Actions:**
1. Use WebSearch with query: "quantum computing recent developments 2025"
2. Review top search results
3. Optionally use WebFetch on most relevant articles
4. Synthesize information from sources

**Output:**
- Comprehensive summary of quantum computing developments
- Key breakthroughs and trends
- **Sources:** section with URLs to articles

### Example 3: URL Content Reading
**Input:**
- "Read and summarize https://example.com/long-article"

**Actions:**
1. Use WebFetch with URL and prompt: "Extract main points and key arguments"
2. Process the fetched content
3. Structure the summary

**Output:**
- Structured summary of article
- Key points and takeaways
- Important quotes or statistics
- Overall assessment

### Example 4: Combined Workflow
**Input:**
- "Research the Eiffel Tower: find an image, analyze it, and give me historical context"

**Actions:**
1. Use WebSearch: "Eiffel Tower images and history"
2. Use WebFetch on a page with quality images
3. If image URLs found, use Read to analyze one
4. Use WebSearch: "Eiffel Tower history facts"
5. Synthesize visual analysis + historical information

**Output:**
- Visual analysis of Eiffel Tower image (structure, details, perspective)
- Historical context: construction, designer, significance
- Interesting facts and statistics
- **Sources:** section with reference URLs

### Example 5: Screenshot Debugging
**Input:**
- "This error appeared on my screen [error-screenshot.png]. What does it mean and how do I fix it?"

**Actions:**
1. Use Read tool to analyze the error screenshot
2. Extract error message text via OCR
3. Use WebSearch: "[extracted error message] solution"
4. Use WebFetch on relevant Stack Overflow or documentation pages
5. Synthesize solution

**Output:**
- Error message interpretation
- Root cause analysis
- Step-by-step solution
- **Sources:** for troubleshooting guides

## Error Handling

### Image Files
- If image file not found, verify the path with user
- If image format unsupported, inform user of supported formats

### Web Operations
- If WebSearch fails, inform user (may be rate limited or unavailable)
- If WebFetch times out, try again or inform user
- If URL is invalid/inaccessible, validate with user

### General
- Handle all errors gracefully with clear user communication
- Suggest alternatives when primary tool fails
- Maintain context even when operations fail

## Tool Reference

This skill uses these Claude Code built-in tools:

1. **Read** - For loading and analyzing images
   - Supports: PNG, JPG, JPEG, GIF, WebP, etc.
   - Claude's vision automatically processes images

2. **WebSearch** - For internet searches
   - Returns search results with URLs
   - Must include Sources section in response

3. **WebFetch** - For fetching web page content
   - Converts HTML to markdown
   - Requires URL and analysis prompt

## Notes

- **No setup required**: Works immediately without MCP servers or API keys
- **Built-in capabilities**: Uses Claude Code's native tools
- **Privacy-focused**: All processing happens locally/within Claude
- **Always cite sources**: Include URLs when using web tools
- **Multimodal**: Seamlessly combines vision, search, and text processing

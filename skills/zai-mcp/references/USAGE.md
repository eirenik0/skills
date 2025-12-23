# Web and Vision Analysis - Usage Reference

## Overview

This reference provides detailed usage patterns for image analysis, web search, and web page reading using Claude Code's built-in tools.

**No MCP servers or API keys required** - all capabilities use native Claude Code tools.

## Built-in Tools

### 1. Read Tool (Image Analysis)

**Purpose**: Load and analyze images using Claude's multimodal vision capabilities

**Capabilities**:
- Visual understanding and description
- OCR (Optical Character Recognition)
- Object and scene detection
- UI/UX analysis
- Diagram interpretation
- Error message extraction from screenshots

**Supported Formats**: PNG, JPG, JPEG, GIF, WebP, and other common image formats

**Usage Pattern**:
```
Read(file_path="/absolute/path/to/image.png")
```

**Examples**:

```python
# Analyze a screenshot
Read(file_path="/home/user/screenshots/error.png")
# Claude automatically processes the image with vision AI

# Analyze a diagram
Read(file_path="/home/user/documents/architecture-diagram.jpg")
# Provides understanding of structure, components, relationships

# Extract text from image (OCR)
Read(file_path="/home/user/photos/handwritten-note.png")
# Extracts and interprets text content
```

### 2. WebSearch Tool

**Purpose**: Search the internet for current information

**Capabilities**:
- Find recent information beyond Claude's training data
- Discover relevant websites and resources
- Get current news and developments
- Research topics with multiple sources

**Usage Pattern**:
```
WebSearch(query="your search query here")
```

**Important**: Always include a "Sources:" section in your response with URLs from search results.

**Best Practices**:
- Use specific, clear search queries
- Include year/date context for time-sensitive queries (e.g., "2025")
- Use quotes for exact phrase matching
- Formulate queries as you would in Google/Bing

**Examples**:

```python
# Research recent developments
WebSearch(query="quantum computing breakthroughs 2025")

# Find specific information
WebSearch(query="Claude AI model capabilities")

# Fact-checking
WebSearch(query="\"climate change statistics\" 2025")

# Technical documentation
WebSearch(query="Python asyncio tutorial best practices")
```

### 3. WebFetch Tool

**Purpose**: Fetch and analyze specific web page content

**Capabilities**:
- Retrieve full article/page content
- Extract main points and summaries
- Process HTML content (automatically converted to markdown)
- Analyze documentation and guides

**Usage Pattern**:
```
WebFetch(
  url="https://example.com/article",
  prompt="What information to extract"
)
```

**The prompt parameter**: Specifies what you want to extract or analyze from the page

**Examples**:

```python
# Summarize an article
WebFetch(
  url="https://example.com/long-article",
  prompt="Summarize the main arguments and key takeaways"
)

# Extract specific information
WebFetch(
  url="https://docs.example.com/api",
  prompt="List all available API endpoints and their parameters"
)

# Analyze tutorial content
WebFetch(
  url="https://tutorial.com/guide",
  prompt="Extract step-by-step instructions and code examples"
)

# Get documentation details
WebFetch(
  url="https://github.com/project/readme",
  prompt="Explain installation requirements and usage"
)
```

## Common Workflows

### Workflow 1: Screenshot Debugging

**Scenario**: User has an error screenshot and needs help

**Steps**:
1. Use **Read** to analyze the screenshot
2. Extract error message via OCR
3. Use **WebSearch** to find solutions for that error
4. Use **WebFetch** on most relevant Stack Overflow/documentation pages
5. Synthesize complete solution

**Example**:
```
User: "Help me fix this error [screenshot.png]"

Actions:
1. Read(file_path="/path/to/screenshot.png")
   → Extract error: "TypeError: Cannot read property 'map' of undefined"

2. WebSearch(query="TypeError Cannot read property map of undefined JavaScript solution")
   → Find relevant Stack Overflow threads and articles

3. WebFetch(
     url="https://stackoverflow.com/questions/...",
     prompt="Extract the accepted solution and explanation"
   )

4. Provide complete solution:
   - Error explanation
   - Root cause
   - Step-by-step fix
   - Prevention tips
   - Sources with URLs
```

### Workflow 2: Research with Visual Context

**Scenario**: User wants to research a topic that includes visual information

**Steps**:
1. Use **WebSearch** to find relevant articles/pages
2. Use **WebFetch** to get detailed content
3. If image URLs found, use **Read** to analyze images
4. Synthesize text and visual information

**Example**:
```
User: "Research modern sustainable architecture and analyze examples"

Actions:
1. WebSearch(query="modern sustainable architecture 2025 examples")
   → Find articles about green buildings

2. WebFetch(
     url="https://architecture.com/sustainable-designs",
     prompt="Extract information about sustainable design principles and examples"
   )

3. If article mentions or links to images:
   - Note image URLs or download if possible
   - Use Read to analyze architectural images

4. Combine findings:
   - Sustainable architecture principles
   - Visual analysis of example buildings
   - Materials and techniques used
   - Sources cited
```

### Workflow 3: Deep Topic Research

**Scenario**: User needs comprehensive research on a topic

**Steps**:
1. Use **WebSearch** with well-crafted query
2. Use **WebFetch** on multiple top results
3. Synthesize information from all sources
4. Provide comprehensive answer with citations

**Example**:
```
User: "What are the latest developments in quantum computing?"

Actions:
1. WebSearch(query="quantum computing developments breakthroughs 2025")
   → Get list of recent articles

2. WebFetch on top 3-5 articles:
   WebFetch(url="...", prompt="Extract key developments and breakthroughs")
   WebFetch(url="...", prompt="List major companies and research institutions")
   WebFetch(url="...", prompt="Identify practical applications")

3. Synthesize all information:
   - Timeline of recent breakthroughs
   - Key players and institutions
   - Technical advances
   - Practical applications
   - Future outlook

4. Include Sources section with all URLs
```

### Workflow 4: Document Analysis with Context

**Scenario**: User provides a document image and wants contextual information

**Steps**:
1. Use **Read** to analyze the document
2. Extract key terms, topics, or questions
3. Use **WebSearch** to find related information
4. Use **WebFetch** for detailed context
5. Combine visual analysis with researched context

**Example**:
```
User: "Analyze this research paper abstract [image.png] and give me context"

Actions:
1. Read(file_path="/path/to/image.png")
   → Extract: Paper about "quantum error correction using topological qubits"

2. WebSearch(query="topological qubits quantum error correction research 2025")
   → Find related papers and articles

3. WebFetch on key resources:
   - Background papers
   - Related research
   - Institution information

4. Provide:
   - Analysis of paper abstract
   - Context of this research area
   - Significance and implications
   - Related work
   - Sources
```

### Workflow 5: Visual Comparison with Research

**Scenario**: Compare images and provide researched context

**Steps**:
1. Use **Read** on multiple images for comparison
2. Use **WebSearch** to find standards or best practices
3. Provide comparative analysis with evidence

**Example**:
```
User: "Compare these two UI designs [image1.png, image2.png] and tell me which follows better practices"

Actions:
1. Read(file_path="/path/to/image1.png")
   → Analyze UI layout, components, hierarchy

2. Read(file_path="/path/to/image2.png")
   → Analyze second UI design

3. WebSearch(query="UI design best practices 2025 principles")
   → Find current UI/UX standards

4. WebFetch(
     url="https://ux-guide.com/principles",
     prompt="Extract UI design principles and best practices"
   )

5. Provide comparison:
   - Visual analysis of both designs
   - Adherence to best practices
   - Strengths and weaknesses
   - Recommendations
   - Sources
```

## Best Practices

### For Image Analysis (Read Tool)

1. **Provide Clear Prompts**: When analyzing, be specific about what you're looking for
2. **Context Matters**: Give context about what the image represents
3. **Multiple Angles**: Analyze from different perspectives (technical, aesthetic, functional)
4. **Extract Text**: Always attempt OCR for images with text
5. **Describe Thoroughly**: Provide detailed descriptions of visual elements

### For Web Search (WebSearch Tool)

1. **Specific Queries**: Use clear, specific search terms
2. **Date Context**: Include year for time-sensitive topics
3. **Exact Phrases**: Use quotes for exact phrase matching
4. **Verify Sources**: Prefer authoritative sources
5. **Always Cite**: Include Sources section with URLs
6. **Multiple Searches**: Don't hesitate to search multiple times with refined queries

### For Web Fetching (WebFetch Tool)

1. **Clear Prompts**: Specify exactly what information to extract
2. **Validate URLs**: Ensure URLs are correct and accessible
3. **Targeted Extraction**: Focus on specific sections rather than generic summaries
4. **Multiple Sources**: Fetch from multiple sources for comprehensive info
5. **Handle Failures**: If fetch fails, try alternative sources

### Combining Tools

1. **Plan Workflow**: Think through which tools to use in what order
2. **Parallel Operations**: When possible, run independent operations in parallel
3. **Share Context**: Maintain context across tool uses
4. **Synthesize**: Combine results into coherent response
5. **Cite Everything**: Always attribute information to sources

## Error Handling

### Image Analysis Errors

**File Not Found**:
```
Error: ENOENT: no such file or directory
Solution: Verify path, check if relative vs absolute, confirm file exists
```

**Unsupported Format**:
```
Error: Cannot read image format
Solution: Convert to PNG, JPG, or other supported format
```

**Large Files**:
```
Error: File too large
Solution: Resize image before analysis
```

### Web Search Errors

**No Results**:
```
Issue: Search returns no relevant results
Solution: Rephrase query, use different keywords, broaden search terms
```

**Rate Limiting**:
```
Issue: Too many requests
Solution: Wait before retrying, inform user of limitation
```

### Web Fetch Errors

**URL Inaccessible**:
```
Error: Failed to fetch URL
Solution: Verify URL, check if site is up, try alternative source
```

**Timeout**:
```
Error: Request timeout
Solution: Retry once, inform user if persistent
```

**Content Blocked**:
```
Error: Access denied / 403
Solution: Site blocks bots - inform user, suggest manual access
```

### Redirect Handling

**Different Host Redirect**:
```
When WebFetch returns redirect message:
→ Make new WebFetch request with redirect URL
→ Inform user of redirect if relevant
```

## Performance Tips

1. **Batch Operations**: Run independent operations in parallel
2. **Cache Results**: Reference previous results when possible
3. **Selective Fetching**: Only fetch pages that are truly needed
4. **Efficient Queries**: Craft searches to minimize redundant searches
5. **Clear Communication**: Update user on progress for long operations

## Privacy and Security

1. **User Consent**: Ask before analyzing sensitive images
2. **URL Validation**: Verify URLs before fetching
3. **Data Handling**: Don't log or store sensitive information
4. **Respectful Crawling**: Don't overwhelm sites with requests
5. **Terms of Service**: Respect website terms and robots.txt

## Examples by Use Case

### Academic Research
- Search for papers and articles
- Fetch and summarize academic content
- Analyze figures and diagrams from papers
- Build comprehensive literature reviews

### Software Development
- Debug error screenshots
- Research API documentation
- Find code examples and tutorials
- Analyze UI/UX designs

### Content Creation
- Research topics for articles
- Analyze visual inspirations
- Find authoritative sources
- Gather current statistics and facts

### Business Analysis
- Research market trends
- Analyze competitor interfaces
- Gather industry reports
- Process business documents

### Education
- Research learning materials
- Analyze educational diagrams
- Find tutorial content
- Gather multiple perspectives on topics

## Advanced Patterns

### Iterative Refinement
1. Start with broad search
2. Analyze results and identify gaps
3. Perform targeted follow-up searches
4. Fetch specific pages for details
5. Synthesize complete answer

### Cross-Validation
1. Search for information
2. Fetch from multiple independent sources
3. Compare and validate information
4. Highlight consensus and disagreements
5. Cite all sources

### Visual-First Research
1. Find and analyze relevant images
2. Extract key concepts from visuals
3. Research those concepts
4. Connect visual and textual information
5. Provide integrated analysis

## Summary

This skill provides powerful capabilities by combining:
- **Vision AI** for image understanding (Read)
- **Web search** for finding information (WebSearch)
- **Content fetching** for detailed reading (WebFetch)

All without requiring external API keys or MCP server configuration.

Use these tools together creatively to solve complex research, debugging, and analysis tasks!

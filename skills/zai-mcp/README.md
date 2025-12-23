# Web and Vision Analysis Skill

Agent Skill that provides image analysis, web search, and web page reading capabilities using Claude Code's built-in tools.

## Features

- **Image Analysis**: Analyze images using Claude's vision AI (OCR, object detection, scene understanding)
- **Web Search**: Search the internet for current information
- **Web Page Reading**: Fetch and read web page content

**No MCP servers or API keys required!** This skill works immediately using Claude Code's native capabilities.

## Quick Start

1. **Load the Skill**

   The skill is ready to use immediately - no configuration needed!

2. **Use the Capabilities**

   Simply ask Claude to:
   - Analyze images and screenshots
   - Search the web for information
   - Fetch and summarize web pages
   - Combine these capabilities for complex research

## How It Works

This skill uses three built-in Claude Code tools:

- **Read tool** - For loading and analyzing images with Claude's vision
- **WebSearch tool** - For searching the internet
- **WebFetch tool** - For fetching web page content

## Structure

```
zai-mcp/
├── SKILL.md              # Main skill definition with instructions
├── README.md             # This file
├── references/
│   └── USAGE.md          # Detailed usage patterns and workflows
├── assets/
│   └── README.md         # Sample assets directory
└── scripts/
    └── README.md         # Helper scripts documentation
```

## Documentation

- **SKILL.md**: Main skill instructions, workflows, and examples
- **references/USAGE.md**: Detailed usage patterns for each capability
- **scripts/README.md**: Optional helper scripts

## Requirements

**None!** This skill uses Claude Code's built-in tools:
- No external dependencies
- No API keys needed
- No MCP servers to configure
- Works immediately upon loading

## Use Cases

### Image Analysis
```
User: "Analyze this screenshot and tell me what's wrong with the UI"
→ Uses Read tool with Claude's vision to analyze the image
→ Identifies UI issues, layout problems, accessibility concerns
→ Provides actionable feedback
```

### Web Research
```
User: "What are the latest developments in quantum computing?"
→ Uses WebSearch to find current information
→ Optionally uses WebFetch on key articles
→ Synthesizes information with source citations
```

### Content Reading
```
User: "Summarize this article: https://example.com/article"
→ Uses WebFetch to retrieve article content
→ Extracts main points and key arguments
→ Provides structured summary
```

### Combined Analysis
```
User: "Find information about this error [screenshot.png]"
→ Uses Read to analyze error screenshot and extract message
→ Uses WebSearch to find solutions
→ Uses WebFetch to get detailed troubleshooting guides
→ Provides comprehensive solution with sources
```

## Troubleshooting

### Image Analysis Issues
- **File not found**: Verify the image path is correct
- **Format unsupported**: Ensure image is PNG, JPG, GIF, or WebP
- **Image too large**: Consider resizing very large images

### Web Search Issues
- **No results**: Try rephrasing the query or using different keywords
- **Rate limited**: WebSearch may have usage limits; wait before retrying

### Web Fetch Issues
- **URL inaccessible**: Verify URL is correct and publicly accessible
- **Timeout**: Some sites may be slow; try again or use different source
- **Content blocked**: Some sites block automated access

## Contributing

To improve this skill:
1. Update SKILL.md with new patterns or examples
2. Add detailed workflows to references/USAGE.md
3. Create helper scripts for common operations
4. Add sample assets for testing

## License

Proprietary

## References

- [Agent Skills Specification](https://agentskills.io/specification)
- [Claude Code Documentation](https://docs.anthropic.com)

## Version

0.2 - Updated to use built-in tools (no MCP required)

## Author

skills-repo

## Advantages

**Why use this skill?**

1. **Zero Setup**: No API keys, no MCP servers, works immediately
2. **Privacy**: All processing within Claude Code environment
3. **Integrated**: Combines vision, search, and web reading seamlessly
4. **Flexible**: Adaptable workflows for research, debugging, analysis
5. **Reliable**: Uses Claude Code's stable built-in tools

## Support

For issues or questions:
- Check SKILL.md for detailed instructions
- Review references/USAGE.md for usage patterns
- Ensure Claude Code tools (Read, WebSearch, WebFetch) are available

# Z.ai MCP Integration Skill

Agent Skill for integrating z.ai MCP servers to provide image analysis, web search, and web page reading capabilities.

## Features

- **Image Analysis**: Analyze images using vision AI (OCR, object detection, scene understanding)
- **Web Search**: Search the internet for current information
- **Web Page Reading**: Fetch and read web page content

## Quick Start

1. **Configure MCP Server**

   Add to your `.mcp.json`:
   ```json
   {
     "mcpServers": {
       "zai": {
         "command": "npx",
         "args": ["-y", "@z.ai/mcp-server"],
         "env": {
           "ZAI_API_KEY": "your-api-key-here"
         }
       }
     }
   }
   ```

2. **Set API Key**

   Get your API key from [z.ai](https://z.ai) and either:
   - Add it directly to `.mcp.json` (not recommended for shared configs)
   - Set as environment variable: `export ZAI_API_KEY="your-key"`

3. **Use the Skill**

   Invoke the skill when you need:
   - Image analysis
   - Web searches
   - URL content fetching

## Structure

```
zai-mcp/
├── SKILL.md              # Main skill definition
├── README.md             # This file
├── config/
│   └── mcporter.json     # MCP server configuration
├── mcp/
│   └── README.md         # MCP setup instructions
├── references/
│   └── USAGE.md          # Detailed usage reference
├── assets/
│   └── README.md         # Sample assets (optional)
└── scripts/
    └── README.md         # Helper scripts (optional)
```

## Documentation

- **SKILL.md**: Main skill instructions and examples
- **references/USAGE.md**: Detailed usage patterns and workflows
- **mcp/README.md**: MCP server setup and configuration
- **scripts/README.md**: Helper scripts for setup and testing

## Requirements

- Node.js and npm (for npx)
- z.ai API key
- MCP server support in your environment

## Use Cases

### Image Analysis
```
User: "Analyze this screenshot and tell me what's wrong with the UI"
→ Uses z.ai vision to analyze the image
→ Identifies UI issues and provides feedback
```

### Web Research
```
User: "What are the latest developments in quantum computing?"
→ Searches the web using z.ai
→ Fetches relevant articles
→ Synthesizes information with sources
```

### Content Reading
```
User: "Summarize this article: https://example.com/article"
→ Fetches the article content
→ Analyzes any images in the article
→ Provides comprehensive summary
```

## Troubleshooting

### MCP Tools Not Available
- Verify z.ai MCP server is configured in `.mcp.json`
- Check that `ZAI_API_KEY` is set correctly
- Restart your Claude Code session

### API Key Issues
- Ensure API key is valid and not expired
- Check that environment variable has no extra spaces
- Verify API key has necessary permissions

### Tool Name Mismatches
Tool names may vary based on z.ai MCP server version. Common variations:
- Vision: `analyze_image`, `vision`, `image_analysis`
- Search: `search`, `web_search`, `internet_search`
- Fetch: `fetch_url`, `read_page`, `get_url`

## Contributing

To improve this skill:
1. Update SKILL.md with new patterns or examples
2. Add detailed workflows to references/USAGE.md
3. Create helper scripts for common operations
4. Add sample assets for testing

## License

Proprietary - See LICENSE file for details

## References

- [Agent Skills Specification](https://agentskills.io/specification)
- [mcporter Documentation](https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md)
- [Z.ai Documentation](https://z.ai) (check for actual documentation URL)
- [MCP Protocol](https://modelcontextprotocol.io)

## Version

0.1 - Initial release

## Author

skills-repo

## Support

For issues or questions:
- Check documentation in this directory
- Review MCP server configuration
- Verify API key and permissions
- Consult z.ai support resources

# Z.AI Vision Analysis Skill

Advanced image and video analysis using Z.AI vision APIs via mcporter CLI - no MCP server attachment needed.

## Features

- **UI to Code**: Convert UI screenshots to React/HTML/CSS code
- **OCR**: Extract text from screenshots and documents
- **Error Diagnosis**: Analyze error screenshots with actionable fixes
- **Diagram Understanding**: Interpret architecture, UML, ER diagrams, flowcharts
- **Data Visualization**: Analyze charts, dashboards, and graphs
- **UI Diff**: Compare UI versions and detect differences
- **Video Analysis**: Understand video scenes and content (≤8 MB)
- **General Analysis**: Open-ended image understanding

## Quick Start

1. **Set API Key**:
   ```bash
   export Z_AI_API_KEY="your-api-key-here"
   ```

2. **Use via Bash**:
   All tools use `npx mcporter call` commands - no MCP server setup!

3. **Choose the right tool**: See SKILL.md for 8 specialized vision tools

## Requirements

- Node.js ≥ v22.0.0
- Z.AI API key (GLM Coding Plan)
- mcporter (auto-installed via npx)

## Example Usage

```bash
# Diagnose an error screenshot
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool diagnose_error_screenshot \
  --args '{"image_path":"/path/to/error.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

## Documentation

- **SKILL.md**: Complete tool reference and workflows
- **references/**: Detailed usage patterns
- Get API key: https://z.ai

## Version

1.0 - Initial release

## License

Proprietary

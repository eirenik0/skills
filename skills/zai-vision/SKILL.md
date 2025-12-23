---
name: zai-vision
description: Advanced image and video analysis using Z.AI vision APIs via mcporter CLI (no MCP server attachment needed).
license: Proprietary
metadata:
  author: skills-repo
  version: "1.0"
---

# Z.AI Vision Analysis Skill

## When to use

- User needs advanced image analysis beyond Claude's built-in vision
- UI/UX screenshot analysis and conversion
- Error screenshot diagnosis
- Technical diagram interpretation (architecture, flowcharts, UML, ER diagrams)
- Data visualization analysis (charts, dashboards, graphs)
- UI comparison and diff checking
- Video analysis (scenes, moments, entities)
- OCR text extraction from screenshots and documents

## Instructions

This skill provides access to Z.AI's advanced vision APIs using `npx mcporter call` commands through Bash. **No MCP server configuration required** - just use Bash to call the APIs directly.

### Prerequisites

1. **Z.AI API Key**: Set environment variable `Z_AI_API_KEY=your_key`
2. **Node.js**: Version 22.0.0 or higher
3. **mcporter**: Automatically installed via npx

### Available Tools

#### 1. **ui_to_artifact**
Converts UI screenshots into code, prompts, specifications, or descriptions.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool ui_to_artifact \
  --args '{"image_url":"https://example.com/ui.png","output_type":"code"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Convert UI screenshots to HTML/CSS/React code
- Generate UI specifications from designs
- Create artifact descriptions from interfaces

#### 2. **extract_text_from_screenshot**
Performs OCR on screenshots to extract code, terminal output, documentation, and general text.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool extract_text_from_screenshot \
  --args '{"image_path":"/path/to/screenshot.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Extract code from screenshots
- Read terminal output from images
- OCR documentation or text-heavy images
- Convert image-based text to editable text

#### 3. **diagnose_error_screenshot**
Analyzes error snapshots and suggests actionable fixes.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool diagnose_error_screenshot \
  --args '{"image_path":"/path/to/error.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Debug error messages from screenshots
- Get actionable fixes for errors
- Understand stack traces in images
- Troubleshoot visual error indicators

#### 4. **understand_technical_diagram**
Interprets architecture diagrams, flowcharts, UML, ER diagrams, and system designs.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool understand_technical_diagram \
  --args '{"image_url":"https://example.com/diagram.png","diagram_type":"architecture"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Understand system architecture diagrams
- Interpret flowcharts and process diagrams
- Analyze UML class/sequence diagrams
- Parse ER diagrams and database schemas
- Explain technical system designs

#### 5. **analyze_data_visualization**
Reads charts and dashboards to identify insights and trends.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool analyze_data_visualization \
  --args '{"image_path":"/path/to/chart.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Analyze charts, graphs, and plots
- Extract insights from dashboards
- Identify trends in visualizations
- Read metrics from monitoring screens
- Interpret business intelligence displays

#### 6. **ui_diff_check**
Compares two UI screenshots to detect visual or implementation differences.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool ui_diff_check \
  --args '{"image_a":"/path/to/before.png","image_b":"/path/to/after.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Compare UI versions for differences
- QA visual regression testing
- Identify layout changes between designs
- Detect unintended UI modifications
- Review before/after UI updates

#### 7. **image_analysis**
General-purpose image understanding for cases not covered by specialized tools.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool image_analysis \
  --args '{"image_url":"https://example.com/image.png","query":"What is in this image?"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- General image understanding
- When other specialized tools don't fit
- Open-ended image analysis
- Multi-purpose visual inspection

#### 8. **video_analysis**
Inspects videos (local/remote ≤8 MB; MP4/MOV/M4V) to describe scenes, moments, and entities.

**Usage:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool video_analysis \
  --args '{"video_url":"https://example.com/video.mp4","analysis_type":"scenes"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**When to use:**
- Analyze video content and scenes
- Identify moments and entities in videos
- Understand video context
- Extract information from video files
- **Limit**: Videos must be ≤8 MB in MP4/MOV/M4V format

### Workflow

1. **Identify the task** - Choose the appropriate Z.AI vision tool
2. **Prepare image/video** - Ensure file is accessible (local path or URL)
3. **Set API key** - Verify `Z_AI_API_KEY` environment variable is set
4. **Execute mcporter call** - Use Bash tool to run the npx command
5. **Parse JSON response** - Extract and present results to user
6. **Handle errors** - If API call fails, inform user clearly

### Best Practices

1. **Choose the right tool**: Use specialized tools (ui_to_artifact, diagnose_error_screenshot, etc.) over generic image_analysis when possible
2. **Image quality**: Higher quality images produce better results
3. **File size limits**: Keep videos ≤8 MB
4. **Secure API key**: Use environment variable, never hardcode
5. **Error handling**: Wrap calls in error handling and inform user of issues
6. **Cost awareness**: Z.AI has usage limits (Lite: 5-hour vision pool, Pro: same pool)
7. **Local vs URL**: Both local file paths and URLs are supported for images

### API Key Setup

Users need to set up their Z.AI API key:

```bash
# Linux/Mac
export Z_AI_API_KEY="your-api-key-here"

# Windows PowerShell
$env:Z_AI_API_KEY="your-api-key-here"
```

Get API keys from: https://z.ai (requires GLM Coding Plan subscription)

### Usage Limits

- **Lite Plan**: 5-hour maximum prompt resource pool for vision understanding
- **Pro/Max Plans**: Same 5-hour vision resource pool
- Videos must be ≤8 MB
- Supported formats: Images (PNG, JPG, etc.), Videos (MP4, MOV, M4V)

### Error Handling

Common errors:
- **API Key missing**: Check `Z_AI_API_KEY` is set
- **Node version**: Ensure Node.js ≥ v22.0.0
- **File not found**: Verify image/video path
- **Rate limit**: Inform user of usage limits
- **Video too large**: Videos must be ≤8 MB
- **Unsupported format**: Check file format matches supported types

## Examples

### Example 1: Convert UI Screenshot to Code

**Input:**
- "Convert this UI screenshot to React code [ui-design.png]"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool ui_to_artifact \
  --args '{"image_path":"/path/to/ui-design.png","output_type":"react"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**Output:**
- Generated React component code
- Component structure and styling
- Props and state suggestions

### Example 2: Diagnose Error Screenshot

**Input:**
- "Why is this error happening? [error-screen.png]"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool diagnose_error_screenshot \
  --args '{"image_path":"/path/to/error-screen.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**Output:**
- Error message interpretation
- Root cause analysis
- Actionable fix suggestions
- Relevant debugging steps

### Example 3: Understand Architecture Diagram

**Input:**
- "Explain this system architecture diagram [arch-diagram.png]"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool understand_technical_diagram \
  --args '{"image_path":"/path/to/arch-diagram.png","diagram_type":"architecture"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**Output:**
- Component identification
- Data flow explanation
- System interaction description
- Architecture pattern recognition

### Example 4: Analyze Dashboard

**Input:**
- "What insights can you extract from this dashboard? [dashboard.png]"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool analyze_data_visualization \
  --args '{"image_path":"/path/to/dashboard.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**Output:**
- Key metrics identified
- Trends and patterns
- Anomalies or notable data points
- Insights and recommendations

### Example 5: Compare UI Versions

**Input:**
- "What changed between these two UI versions? [before.png] [after.png]"

**Actions:**
```bash
npx mcporter call \
  --server "@z_ai/mcp-server" \
  --tool ui_diff_check \
  --args '{"image_a":"/path/to/before.png","image_b":"/path/to/after.png"}' \
  --env Z_AI_API_KEY="$Z_AI_API_KEY"
```

**Output:**
- Visual differences identified
- Layout changes
- Color/styling modifications
- New/removed elements

## Notes

- **No MCP server attachment**: Uses mcporter CLI directly via Bash
- **API key required**: Z.AI API key from GLM Coding Plan
- **Node.js v22+**: Required for @z_ai/mcp-server
- **Specialized tools**: Use specific tools over generic image_analysis
- **Cost conscious**: Monitor usage against plan limits

## References

- [Z.AI Vision MCP Server Documentation](https://docs.z.ai/devpack/mcp/vision-mcp-server)
- [Z.AI NPM Package](https://www.npmjs.com/package/@z_ai/mcp-server)
- [mcporter Documentation](https://raw.githubusercontent.com/steipete/mcporter/refs/heads/main/README.md)
- [Agent Skills Specification](https://agentskills.io/specification)

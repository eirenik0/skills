# Scripts Directory

This directory contains helper scripts for the z.ai MCP skill.

## Potential Scripts

### setup.sh / setup.ps1
- Configure z.ai MCP server
- Set up environment variables
- Install dependencies

### test.sh / test.ps1
- Test MCP server connectivity
- Verify API key
- Check tool availability

### Example: setup.sh

```bash
#!/bin/bash
# Setup z.ai MCP server

echo "Setting up z.ai MCP server..."

# Check if API key is set
if [ -z "$ZAI_API_KEY" ]; then
  echo "ZAI_API_KEY not set. Please set it:"
  echo "  export ZAI_API_KEY='your-api-key'"
  exit 1
fi

# Test MCP server
echo "Testing z.ai MCP server..."
npx -y @z.ai/mcp-server --version

echo "Setup complete!"
```

### Example: test.sh

```bash
#!/bin/bash
# Test z.ai MCP server connectivity

echo "Testing z.ai MCP server..."

# Check environment
if [ -z "$ZAI_API_KEY" ]; then
  echo "❌ ZAI_API_KEY not set"
  exit 1
fi
echo "✓ ZAI_API_KEY is set"

# Test server
if npx -y @z.ai/mcp-server --version &> /dev/null; then
  echo "✓ MCP server is accessible"
else
  echo "❌ MCP server not accessible"
  exit 1
fi

echo "All tests passed!"
```

## Usage

Make scripts executable:
```bash
chmod +x scripts/*.sh
```

Run scripts:
```bash
./scripts/setup.sh
./scripts/test.sh
```

## Notes

- Keep scripts simple and well-documented
- Support both Unix (bash) and Windows (PowerShell)
- Handle errors gracefully
- Provide clear feedback to users

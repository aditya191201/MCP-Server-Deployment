# Screenshot MCP Server

A Model Context Protocol (MCP) server that enables Claude to capture screenshots of your screen.

## Features

- **Screen Capture**: Capture your current screen and share it directly with Claude
- **Optimized Images**: Screenshots are automatically compressed to JPEG format for efficient transfer
- **Simple Integration**: Easy to install and configure with Claude Desktop

## Requirements

- Python 3.13+
- macOS (for `pyautogui` screen capture support)
- [uv](https://docs.astral.sh/uv/) package manager (recommended)

## Installation

### Option 1: Install via uvx (Recommended)

No local installation required! Add directly to your Claude configuration.

### Option 2: Install from Source

```bash
git clone https://github.com/aditya191201/MCP-Server-Deployment.git
cd MCP-Server-Deployment
uv sync
```


## Configuration

### Claude Desktop

Add the following to your Claude Desktop configuration file:

**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "screenshot": {
      "command": "uvx",
      "args": [
        "--from",
        "git+https://github.com/aditya191201/MCP-Server-Deployment.git",
        "mcp-server"
      ]
    }
  }
}
```

### Local Development

If running from source:

```json
{
  "mcpServers": {
    "screenshot": {
      "command": "uv",
      "args": ["--directory", "/path/to/MCP-Server-Deployment", "run", "mcp-server"]
    }
  }
}
```


## Usage

Once configured, restart Claude Desktop. You can then ask Claude to capture your screen:

- "Take a screenshot of my screen"
- "Capture what's on my display"
- "Show me what's on my screen right now"

### Available Tools

| Tool | Description |
|------|-------------|
| `capture_screenshot` | Captures the current screen and returns a JPEG image |

## Permissions

On macOS, you'll need to grant screen recording permissions:

1. Go to **System Preferences** → **Privacy & Security** → **Screen Recording**
2. Enable permissions for your terminal app (Terminal, iTerm2, etc.) or Claude Desktop

## Troubleshooting

### "Screen capture failed" error
- Ensure screen recording permissions are granted
- Try restarting Claude Desktop after granting permissions

### Server not appearing in Claude
- Verify the configuration file syntax is valid JSON
- Check that `uvx` is installed and accessible from your PATH
- Restart Claude Desktop completely

## Development

```bash
# Clone the repository
git clone https://github.com/aditya191201/MCP-Server-Deployment.git
cd MCP-Server-Deployment

# Create virtual environment and install dependencies
uv sync

# Run the server locally
uv run mcp-server
```

## License

MIT

## Author

Aditya Deshpande - [@aditya191201](https://github.com/aditya191201)

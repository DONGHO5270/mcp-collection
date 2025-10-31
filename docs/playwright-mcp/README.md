# playwright-mcp Server

> Official Microsoft browser automation: accessibility-tree based, fast, and vision-free

[![GitHub](https://img.shields.io/badge/GitHub-microsoft%2Fplaywright--mcp-blue)](https://github.com/microsoft/playwright-mcp)
[![NPM](https://img.shields.io/badge/NPM-%40playwright%2Fmcp-red)](https://www.npmjs.com/package/@playwright/mcp)
[![Status](https://img.shields.io/badge/Status-Official-green)]()

## 📌 What is playwright-mcp?

**playwright-mcp** is Microsoft's official MCP server that provides AI assistants with professional browser automation capabilities using Playwright. Unlike screenshot-based approaches, it uses Playwright's accessibility tree for deterministic, structured interactions—enabling LLMs to navigate, click, type, and scrape web pages without vision models.

### Key Features

- **Accessibility Tree Based**: No screenshots, no pixels—pure structured data
- **Fast & Lightweight**: Efficient automation without visual processing overhead
- **Multi-Browser Support**: Chrome, Firefox, WebKit, MS Edge
- **LLM-Friendly**: Deterministic tool application, no ambiguity
- **Advanced Capabilities**: Vision mode, PDF export, network interception
- **Safe Execution**: Sandboxed browser contexts with timeout controls

### Use Cases

✅ **E2E Testing**: Automated end-to-end testing workflows
✅ **Web Scraping**: Extract data from dynamic websites
✅ **Form Automation**: Fill and submit web forms programmatically
✅ **UI Testing**: Validate user interfaces across browsers
✅ **Screenshot Capture**: Take full-page or element screenshots

### When to Use

- When need browser automation for AI agents
- When testing web applications across browsers
- When scraping dynamic JavaScript-heavy sites
- When automating repetitive web tasks
- When integrating browser capabilities into AI workflows

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version

### Step 1: Open Configuration

**macOS/Linux**:
```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**Windows**:
```bash
code %APPDATA%\Claude\claude_desktop_config.json
```

### Step 2: Add Configuration

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "-y",
        "@playwright/mcp@latest"
      ]
    }
  }
}
```

**With custom browser**:
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "-y",
        "@playwright/mcp@latest",
        "--browser", "chrome"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "playwright" is listed

### Step 4: Test Installation

In Claude Desktop:
```
Navigate to https://example.com and click the "More information" link
```

Claude will use `browser_navigate` and `browser_click` tools to automate the browser.

---

## ⚙️ Configuration

### Command-Line Options

| Option | Values | Description |
|--------|--------|-------------|
| `--browser` | chrome, firefox, webkit, msedge | Browser engine (default: chrome) |
| `--caps` | vision, pdf | Additional capabilities |
| `--headless` | true, false | Headless mode (default: true) |

Example with options:
```json
{
  "args": [
    "-y",
    "@playwright/mcp@latest",
    "--browser", "firefox",
    "--caps", "vision,pdf"
  ]
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Browser not found"

**Symptoms**: Error "Executable doesn't exist"

**Solutions**:

1. **Install browsers**:
   ```bash
   npx playwright install
   ```

2. **Install specific browser**:
   ```bash
   npx playwright install chrome
   ```

### Issue 2: Timeout errors

**Symptoms**: "Navigation timeout" or "Element not found"

**Solutions**:

1. **Increase timeout** in script or wait for elements:
   - Use `browser_wait_for` tool before interactions

2. **Check network speed**: Slow connections need longer timeouts

---

## 🔄 Alternative Methods

### Method 1: Global Installation

```bash
npm install -g @playwright/mcp
playwright-mcp
```

Configure with:
```json
{
  "command": "playwright-mcp"
}
```

**Pros**: Faster startup
**Cons**: Manual version management

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `browser_navigate` | Navigate to URL |
| `browser_snapshot` | Capture accessibility tree |
| `browser_click` | Click element by ref |
| `browser_type` | Type text into input |
| `browser_take_screenshot` | Capture screenshot (full/element) |
| `browser_evaluate` | Execute JavaScript |
| `browser_wait_for` | Wait for condition |
| `browser_fill_form` | Fill multiple form fields |
| `browser_select_option` | Select dropdown option |
| `browser_tabs` | Manage browser tabs |
| `browser_console_messages` | Get console output |
| `browser_network_requests` | Monitor network traffic |

---

## 🎯 Usage Examples

### Example 1: Web Scraping

**Prompt**:
```
Go to https://news.ycombinator.com and extract the top 5 post titles
```

**Result**: Navigates, snapshots accessibility tree, extracts titles from structured data

### Example 2: Form Automation

**Prompt**:
```
Fill the login form at https://example.com/login with email "test@example.com" and password "demo123"
```

**Result**: Uses `browser_fill_form` to populate fields and submit

---

## 🔗 Related Resources

- **Official Repository**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)
- **NPM Package**: [@playwright/mcp](https://www.npmjs.com/package/@playwright/mcp)
- **Playwright Docs**: [playwright.dev](https://playwright.dev)
- **GitHub Copilot Integration**: Built-in support

---

## 💡 Tips & Best Practices

1. **Install browsers first** before testing automation
2. **Use accessibility snapshots** instead of screenshots for better performance

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Browsers installed (`npx playwright install`)
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "playwright"

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/microsoft/playwright-mcp/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (@playwright/mcp)
**Status**: ✅ Official Microsoft Release
**Release Date**: March 2025

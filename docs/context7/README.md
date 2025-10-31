# context7 MCP Server

> Up-to-date, version-specific documentation and code examples for libraries

[![GitHub](https://img.shields.io/badge/GitHub-upstash%2Fcontext7-blue)](https://github.com/upstash/context7)
[![NPM](https://img.shields.io/badge/NPM-%40upstash%2Fcontext7--mcp-red)](https://www.npmjs.com/package/@upstash/context7-mcp)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is context7?

**context7** is an MCP server by Upstash that provides up-to-date, version-specific documentation and code examples for libraries directly into your prompt. It pulls fresh documentation from official sources and injects it into your context, ensuring you always work with current APIs and best practices.

### Key Features

- **Up-to-date Documentation**: Real-time docs from official sources
- **Version-Specific**: Matches exact library versions you're using
- **Multi-Language Support**: Works with JavaScript, Python, Go, Rust, and more
- **Private Repos**: Access private documentation with API key (optional)
- **Zero Configuration**: Works immediately with "use context7" prompt

### Use Cases

✅ **API Documentation**: Get current API reference for any library
✅ **Code Examples**: Real-world usage patterns from official docs
✅ **Migration Guides**: Version-specific upgrade instructions
✅ **Best Practices**: Latest recommendations from maintainers
✅ **Private Libraries**: Access internal documentation with API key

### When to Use

- When working with external libraries and need current docs
- When API documentation isn't locally cached
- When unsure about version-specific features
- When migrating between library versions
- When need examples beyond basic tutorials

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version
- **API Key**: Optional (free tier available)

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

**Basic setup** (free tier):

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ]
    }
  }
}
```

**With API Key** (higher rate limits, private repos):

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp",
        "--api-key",
        "YOUR_API_KEY"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "context7" is listed

### Step 4: Test Installation

In Claude Desktop:

```
use context7

How do I create a React component with TypeScript?
```

If working correctly, Claude will fetch React + TypeScript documentation and provide current examples.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CONTEXT7_API_KEY` | None | API key for higher rate limits |
| `CONTEXT7_CACHE_TTL` | `3600` | Cache duration in seconds |
| `LOG_LEVEL` | `info` | Logging verbosity |

### Advanced Configuration

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp", "--api-key", "YOUR_API_KEY"],
      "env": {
        "CONTEXT7_CACHE_TTL": "7200",
        "LOG_LEVEL": "debug"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "context7 not available"

**Symptoms**: Claude doesn't recognize context7 tool

**Solutions**:

1. **Verify NPM cache**:
   ```bash
   npx clear-npx-cache
   npx -y @upstash/context7-mcp
   ```

2. **Check internet connection** (NPX downloads on first run)

3. **Try alternative runtime** (see Alternative Methods)

### Issue 2: Rate limit exceeded

**Symptoms**: Error "Rate limit reached, try again later"

**Cause**: Free tier limits exceeded

**Solutions**:

1. **Get API key**: Sign up at [upstash.com](https://upstash.com)

2. **Add API key to config**:
   ```json
   {
     "args": ["-y", "@upstash/context7-mcp", "--api-key", "YOUR_KEY"]
   }
   ```

### Issue 3: Outdated documentation

**Symptoms**: Documentation doesn't match library version

**Cause**: Cache outdated or version mismatch

**Solutions**:

1. **Clear cache**:
   ```json
   {
     "env": {
       "CONTEXT7_CACHE_TTL": "0"
     }
   }
   ```

2. **Specify version in prompt**: "use context7 for React 18.2.0"

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @upstash/context7-mcp --client claude
```

**Pros**: Automated setup
**Cons**: Requires Smithery CLI

### Method 2: Bunx (for Bun projects)

```json
{
  "mcpServers": {
    "context7": {
      "command": "bunx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### Method 3: Deno Runtime

```json
{
  "mcpServers": {
    "context7": {
      "command": "deno",
      "args": ["run", "--allow-net", "npm:@upstash/context7-mcp"]
    }
  }
}
```

### Method 4: Windows CMD

```json
{
  "mcpServers": {
    "context7": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@upstash/context7-mcp"]
    }
  }
}
```

---

## 🎯 Usage Example

**Prompt**:
```
use context7

How do I use React 18's useTransition hook?
```

**Result**: Claude fetches React 18 docs and provides current usage examples with useTransition, including:
- Hook signature and parameters
- Real-world usage patterns
- Performance considerations
- Best practices for concurrent rendering

**Supported Languages**: JavaScript/TypeScript (React, Vue, Next.js, Express), Python (Django, Flask, FastAPI), Go (Gin, Echo), Rust (Actix, Rocket), Java (Spring), Ruby (Rails), PHP (Laravel)

---

## 🔗 Related Resources

- **Official Repository**: [upstash/context7](https://github.com/upstash/context7)
- **NPM Package**: [@upstash/context7-mcp](https://www.npmjs.com/package/@upstash/context7-mcp)
- **Get API Key**: [upstash.com](https://upstash.com)
- **Blog Post**: [Context7 MCP Announcement](https://upstash.com/blog/context7-mcp)

---

## 💡 Tips & Best Practices

1. **Always specify version** for critical projects (e.g., "React 18.2.0")
2. **Use API key** for production/heavy usage
3. **Test with "use context7"** in prompt to verify installation

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Internet connection active (for NPX)
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "context7"
- [ ] Prompt includes "use context7"

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/upstash/context7/issues)
- **Documentation**: [Upstash Docs](https://upstash.com/docs)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (@upstash/context7-mcp)
**Status**: ✅ Stable

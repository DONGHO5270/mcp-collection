# code-context-provider-mcp

> Code context and symbol analysis with WebAssembly Tree-sitter parsers

[![GitHub](https://img.shields.io/badge/GitHub-AB498%2Fcode--context--provider--mcp-blue)](https://github.com/AB498/code-context-provider-mcp)
[![NPM](https://img.shields.io/badge/NPM-code--context--provider--mcp-red)](https://www.npmjs.com/package/code-context-provider-mcp)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is code-context-provider-mcp?

**code-context-provider-mcp** is an MCP server that provides comprehensive code context and analysis for AI assistants. It extracts directory structures and code symbols (functions, variables, classes, imports, exports) using WebAssembly Tree-sitter parsers with **zero native dependencies**, making it lightweight and portable.

### Key Features

- **Zero Native Dependencies**: Pure WebAssembly implementation
- **AST-Based Analysis**: Tree-sitter parsers for accurate symbol extraction
- **Multi-Language Support**: JavaScript/TypeScript (.js, .jsx, .ts, .tsx) and Python (.py)
- **Directory Structure**: Complete project tree with depth control
- **Symbol Extraction**: Functions, variables, classes, imports, exports
- **Configurable Depth**: Control analysis depth for large projects (default: 5 levels)

### Use Cases

✅ **Project Overview**: Get complete codebase structure at a glance
✅ **Symbol Discovery**: Find all functions, classes, and variables
✅ **Dependency Analysis**: Extract imports and exports for dependency mapping
✅ **Code Navigation**: Quickly locate symbols across files
✅ **Refactoring Support**: Identify symbol usage before changes

### When to Use

- When need comprehensive project structure overview
- When analyzing codebase for refactoring
- When identifying dependencies and imports
- When navigating large codebases with AI assistance
- When building code analysis tools

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
    "code-context-provider": {
      "command": "npx",
      "args": [
        "-y",
        "code-context-provider-mcp@latest"
      ]
    }
  }
}
```

**With custom max depth**:
```json
{
  "mcpServers": {
    "code-context-provider": {
      "command": "npx",
      "args": ["-y", "code-context-provider-mcp@latest"],
      "env": {
        "MAX_DEPTH": "10"
      }
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "code-context-provider" is listed

### Step 4: Test Installation

In Claude Desktop:

```
Analyze the structure of my project at C:/Users/YourName/Projects/my-app
```

Claude will use `get_code_context` tool to analyze directory structure and code symbols.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `MAX_DEPTH` | `5` | Maximum directory depth for analysis |
| `INCLUDE_SYMBOLS` | `true` | Extract code symbols (functions, classes) |
| `ANALYZE_JS` | `true` | Analyze JavaScript/TypeScript files |
| `ANALYZE_PY` | `true` | Analyze Python files |

### Example Configuration

**Large projects** (limit depth):
```json
{
  "mcpServers": {
    "code-context-provider": {
      "command": "npx",
      "args": ["-y", "code-context-provider-mcp@latest"],
      "env": {
        "MAX_DEPTH": "3"
      }
    }
  }
}
```

**Symbol extraction only**:
```json
{
  "env": {
    "MAX_DEPTH": "10",
    "INCLUDE_SYMBOLS": "true"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "WASM parser not loaded"

**Symptoms**: Error loading Tree-sitter WASM parsers

**Solutions**:

1. **Clear NPM cache**:
   ```bash
   npx clear-npx-cache
   npx -y code-context-provider-mcp@latest
   ```

2. **Check internet connection** (parsers download on first run)

3. **Manual setup**:
   ```bash
   npm install -g code-context-provider-mcp
   npm run setup
   ```

### Issue 2: Analysis too slow

**Symptoms**: Tool takes >30 seconds for large projects

**Cause**: MAX_DEPTH too high or project too large

**Solutions**:

1. **Reduce depth**:
   ```json
   {
     "env": {
       "MAX_DEPTH": "3"
     }
   }
   ```

2. **Analyze specific subdirectory** instead of root

3. **Exclude large folders** (node_modules, dist, build)

### Issue 3: Symbols not extracted

**Symptoms**: Directory structure shown but no functions/classes

**Cause**: Language not supported or INCLUDE_SYMBOLS disabled

**Solutions**:

1. **Verify supported language**: JS, TS, JSX, TSX, PY only

2. **Enable symbols**:
   ```json
   {
     "env": {
       "INCLUDE_SYMBOLS": "true"
     }
   }
   ```

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @AB498/code-context-provider-mcp --client claude
```

**Pros**: Automated setup
**Cons**: Requires Smithery CLI

### Method 2: Global Installation

```bash
npm install -g code-context-provider-mcp
```

Configure with `"command": "code-context-provider-mcp"`

---

## 📚 Available Tools

### `get_code_context`

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `absolutePath` | string | required | Absolute path to analyze |
| `maxDepth` | number | 5 | Maximum directory depth |
| `includeSymbols` | boolean | true | Extract code symbols |
| `symbolType` | string | "all" | functions, variables, classes, imports, exports, all |

**Returns**: Directory tree, file counts, code symbols

---

## 🎯 Usage Example

**Prompt**:
```
Analyze the structure of my React project at C:/Projects/my-app/src
```

**Result**: Directory tree with components/, hooks/, utils/. Shows 15 files, 11 functions, 1 class, 8 imports, 3 exports with per-file symbol counts

---

## 🔗 Related Resources

- **Official Repository**: [AB498/code-context-provider-mcp](https://github.com/AB498/code-context-provider-mcp)
- **NPM Package**: [code-context-provider-mcp](https://www.npmjs.com/package/code-context-provider-mcp)
- **Tree-sitter**: [tree-sitter.github.io](https://tree-sitter.github.io)

---

## 💡 Tips & Best Practices

1. **Start with maxDepth=3** for large projects, increase if needed
2. **Analyze specific folders** (src/, lib/) to avoid node_modules

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Internet connection active (WASM parsers download)
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "code-context-provider"
- [ ] Path is absolute, not relative

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/AB498/code-context-provider-mcp/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (code-context-provider-mcp)
**Status**: ✅ Stable

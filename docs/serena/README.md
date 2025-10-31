# serena MCP Server

> Open-source coding agent toolkit: semantic code understanding, memory persistence, and LSP integration

[![GitHub](https://img.shields.io/badge/GitHub-oraios%2Fserena-blue)](https://github.com/oraios/serena)
[![Status](https://img.shields.io/badge/Status-Open--Source-green)]()

## 📌 What is serena?

**serena** is an open-source MCP server developed by Oraios AI that transforms LLMs into full-fledged coding agents. It provides semantic code retrieval, project memory persistence, and Language Server Protocol (LSP) integration—enabling AI assistants to understand codebases deeply, remember context across sessions, and maintain 70% lower token usage.

### Key Features

- **Project Memory System**: Persistent knowledge storage in `.serena/memories/`
- **Semantic Code Search**: Find code by meaning, not just keywords
- **LSP Integration**: Real-time code intelligence (autocomplete, diagnostics)
- **Symbol Navigation**: Jump to definitions, find references
- **Context Persistence**: Remember progress across sessions
- **Token Efficiency**: Save up to 70% tokens vs standard approaches
- **Task Continuation**: Resume long tasks from saved memories

### Use Cases

✅ **Long-Running Projects**: Maintain context across multiple sessions
✅ **Codebase Understanding**: Semantic search and navigation
✅ **Refactoring Support**: Find all references before changes
✅ **Code Quality**: Real-time diagnostics and suggestions
✅ **Token Optimization**: Reduce costs with efficient memory system

### When to Use

- When working on large, complex codebases
- When need context persistence across sessions
- When approaching Claude Code token limits
- When performing semantic code searches
- When refactoring or analyzing dependencies

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/oraios/serena.git
cd serena
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Build Project

```bash
npm run build
```

### Step 4: Configure Claude Desktop

**macOS/Linux**:
```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**Windows**:
```bash
code %APPDATA%\Claude\claude_desktop_config.json
```

Add configuration:

```json
{
  "mcpServers": {
    "serena": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/serena/dist/index.js"
      ]
    }
  }
}
```

### Step 5: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "serena" is listed

### Step 6: Test Installation & Onboarding

In Claude Desktop:
```
Initialize Serena for my project at C:/Projects/my-app
```

Serena performs **onboarding**: scans codebase, creates memories in `.serena/memories/`, stores project structure for future use.

---

## ⚙️ Configuration

### Memory Location

Memories stored in: `.serena/memories/` (project root)

**Files created**:
- `project_structure.md` - Directory tree, key files
- `code_patterns.md` - Common patterns, conventions
- `dependencies.md` - Package dependencies
- `task_progress.md` - Current work state

### LSP Settings (Optional)

Configure language servers:
```json
{
  "env": {
    "LSP_TYPESCRIPT": "enabled",
    "LSP_PYTHON": "enabled"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Onboarding failed"

**Symptoms**: Error during initial project scan

**Solutions**:

1. **Check permissions**: Ensure read access to project directory

2. **Verify Node.js**: Must be v18+

3. **Check project size**: Very large projects (>10K files) may timeout

### Issue 2: Memory files not created

**Symptoms**: `.serena/memories/` directory missing

**Solutions**:

1. **Create manually**:
   ```bash
   mkdir -p .serena/memories
   ```

2. **Run onboarding again**: "Initialize Serena for this project"

---

## 🔄 Alternative Methods

### Method 1: NPM Global Install (if available)

```bash
npm install -g serena-mcp
serena-mcp
```

**Pros**: Easier updates
**Cons**: Check if package exists on npm

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `onboarding` | Initialize project memory |
| `find_symbol` | Search code by semantic meaning |
| `find_references` | Find all references to symbol |
| `go_to_definition` | Jump to symbol definition |
| `list_memories` | List all stored memories |
| `write_memory` | Save current progress |
| `read_memory` | Load previous progress |
| `get_diagnostics` | Get LSP diagnostics |
| `semantic_search` | Semantic code search |

---

## 🎯 Usage Examples

### Example 1: Semantic Search

**Prompt**:
```
Find all functions that handle user authentication
```

**Result**: Returns functions with semantic meaning related to authentication, not just keyword matches

### Example 2: Task Continuation

**Session 1**:
```
Create a memory of current refactoring progress
```

**Session 2** (new conversation):
```
Read the refactoring memory and continue where we left off
```

**Result**: Loads previous context, resumes work seamlessly

---

## 🔗 Related Resources

- **Official Repository**: [oraios/serena](https://github.com/oraios/serena)
- **Release Date**: April 5, 2025
- **Oraios AI**: [oraios.ai](https://oraios.ai)

---

## 💡 Tips & Best Practices

1. **Run onboarding first** for new projects to build memory
2. **Create memory snapshots** before hitting token limits

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] `npm install` completed
- [ ] `npm run build` successful
- [ ] Absolute path in config
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "serena"
- [ ] `.serena/memories/` directory exists

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/oraios/serena/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (Open Source)
**Status**: ✅ Stable
**Release Date**: April 5, 2025

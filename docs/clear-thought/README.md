# clear-thought MCP Server

> Deep sequential analysis with branching, revision, and memory management capabilities

[![GitHub](https://img.shields.io/badge/GitHub-ThinkFar%2Fclear--thought--mcp-blue)](https://github.com/ThinkFar/clear-thought-mcp)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is clear-thought?

**clear-thought** is an MCP (Model Context Protocol) server that enables Claude to perform structured, sequential thinking with advanced features like thought branching, revision tracking, and persistent memory management.

### Key Features

- **Sequential Thinking**: Step-by-step reasoning with numbered thoughts
- **Thought Branching**: Explore alternative reasoning paths
- **Revision Tracking**: Revise and refine previous thoughts
- **Memory Management**: Store and retrieve reasoning sessions
- **Mental Models**: Apply structured frameworks (First Principles, Opportunity Cost, etc.)
- **Debugging Approaches**: Systematic problem-solving (Binary Search, Root Cause Analysis, etc.)

### Use Cases

✅ **Complex Problem Solving**: Break down multi-step problems systematically
✅ **Decision Making**: Explore multiple decision paths with branching
✅ **Code Architecture**: Think through system design with First Principles
✅ **Debugging**: Apply systematic debugging approaches (Binary Search, Divide & Conquer)
✅ **Analysis**: Structured analysis with mental models (SWOT, Issue Trees, Fishbone)

### When to Use

- When you need Claude to "think out loud" step-by-step
- When problems require exploring multiple solution paths
- When you want to track reasoning history across sessions
- When systematic mental models would improve analysis quality

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version
- **Git**: For cloning the repository

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/ThinkFar/clear-thought-mcp.git
cd clear-thought-mcp
```

### Step 2: Install Dependencies

```bash
npm install
```

**Expected output**:
```
added 47 packages in 3s
```

If you see dependency warnings, they are usually safe to ignore unless they mention security vulnerabilities.

### Step 3: Build TypeScript

```bash
npm run build
```

**Expected output**:
```
> clear-thought-mcp@1.0.0 build
> tsc
```

This compiles TypeScript files to JavaScript in the `dist/` folder.

### Step 4: Configure Claude Desktop

Open your Claude Desktop configuration file:

**macOS/Linux**:
```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**Windows**:
```bash
code %APPDATA%\Claude\claude_desktop_config.json
```

Add the following configuration:

```json
{
  "mcpServers": {
    "clear-thought": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/clear-thought-mcp/dist/index.js"
      ],
      "env": {
        "MEMORY_DIR": "C:/Users/YourUsername/Documents/mcp-servers/clear-thought-mcp/.memory"
      }
    }
  }
}
```

**Important**:
- Replace `C:/Users/YourUsername/` with your actual user path
- Use forward slashes `/` even on Windows
- The `MEMORY_DIR` is optional (defaults to `./.memory`)

### Step 5: Restart Claude Desktop

1. Quit Claude Desktop completely (not just close window)
2. Relaunch Claude Desktop
3. Check the MCP icon in the bottom-right corner
4. You should see "clear-thought" listed

### Step 6: Verify Installation

In Claude Desktop, type:

```
Use sequential thinking to analyze: What are the benefits of TypeScript?
```

If configured correctly, Claude will use the `sequentialthinking` tool and show numbered thoughts.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `MEMORY_DIR` | `./.memory` | Directory for storing thought sessions |
| `MAX_THOUGHTS` | `50` | Maximum thoughts per session |
| `ENABLE_BRANCHING` | `true` | Allow thought branching |
| `LOG_LEVEL` | `info` | Logging level (debug/info/warn/error) |

### Advanced Configuration

**Enable Debug Logging**:
```json
{
  "mcpServers": {
    "clear-thought": {
      "command": "node",
      "args": ["C:/path/to/clear-thought-mcp/dist/index.js"],
      "env": {
        "LOG_LEVEL": "debug"
      }
    }
  }
}
```

**Increase Thought Limit**:
```json
{
  "env": {
    "MAX_THOUGHTS": "100"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "clear-thought server not found"

**Symptoms**: Claude Desktop doesn't show clear-thought in MCP list

**Causes**:
- Path in `claude_desktop_config.json` is incorrect
- TypeScript not compiled (missing `dist/` folder)
- Configuration file has JSON syntax errors

**Solutions**:

1. **Verify path exists**:
   ```bash
   # Check if dist/index.js exists
   ls -la ~/Documents/mcp-servers/clear-thought-mcp/dist/index.js
   ```

2. **Rebuild project**:
   ```bash
   cd ~/Documents/mcp-servers/clear-thought-mcp
   npm run build
   ```

3. **Validate JSON syntax**:
   - Use [JSONLint](https://jsonlint.com/) to check config file
   - Common errors: missing commas, trailing commas, unescaped backslashes

4. **Check Claude logs** (macOS):
   ```bash
   tail -f ~/Library/Logs/Claude/mcp*.log
   ```

### Issue 2: "MODULE_NOT_FOUND" errors

**Symptoms**:
```
Error: Cannot find module '@modelcontextprotocol/sdk'
```

**Solutions**:

1. **Reinstall dependencies**:
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```

2. **Clear npm cache**:
   ```bash
   npm cache clean --force
   npm install
   ```

3. **Check Node version**:
   ```bash
   node --version  # Should be v18+
   ```

### Issue 3: Permission denied (macOS/Linux)

**Symptoms**:
```
EACCES: permission denied, mkdir '.memory'
```

**Solutions**:

1. **Fix directory permissions**:
   ```bash
   chmod 755 ~/Documents/mcp-servers/clear-thought-mcp
   mkdir -p ~/Documents/mcp-servers/clear-thought-mcp/.memory
   chmod 755 ~/Documents/mcp-servers/clear-thought-mcp/.memory
   ```

2. **Change memory directory**:
   ```json
   {
     "env": {
       "MEMORY_DIR": "~/Documents/clear-thought-memory"
     }
   }
   ```

### Issue 4: Tools not appearing in Claude

**Symptoms**: clear-thought listed in MCP, but tools don't work

**Causes**:
- Server crashed during initialization
- Environment variables not set correctly
- Conflicting MCP servers

**Solutions**:

1. **Check server logs**:
   ```bash
   tail -f ~/Library/Logs/Claude/mcp-clear-thought.log
   ```

2. **Test standalone**:
   ```bash
   node ~/Documents/mcp-servers/clear-thought-mcp/dist/index.js
   # Should output: "Clear Thought MCP Server running..."
   ```

3. **Disable other MCP servers temporarily** to test isolation

---

## 🔄 Alternative Methods

### Method 1: Using npx (No Installation)

If you prefer not to clone the repository:

```json
{
  "mcpServers": {
    "clear-thought": {
      "command": "npx",
      "args": [
        "-y",
        "clear-thought-mcp"
      ]
    }
  }
}
```

**Pros**: No manual git clone or build
**Cons**: Slower startup (downloads on first run), requires npm registry access

### Method 2: Docker Container

For isolated environment:

```bash
# Create Dockerfile
cat > Dockerfile <<EOF
FROM node:18-alpine
WORKDIR /app
RUN git clone https://github.com/ThinkFar/clear-thought-mcp.git .
RUN npm install && npm run build
CMD ["node", "dist/index.js"]
EOF

# Build and run
docker build -t clear-thought-mcp .
docker run -p 3000:3000 clear-thought-mcp
```

Then configure Claude to connect via HTTP (if supported).

### Method 3: Global npm Installation

```bash
# Install globally
npm install -g clear-thought-mcp

# Configure
{
  "mcpServers": {
    "clear-thought": {
      "command": "clear-thought-mcp"
    }
  }
}
```

**Note**: Not all MCP servers support global installation. Check repository README.

---

## 📚 Available Tools

Once installed, clear-thought provides these tools to Claude:

### 1. `sequentialthinking`
Sequential thought process with branching and revision

**Parameters**:
- `thought` (string): Current thought content
- `thoughtNumber` (number): Position in sequence
- `totalThoughts` (number): Expected total thoughts
- `nextThoughtNeeded` (boolean): Whether to continue
- `branchId` (string, optional): Branch identifier
- `isRevision` (boolean, optional): Is this a revision?

### 2. `mentalmodel`
Apply structured mental models

**Models**:
- `first_principles`: Break down to fundamental truths
- `opportunity_cost`: Evaluate trade-offs
- `pareto_principle`: 80/20 analysis
- `occams_razor`: Simplest explanation

### 3. `debuggingapproach`
Systematic debugging strategies

**Approaches**:
- `binary_search`: Divide and conquer
- `root_cause_analysis`: Find underlying causes
- `delta_debugging`: Isolate changes
- `log_analysis`: Pattern detection

---

## 🎯 Usage Examples

### Example 1: Sequential Problem Solving

**Prompt**:
```
Use sequential thinking to plan a React component refactoring
```

**Result**: Claude will use `sequentialthinking` tool to break down the task into numbered steps with clear reasoning.

### Example 2: First Principles Analysis

**Prompt**:
```
Apply first principles thinking to analyze whether we should use GraphQL or REST
```

**Result**: Claude will use `mentalmodel` with `first_principles` to break down assumptions.

### Example 3: Debugging Strategy

**Prompt**:
```
Use binary search debugging to find why tests are failing
```

**Result**: Claude will apply `debuggingapproach` with `binary_search` to systematically isolate the issue.

---

## 🔗 Related Resources

- **Official Repository**: [ThinkFar/clear-thought-mcp](https://github.com/ThinkFar/clear-thought-mcp)
- **MCP Documentation**: [modelcontextprotocol.io](https://modelcontextprotocol.io)
- **Claude Desktop Setup**: [Anthropic Docs](https://docs.anthropic.com)

---

## 💡 Tips & Best Practices

1. **Start with thoughtNumber=1**: Always begin sequential thinking from 1
2. **Set realistic totalThoughts**: Estimate 5-10 for most tasks
3. **Use branching for exploration**: When uncertain, create branches to explore options
4. **Memory persists across sessions**: Previous thinking sessions are stored in `.memory/`
5. **Combine with other MCP servers**: Works well with code-context-provider, github-mcp, etc.

---

## 🐛 Troubleshooting Checklist

Before reporting issues, verify:

- [ ] Node.js version is 18.0.0+
- [ ] Repository is cloned and `npm install` completed
- [ ] `npm run build` ran successfully
- [ ] Path in `claude_desktop_config.json` is absolute and correct
- [ ] JSON syntax is valid (no trailing commas, quotes escaped)
- [ ] Claude Desktop was fully restarted (not just window closed)
- [ ] MCP icon shows "clear-thought" in the list
- [ ] Logs don't show errors: `~/Library/Logs/Claude/mcp*.log`

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/ThinkFar/clear-thought-mcp/issues)
- **Discussions**: [GitHub Discussions](https://github.com/ThinkFar/clear-thought-mcp/discussions)
- **Premium Support**: Available with [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: 1.0.0
**Status**: ✅ Stable

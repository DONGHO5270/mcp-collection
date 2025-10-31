# sequential-thinking-tools MCP Server

> Dynamic, reflective problem-solving through structured step-by-step thinking

[![GitHub](https://img.shields.io/badge/GitHub-modelcontextprotocol%2Fservers-blue)](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)
[![NPM](https://img.shields.io/badge/NPM-%40modelcontextprotocol%2Fserver--sequential--thinking-red)](https://www.npmjs.com/package/@modelcontextprotocol/server-sequential-thinking)
[![Status](https://img.shields.io/badge/Status-Official-green)]()

## 📌 What is sequential-thinking-tools?

**sequential-thinking-tools** is an official Anthropic MCP server that enables Claude to break down complex problems into manageable steps with built-in support for revision and course correction. Unlike simple chain-of-thought, this tool allows dynamic adjustment of the thinking process as new information emerges.

### Key Features

- **Step-by-Step Breakdown**: Decompose complex problems into sequential steps
- **Dynamic Revision**: Adjust reasoning mid-process as understanding evolves
- **Context Maintenance**: Keep track of progress across multiple steps
- **Irrelevant Filtering**: Focus on relevant information, skip noise
- **Planning Support**: Design with room for iteration and correction

### Use Cases

✅ **Complex Analysis**: Multi-step problem decomposition
✅ **Planning & Design**: Architecture decisions with revision capability
✅ **Course Correction**: Adapt reasoning when initial assumptions fail
✅ **Uncertain Scope**: Problems where full scope isn't clear initially
✅ **Long-Form Reasoning**: Maintain context over extended analysis

### When to Use

- When problems have unclear scope at the start
- When you need room to revise your approach mid-analysis
- When breaking down complex problems into steps
- When maintaining context across multiple reasoning stages
- When filtering relevant from irrelevant information

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0+
- **npm**: v8.0.0+
- **Claude Desktop**: Latest version

### Method 1: NPX (Recommended)

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
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    }
  }
}
```

### Method 2: Local Installation

```bash
# Install package
npm install -g @modelcontextprotocol/server-sequential-thinking

# Configure
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "node",
      "args": [
        "/path/to/global/node_modules/@modelcontextprotocol/server-sequential-thinking/dist/index.js"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch
3. Check MCP icon (bottom-right)
4. Verify "sequential-thinking" listed

### Step 4: Test Installation

```
Break down this problem step-by-step: How should we migrate 10M user records to a new database schema?
```

Claude will use `sequential_thinking` tool to create numbered steps with revision capability.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `MAX_STEPS` | `50` | Maximum steps per session |
| `ENABLE_REVISION` | `true` | Allow step revision |
| `LOG_LEVEL` | `info` | Logging verbosity |

### Example Configuration

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"],
      "env": {
        "MAX_STEPS": "100",
        "LOG_LEVEL": "debug"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "sequential_thinking tool not available"

**Symptoms**: Tool doesn't appear in Claude

**Solutions**:

1. **Check NPX cache**:
   ```bash
   npx clear-npx-cache
   npx -y @modelcontextprotocol/server-sequential-thinking
   ```

2. **Verify internet connection** (NPX downloads on first run)

3. **Use local installation** (Method 2 above)

### Issue 2: Steps not revising

**Symptoms**: Can't go back and revise previous steps

**Causes**: Revision disabled or session expired

**Solutions**:

1. **Enable revision**:
   ```json
   {
     "env": {
       "ENABLE_REVISION": "true"
     }
   }
   ```

2. **Start new session** if too much time passed

### Issue 3: NPX slow startup

**Symptoms**: 5-10 second delay on first use

**Cause**: NPX downloads package on first run

**Solutions**:

1. **Pre-cache package**:
   ```bash
   npx -y @modelcontextprotocol/server-sequential-thinking
   ```

2. **Use local installation** for faster startup

---

## 🔄 Alternative Methods

### Docker Installation

```bash
docker run -p 3000:3000 \
  mcp/sequential-thinking:latest
```

Then configure Claude to connect via HTTP (if supported).

### Manual Build from Source

```bash
git clone https://github.com/modelcontextprotocol/servers.git
cd servers/src/sequentialthinking
npm install
npm run build

# Use dist/index.js in config
```

---

## 📚 How It Works

### Sequential Thinking Process

1. **Initial Assessment**: Claude evaluates problem scope
2. **Step Breakdown**: Decompose into numbered steps
3. **Iterative Execution**: Execute step-by-step
4. **Dynamic Revision**: Revise steps as understanding evolves
5. **Context Maintenance**: Track progress across steps
6. **Irrelevant Filtering**: Focus on relevant information

### Example Flow

```
Step 1: Understand current database schema
Step 2: Identify migration risks
Step 3: [REVISED] Design incremental migration strategy
Step 4: Create rollback plan
Step 5: Execute pilot migration
```

---

## 🎯 Usage Examples

### Example 1: Problem Decomposition

**Prompt**:
```
Break down: How do we implement real-time collaboration in our app?
```

**Result**:
- Step 1: Analyze WebSocket requirements
- Step 2: Design conflict resolution
- Step 3: Implement operational transforms
- (Revises Step 2 after discovering CRDT alternative)

### Example 2: Planning with Revision

**Prompt**:
```
Plan our Q4 feature roadmap, but be ready to adjust based on dependencies
```

**Result**: Sequential plan with built-in revision points when dependencies discovered.

---

## 🔗 Related Resources

- **Official Repository**: [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)
- **NPM Package**: [@modelcontextprotocol/server-sequential-thinking](https://www.npmjs.com/package/@modelcontextprotocol/server-sequential-thinking)
- **MCP Protocol**: [modelcontextprotocol.io](https://modelcontextprotocol.io)

---

## 💡 Tips & Best Practices

1. **Use for uncertain scope** problems (not well-defined ones)
2. **Combine with clear-thought** for deeper analysis per step
3. **Enable revision** for exploratory problems
4. **Set realistic MAX_STEPS** (default 50 is usually enough)
5. **Start broad, then narrow** each step as context builds

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Internet connection (for NPX)
- [ ] JSON config syntax valid
- [ ] Claude Desktop restarted fully
- [ ] MCP icon shows "sequential-thinking"
- [ ] NPX cache cleared if issues

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/modelcontextprotocol/servers/issues)
- **Documentation**: [MCP Docs](https://modelcontextprotocol.io/docs)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Official Anthropic MCP
**Status**: ✅ Stable

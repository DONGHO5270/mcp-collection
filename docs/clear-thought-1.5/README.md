# clear-thought-1.5 MCP Server

> Advanced reasoning with 30+ operations: Systems Thinking, Decision Frameworks, and Metacognitive Analysis

[![GitHub](https://img.shields.io/badge/GitHub-glassBead--tc%2Fclear--thought--onepointfive-blue)](https://github.com/glassBead-tc/clear-thought-onepointfive)
[![Smithery](https://img.shields.io/badge/Smithery-Install-green)](https://smithery.ai/server/@waldzellai/clear-thought)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is clear-thought-1.5?

**clear-thought-1.5** is an enhanced MCP server providing 30+ advanced reasoning operations through a single `clear_thought` tool. Built on Anthropic's Model Context Protocol, it enables Claude to perform sophisticated analysis including systems thinking, decision frameworks, and multi-perspective reasoning.

### Key Features

**Core Operations**:
- **systems_thinking**: Model problems as interconnected systems
- **decision_framework**: Structured option analysis and ranking
- **collaborative_reasoning**: Multi-persona perspective analysis
- **Ulysses Protocol**: High-stakes decision safeguards
- **OODA Loop**: Observe-Orient-Decide-Act rapid response
- **causal_analysis**: Root cause identification
- **sequential_thinking**: Advanced chain-of-thought with patterns (tree, beam, mcts, graph)

**Advanced Capabilities**:
- 30+ reasoning operations in one tool
- Configurable thinking patterns (auto, tree, beam, mcts, graph)
- Metacognitive monitoring and bias detection
- Structured argumentation (thesis, antithesis, synthesis)
- Visual reasoning with diagram support

### Use Cases

✅ **Strategic Planning**: OODA Loop for rapid business decisions
✅ **System Architecture**: Systems thinking for component analysis
✅ **Risk Management**: Ulysses Protocol for high-stakes scenarios
✅ **Multi-perspective Analysis**: Collaborative reasoning with simulated personas
✅ **Decision Making**: Weighted criteria frameworks with scoring

### When to Use

- When you need advanced reasoning beyond sequential thinking
- When problems require systems-level understanding
- When decisions involve multiple stakeholders or perspectives
- When high-stakes decisions need safeguards (Ulysses Protocol)
- When rapid response is critical (OODA Loop)

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version
- **Git**: For cloning repositories

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/glassBead-tc/clear-thought-onepointfive.git
cd clear-thought-onepointfive
```

**Alternative**: Use waldzellai fork (OG Sequential Thinking):
```bash
git clone https://github.com/waldzellai/clearthought-onepointfive.git
cd clearthought-onepointfive
```

### Step 2: Install Dependencies

```bash
npm install
```

**Expected output**:
```
added 52 packages in 4s
```

### Step 3: Build Project

```bash
npm run build
```

**Expected output**:
```
> clear-thought-1.5@1.5.0 build
> tsc
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
    "clear-thought-1.5": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/clear-thought-onepointfive/dist/index.js"
      ],
      "env": {
        "MEMORY_DIR": "C:/Users/YourUsername/Documents/mcp-servers/clear-thought-onepointfive/.memory",
        "DEFAULT_PATTERN": "auto"
      }
    }
  }
}
```

**Important**:
- Replace path with your actual directory
- Use forward slashes `/` on all platforms
- `DEFAULT_PATTERN`: auto, tree, beam, mcts, or graph

### Step 5: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "clear-thought-1.5" is listed

### Step 6: Verify Installation

In Claude Desktop:

```
Use systems thinking to analyze: How should we architect a microservices system?
```

If working correctly, Claude will use the `clear_thought` tool with `systems_thinking` operation.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `MEMORY_DIR` | `./.memory` | Storage for reasoning sessions |
| `DEFAULT_PATTERN` | `auto` | Thinking pattern (auto/tree/beam/mcts/graph) |
| `MAX_OPERATIONS` | `100` | Maximum operations per session |
| `LOG_LEVEL` | `info` | Logging verbosity |

### Advanced Configuration

**Enable MCTS Pattern** (Monte Carlo Tree Search):
```json
{
  "env": {
    "DEFAULT_PATTERN": "mcts"
  }
}
```

**Enable Debug Logging**:
```json
{
  "env": {
    "LOG_LEVEL": "debug"
  }
}
```

**Custom Memory Location**:
```json
{
  "env": {
    "MEMORY_DIR": "~/Documents/clear-thought-memory"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "clear_thought tool not found"

**Symptoms**: Claude doesn't recognize `clear_thought` tool

**Solutions**:

1. **Verify build completed**:
   ```bash
   ls -la ~/Documents/mcp-servers/clear-thought-onepointfive/dist/
   # Should show index.js
   ```

2. **Check configuration path**:
   ```bash
   cat ~/Library/Application\ Support/Claude/claude_desktop_config.json
   # Verify path matches your installation
   ```

3. **Restart Claude Desktop** (full quit, not just close)

### Issue 2: "operation not supported"

**Symptoms**: Error like "systems_thinking is not a valid operation"

**Causes**:
- Using old version of clear-thought (not 1.5)
- Build failed silently

**Solutions**:

1. **Verify version**:
   ```bash
   grep "version" ~/Documents/mcp-servers/clear-thought-onepointfive/package.json
   # Should show 1.5.x
   ```

2. **Rebuild**:
   ```bash
   cd ~/Documents/mcp-servers/clear-thought-onepointfive
   npm run build
   ```

### Issue 3: Memory persistence issues

**Symptoms**: Previous reasoning sessions not remembered

**Solutions**:

1. **Check memory directory exists**:
   ```bash
   mkdir -p ~/Documents/mcp-servers/clear-thought-onepointfive/.memory
   chmod 755 ~/Documents/mcp-servers/clear-thought-onepointfive/.memory
   ```

2. **Verify environment variable**:
   ```json
   {
     "env": {
       "MEMORY_DIR": "/full/absolute/path/.memory"
     }
   }
   ```

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

Easiest method using Smithery:

```bash
npx -y @smithery/cli install @waldzellai/clear-thought-onepointfive --client claude
```

**Pros**: Automated setup, no manual configuration
**Cons**: Requires npm registry access

### Method 2: NPM Package

Install from npm registry:

```bash
npm install -g @waldzellai/clear-thought
```

Then configure:
```json
{
  "mcpServers": {
    "clear-thought-1.5": {
      "command": "clear-thought"
    }
  }
}
```

**Note**: Global installation may require elevated permissions.

---

## 📚 Available Operations

### 1. `systems_thinking`
Model problems as interconnected systems with components, relationships, and feedback loops.

**Use when**: Analyzing complex systems, architecture decisions, organizational design

### 2. `decision_framework`
Structured evaluation of options against weighted criteria.

**Use when**: Comparing alternatives, technology choices, strategic decisions

### 3. `collaborative_reasoning`
Multi-persona analysis with simulated expert perspectives.

**Use when**: Need diverse viewpoints, stakeholder analysis, conflict resolution

### 4. `Ulysses Protocol`
High-stakes decision safeguards with pre-commitment and exit criteria.

**Use when**: Irreversible decisions, large investments, critical launches

### 5. `OODA Loop`
Observe-Orient-Decide-Act rapid response framework.

**Use when**: Fast-changing environments, competitive analysis, crisis response

### 6. `causal_analysis`
Root cause identification using 5 Whys and Ishikawa diagrams.

**Use when**: Debugging, incident analysis, quality issues

### 7. `sequential_thinking`
Advanced chain-of-thought with patterns (tree, beam, mcts, graph).

**Use when**: Complex problem-solving, multi-step reasoning

---

## 🎯 Usage Examples

### Example 1: Systems Thinking

**Prompt**:
```
Use systems thinking to analyze our microservices architecture
```

**Result**: Claude uses `clear_thought` with `systems_thinking` to map components, relationships, feedback loops, and identify leverage points.

### Example 2: Decision Framework

**Prompt**:
```
Use decision framework to compare React vs Vue vs Svelte for our new project
Criteria: learning curve, performance, ecosystem, team expertise
```

**Result**: Weighted scoring matrix with recommendations.

### Example 3: Ulysses Protocol

**Prompt**:
```
Apply Ulysses Protocol to our database migration decision
High stakes: 10M user records, zero downtime requirement
```

**Result**: Pre-commitment plan, exit criteria, rollback procedures.

---

## 🔗 Related Resources

- **Official Repository**: [glassBead-tc/clear-thought-onepointfive](https://github.com/glassBead-tc/clear-thought-onepointfive)
- **OG Fork**: [waldzellai/clearthought-onepointfive](https://github.com/waldzellai/clearthought-onepointfive)
- **Smithery**: [Install Guide](https://smithery.ai/server/@waldzellai/clear-thought)
- **MCP Protocol**: [modelcontextprotocol.io](https://modelcontextprotocol.io)

---

## 💡 Tips & Best Practices

1. **Start with `systems_thinking`** for complex problems
2. **Use `decision_framework`** for comparing 2-5 options
3. **Apply `Ulysses Protocol`** for irreversible decisions
4. **Combine operations**: Sequential → Systems → Decision
5. **Set `DEFAULT_PATTERN: auto`** for intelligent pattern selection
6. **Use memory persistence** to build on previous analyses

---

## 🐛 Troubleshooting Checklist

Before reporting issues:

- [ ] Node.js ≥ 18.0.0
- [ ] `npm install` completed
- [ ] `npm run build` successful
- [ ] Absolute path in config
- [ ] JSON syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "clear-thought-1.5"
- [ ] Logs checked: `~/Library/Logs/Claude/mcp*.log`

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/glassBead-tc/clear-thought-onepointfive/issues)
- **Discussions**: [GitHub Discussions](https://github.com/glassBead-tc/clear-thought-onepointfive/discussions)
- **Premium Support**: Available with [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: 1.5.0
**Status**: ✅ Stable

# model-enhancement-servers

> Cognitive enhancement with 13+ specialized reasoning modules for advanced AI capabilities

[![GitHub](https://img.shields.io/badge/GitHub-waldzellai%2Fmodel--enhancement--servers-blue)](https://github.com/waldzellai/model-enhancement-servers)
[![Smithery](https://img.shields.io/badge/Smithery-Install-green)](https://smithery.ai/protocol/waldzellai)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is model-enhancement-servers?

**model-enhancement-servers** is a monorepo collection of MCP servers that extend AI capabilities through specialized reasoning modules. Each server provides advanced cognitive tools including structured argumentation, visual reasoning, scientific method, analogical thinking, metacognitive monitoring, and more, enabling Claude to perform sophisticated analysis beyond standard capabilities.

### Key Modules (13+)

- **Structured Argumentation**: Formal dialectical reasoning (thesis, antithesis, synthesis)
- **Visual Reasoning**: Diagrammatic thinking and spatial representation
- **Scientific Method**: Hypothesis testing and evidence evaluation
- **Analogical Reasoning**: Structured metaphorical thinking and pattern mapping
- **Metacognitive Monitoring**: Knowledge assessment and confidence tracking
- **Decision Framework**: Structured decision analysis with weighted criteria
- **Collaborative Reasoning**: Multi-perspective problem solving with personas
- **Bias Detection**: Identify cognitive biases and logical fallacies
- **Constraint Solver**: Optimize solutions within constraints
- **Goal Tracker**: Track objectives and progress systematically
- **Multimodal Synthesizer**: Integrate text, visual, and data analysis
- **Narrative Planner**: Structure storytelling and narrative arcs
- **Ethical Reasoning**: Evaluate decisions against ethical frameworks

### Use Cases

✅ **Complex Analysis**: Multi-dimensional problem evaluation
✅ **Formal Debate**: Structured argumentation with thesis/antithesis/synthesis
✅ **Scientific Research**: Hypothesis-driven investigation
✅ **Strategic Planning**: Decision frameworks with trade-off analysis
✅ **Bias Detection**: Identify and mitigate cognitive biases

### When to Use

- When need formal reasoning structures
- When analyzing complex decisions
- When conducting hypothesis-driven research
- When identifying cognitive biases
- When optimizing under constraints

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/waldzellai/model-enhancement-servers.git
cd model-enhancement-servers
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Build All Servers

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

Add configuration (example for structured argumentation):

```json
{
  "mcpServers": {
    "structured-argumentation": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/model-enhancement-servers/src/structured-argumentation/dist/index.js"
      ]
    }
  }
}
```

**Note**: Each module is a separate server. Install only needed modules or install all.

### Step 5: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify modules are listed

### Step 6: Test Installation

In Claude Desktop:

```
Use structured argumentation to analyze: Should we adopt microservices architecture?
```

Claude will use `submit_argument` tool to create thesis, antithesis, and synthesis.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `LOG_LEVEL` | `info` | Logging verbosity |
| `MAX_RECURSION` | `10` | Maximum reasoning depth |

### Example Configuration

```json
{
  "mcpServers": {
    "structured-argumentation": {
      "command": "node",
      "args": ["path/to/dist/index.js"],
      "env": {
        "LOG_LEVEL": "debug",
        "MAX_RECURSION": "15"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Module not found"

**Symptoms**: Error loading specific reasoning module

**Solutions**:

1. **Verify build**: Run `npm run build` in repository root

2. **Check path**: Ensure path points to dist/index.js for specific module

### Issue 2: Reasoning loops

**Symptoms**: Tool execution takes too long or loops

**Solutions**:

1. **Reduce MAX_RECURSION**:
   ```json
   {
     "env": {
       "MAX_RECURSION": "5"
     }
   }
   ```

2. **Simplify prompts**: Use more specific reasoning requests

### Issue 3: Multiple modules conflict

**Symptoms**: Unexpected behavior when using multiple modules

**Solutions**:

1. **Use one module at a time**: Don't mix conflicting reasoning types

2. **Clear session**: Start new conversation for different reasoning type

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation (Individual Modules)

```bash
npx -y @smithery/cli install @waldzellai/structured-argumentation --client claude
```

**Available via Smithery**:
- @waldzellai/structured-argumentation
- @waldzellai/visual-reasoning
- @waldzellai/scientific-method
- @waldzellai/analogical-reasoning
- (and 9 more modules)

---

## 📚 Available Modules

| Module | Description | Use Case |
|--------|-------------|----------|
| **Structured Argumentation** | Thesis/Antithesis/Synthesis | Formal debate, decision analysis |
| **Visual Reasoning** | Diagrams, spatial thinking | System design, architecture |
| **Scientific Method** | Hypothesis testing | Research, experimentation |
| **Analogical Reasoning** | Pattern mapping | Creative problem-solving |
| **Metacognitive Monitoring** | Self-assessment | Quality control, confidence |
| **Decision Framework** | Weighted criteria | Strategic decisions |
| **Collaborative Reasoning** | Multi-persona analysis | Stakeholder perspectives |
| **Bias Detection** | Identify fallacies | Critical thinking |
| **Constraint Solver** | Optimization | Resource allocation |
| **Goal Tracker** | Objective management | Project planning |
| **Multimodal Synthesizer** | Cross-modal integration | Data analysis |
| **Narrative Planner** | Story structure | Communication design |
| **Ethical Reasoning** | Ethical frameworks | Moral decisions |

---

## 🎯 Usage Example

**Prompt**:
```
Use structured argumentation to analyze whether we should adopt microservices architecture

Thesis: Microservices improve scalability
Antithesis: Microservices increase complexity
Synthesis: Use microservices for high-traffic services, monolith for internal tools
```

**Result**: Formal argument structure with premises, evidence, and synthesis

---

## 🔗 Related Resources

- **Official Repository**: [waldzellai/model-enhancement-servers](https://github.com/waldzellai/model-enhancement-servers)
- **Smithery**: [waldzellai Protocol](https://smithery.ai/protocol/waldzellai)
- **Medium Article**: [MCP 101: Episode 1](https://glassbead-tc.medium.com/mcp-101-episode-1-model-enhancement-servers-afbd459d49e3)

---

## 💡 Tips & Best Practices

1. **Install only needed modules** to reduce overhead
2. **Use specific module** for task (don't mix reasoning types)
3. **Start with low MAX_RECURSION** (5-10) for faster responses

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] `npm install` completed
- [ ] `npm run build` successful
- [ ] Absolute path to specific module in config
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows module name

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/waldzellai/model-enhancement-servers/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest
**Status**: ✅ Stable

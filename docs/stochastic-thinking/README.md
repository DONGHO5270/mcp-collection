# stochastic-thinking MCP Server

> Probabilistic decision-making with Monte Carlo, Bayesian, and MCTS algorithms

[![GitHub](https://img.shields.io/badge/GitHub-chirag127%2FStochastic--Thinking--MCP--Server-blue)](https://github.com/chirag127/Stochastic-Thinking-MCP-Server)
[![Smithery](https://img.shields.io/badge/Smithery-Install-green)](https://smithery.ai/server/@chirag127/stochastic-thinking-mcp-server)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is stochastic-thinking?

**stochastic-thinking** is an MCP server that provides advanced stochastic algorithms and probabilistic decision-making capabilities to Claude. It extends sequential thinking with mathematical models for handling uncertainty, exploring decision spaces, and optimizing under probabilistic constraints.

### Key Algorithms

- **Monte Carlo Tree Search (MCTS)**: Explore decision trees with simulations
- **Bayesian Optimization**: Optimize unknown functions under uncertainty
- **Markov Decision Processes (MDPs)**: Sequential decision-making
- **Multi-Armed Bandit**: Exploration vs exploitation trade-offs
- **Hidden Markov Models (HMMs)**: Probabilistic state inference

### Use Cases

✅ **Risk Analysis**: Monte Carlo simulations for risk quantification
✅ **Decision Trees**: MCTS for exploring complex decision spaces
✅ **A/B Testing**: Multi-Armed Bandit for experiment optimization
✅ **Uncertainty Modeling**: Bayesian methods for parameter estimation
✅ **Sequential Decisions**: MDPs for multi-step planning under uncertainty

### When to Use

- When decisions involve significant uncertainty
- When exploring large decision spaces
- When optimizing with limited information
- When balancing exploration vs exploitation
- When quantifying risks with probability distributions

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0+
- **npm**: v8.0.0+
- **Claude Desktop**: Latest version

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/chirag127/Stochastic-Thinking-MCP-Server.git
cd Stochastic-Thinking-MCP-Server
```

### Step 2: Install Dependencies

```bash
npm install
```

**Expected output**:
```
added 45 packages in 3s
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
    "stochastic-thinking": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/Stochastic-Thinking-MCP-Server/dist/index.js"
      ],
      "env": {
        "DEFAULT_ITERATIONS": "10000",
        "SIMULATION_SEED": "42"
      }
    }
  }
}
```

### Step 5: Restart and Verify

1. Restart Claude Desktop fully
2. Check MCP icon for "stochastic-thinking"
3. Test:

```
Run Monte Carlo simulation: What's the probability of success if we have 3 independent features, each with 80% completion chance?
```

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `DEFAULT_ITERATIONS` | `10000` | Monte Carlo simulation iterations |
| `SIMULATION_SEED` | `random` | Random seed for reproducibility |
| `CONFIDENCE_LEVEL` | `0.95` | Confidence interval (95%) |
| `EXPLORATION_CONSTANT` | `1.414` | UCT constant for MCTS |

### Example Configurations

**High Precision Simulations**:
```json
{
  "env": {
    "DEFAULT_ITERATIONS": "100000",
    "SIMULATION_SEED": "42"
  }
}
```

**Fast Exploration (MCTS)**:
```json
{
  "env": {
    "EXPLORATION_CONSTANT": "2.0"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: Simulations too slow

**Symptoms**: Monte Carlo taking >30 seconds

**Solutions**:

1. **Reduce iterations**:
   ```json
   {
     "env": {
       "DEFAULT_ITERATIONS": "1000"
     }
   }
   ```

2. **Use faster algorithm**: Switch from MCTS to simpler Monte Carlo

### Issue 2: Non-deterministic results

**Symptoms**: Different results each run

**Cause**: Random seed not set

**Solution**:

```json
{
  "env": {
    "SIMULATION_SEED": "42"
  }
}
```

### Issue 3: Tool timeouts

**Symptoms**: Error "stochasticalgorithm timed out"

**Causes**: Iterations too high or complex model

**Solutions**:

1. **Lower iterations**: Start with 1000, increase gradually
2. **Simplify model**: Reduce state space for MDPs

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @chirag127/stochastic-thinking-mcp-server --client claude
```

**Pros**: Automated setup
**Cons**: Requires Smithery CLI

### Method 2: Docker

```bash
docker run -p 3000:3000 stochastic-thinking:latest
```

---

## 📚 Available Algorithms

### 1. Monte Carlo Simulation
Run thousands of random trials to estimate probabilities.

**Use when**: Quantifying risk, estimating project completion, revenue forecasting

**Example**: "What's our revenue range with 95% confidence given these assumptions?"

### 2. Monte Carlo Tree Search (MCTS)
Explore decision trees by simulating random playouts.

**Use when**: Game AI, planning with large action spaces, strategic decisions

**Example**: "Find optimal product launch strategy exploring different market entry sequences"

### 3. Bayesian Optimization
Optimize unknown functions with Gaussian processes.

**Use when**: Hyperparameter tuning, A/B test optimization, resource allocation

**Example**: "Find optimal ad spend allocation across channels"

### 4. Multi-Armed Bandit
Balance exploration (trying new options) vs exploitation (using best known).

**Use when**: A/B testing, dynamic pricing, content recommendations

**Example**: "Optimize which features to show to maximize engagement"

### 5. Markov Decision Process (MDP)
Sequential decision-making with states, actions, rewards.

**Use when**: Multi-step planning, reinforcement learning scenarios, workflow optimization

**Example**: "Optimize customer support workflow transitions"

### 6. Hidden Markov Model (HMM)
Infer hidden states from observable sequences.

**Use when**: Time series analysis, anomaly detection, user behavior modeling

**Example**: "Detect user churn signals from activity patterns"

---

## 🎯 Usage Examples

### Example 1: Risk Analysis

**Prompt**:
```
Monte Carlo simulation: We have 3 critical path tasks, each 70% likely to complete on time. What's the probability the entire project finishes on schedule?
```

**Result**:
- Probability: 34.3%
- 95% CI: [32.1%, 36.5%]
- Risk level: HIGH

### Example 2: A/B Test Optimization

**Prompt**:
```
Multi-Armed Bandit: We're testing 4 homepage variants. Current CTRs: A=2.1%, B=2.3%, C=1.9%, D=2.5%. Which should we show next 1000 visitors?
```

**Result**: Thompson Sampling recommends D (60%), B (25%), A (10%), C (5%)

### Example 3: Decision Tree Exploration

**Prompt**:
```
MCTS: Explore market entry strategies for our SaaS product. Options: Direct sales, Partner channel, Freemium, Enterprise-first. Budget: $500K.
```

**Result**: MCTS tree with win rates for each path after 10K simulations.

---

## 🔗 Related Resources

- **GitHub**: [chirag127/Stochastic-Thinking-MCP-Server](https://github.com/chirag127/Stochastic-Thinking-MCP-Server)
- **Smithery**: [Install Guide](https://smithery.ai/server/@chirag127/stochastic-thinking-mcp-server)
- **MCTS Theory**: [Research Papers](https://www.researchgate.net/publication/221707773_Bayesian_Inference_in_Monte-Carlo_Tree_Search)

---

## 💡 Tips & Best Practices

1. **Start with 1K iterations** for fast feedback, increase to 10K for production
2. **Set SIMULATION_SEED** for reproducible results in testing
3. **Use Monte Carlo** for risk analysis (simple, fast)
4. **Use MCTS** for decision trees (complex, slower)
5. **Use Bayesian Optimization** for hyperparameter tuning
6. **Combine with clear-thought** for interpretation of results

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] `npm install` completed
- [ ] `npm run build` successful
- [ ] Absolute path in config
- [ ] Claude Desktop restarted
- [ ] DEFAULT_ITERATIONS not too high (≤10K for testing)
- [ ] Logs: `~/Library/Logs/Claude/mcp*.log`

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/chirag127/Stochastic-Thinking-MCP-Server/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: 1.0.0
**Status**: ✅ Stable

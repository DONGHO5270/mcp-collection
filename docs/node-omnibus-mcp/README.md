# node-omnibus-mcp Server

> Comprehensive Node.js development tooling: project scaffolding, TypeScript, and React automation

[![GitHub](https://img.shields.io/badge/GitHub-bsmi021%2Fmcp--node--omnibus--server-blue)](https://github.com/bsmi021/mcp-node-omnibus-server)
[![Smithery](https://img.shields.io/badge/Smithery-Install-green)](https://smithery.ai/server/@bsmi021/mcp-node-omnibus-server)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is node-omnibus-mcp?

**node-omnibus-mcp** is a comprehensive MCP server that provides advanced Node.js development tooling and automation capabilities. It enables AI-assisted project scaffolding, component generation, TypeScript configuration, and dependency management for React, Next.js, Express, Fastify, and plain Node.js projects.

### Key Features

- **Project Scaffolding**: Create React, Next.js, Express, Fastify, Node.js projects
- **TypeScript Support**: Automatic TypeScript configuration and setup
- **Component Generation**: Create React components (functional/class) with props
- **Dependency Management**: Smart package installation and version management
- **Script Management**: Add npm scripts to package.json
- **TypeScript Configuration**: Update tsconfig.json with compiler options
- **Documentation Generation**: Create README, API docs, component docs

### Use Cases

✅ **Quick Project Setup**: Scaffold new projects with best practices
✅ **Component Boilerplate**: Generate React components with TypeScript
✅ **Dependency Management**: Install packages with type definitions
✅ **Configuration Automation**: Update TypeScript, ESLint, Prettier configs
✅ **Documentation**: Auto-generate documentation files

### When to Use

- When starting new Node.js/TypeScript projects
- When need React component boilerplate
- When managing project dependencies
- When automating TypeScript configuration
- When generating project documentation

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version

### Step 1: Clone Repository

```bash
cd ~/Documents/mcp-servers
git clone https://github.com/bsmi021/mcp-node-omnibus-server.git
cd mcp-node-omnibus-server
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
    "node-omnibus": {
      "command": "node",
      "args": [
        "C:/Users/YourUsername/Documents/mcp-servers/mcp-node-omnibus-server/dist/index.js"
      ]
    }
  }
}
```

### Step 5: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "node-omnibus" is listed

### Step 6: Test Installation

In Claude Desktop:

```
Create a new React project with TypeScript named "my-app"
```

Claude will use `create_project` tool to scaffold the project.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `DEFAULT_PACKAGE_MANAGER` | `npm` | Package manager (npm, yarn, pnpm) |
| `TYPESCRIPT_VERSION` | `latest` | TypeScript version to install |
| `LOG_LEVEL` | `info` | Logging verbosity |

### Example Configuration

```json
{
  "mcpServers": {
    "node-omnibus": {
      "command": "node",
      "args": ["path/to/dist/index.js"],
      "env": {
        "DEFAULT_PACKAGE_MANAGER": "pnpm",
        "LOG_LEVEL": "debug"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Command not found: node"

**Symptoms**: Error launching server

**Solutions**:

1. **Verify Node.js path**: Use full path to node executable

2. **Check installation**:
   ```bash
   which node  # macOS/Linux
   where node  # Windows
   ```

### Issue 2: Project creation fails

**Symptoms**: Error creating new project

**Solutions**:

1. **Check directory permissions**: Ensure write access

2. **Verify path exists**: Parent directory must exist

3. **Check Node.js version**: Must be ≥ 18.0.0

### Issue 3: TypeScript errors

**Symptoms**: Type definition errors after component generation

**Solutions**:

1. **Install types**: Run `npm install --save-dev @types/react`

2. **Update tsconfig**: Verify `compilerOptions` are correct

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @bsmi021/mcp-node-omnibus-server --client claude
```

**Pros**: Automated setup
**Cons**: Requires Smithery CLI

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `create_project` | Scaffold new project (React, Next.js, Express, Fastify, Node.js) |
| `install_packages` | Install npm packages with version management |
| `generate_component` | Create React component (functional/class) |
| `create_type_definition` | Create TypeScript type/interface |
| `add_script` | Add npm script to package.json |
| `update_tsconfig` | Update TypeScript compiler options |
| `create_documentation` | Generate README/API/component docs |

---

## 🎯 Usage Examples

### Example 1: Create Next.js Project

**Prompt**:
```
Create a new Next.js project with TypeScript at C:/Projects/my-next-app
```

**Result**: Scaffolds Next.js project with TypeScript, installs dependencies, generates tsconfig.json

### Example 2: Generate React Component

**Prompt**:
```
Generate a functional React component named "Button" with props: text (string), onClick (function)
```

**Result**: Creates Button.tsx with TypeScript props interface

### Example 3: Install Packages

**Prompt**:
```
Install axios and lodash as dependencies in my project at C:/Projects/my-app
```

**Result**: Installs packages, updates package.json, installs type definitions

---

## 🔗 Related Resources

- **Official Repository**: [bsmi021/mcp-node-omnibus-server](https://github.com/bsmi021/mcp-node-omnibus-server)
- **Smithery**: [Install Guide](https://smithery.ai/server/@bsmi021/mcp-node-omnibus-server)
- **TypeScript**: [typescriptlang.org](https://www.typescriptlang.org)

---

## 💡 Tips & Best Practices

1. **Use TypeScript**: Enable TypeScript for better type safety
2. **Generate components**: Save time with automated component boilerplate
3. **Check paths**: Always use absolute paths for project creation

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] `npm install` completed
- [ ] `npm run build` successful
- [ ] Absolute path in config
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "node-omnibus"

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/bsmi021/mcp-node-omnibus-server/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest
**Status**: ✅ Stable

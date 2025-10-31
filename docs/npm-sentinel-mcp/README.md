# npm-sentinel-mcp Server

> AI-powered NPM package security, vulnerability scanning, and dependency analysis

[![GitHub](https://img.shields.io/badge/GitHub-Nekzus%2Fnpm--sentinel--mcp-blue)](https://github.com/Nekzus/npm-sentinel-mcp)
[![NPM](https://img.shields.io/badge/NPM-%40nekzus%2Fmcp--server-red)](https://www.npmjs.com/package/@nekzus/mcp-server)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is npm-sentinel-mcp?

**npm-sentinel-mcp** is a powerful MCP server that revolutionizes NPM package analysis through AI. It provides real-time intelligence on package security, dependencies, and performance to safeguard and optimize your npm ecosystem, making package management decisions faster and safer for modern development workflows.

### Key Features

- **Security Vulnerability Scanning**: Identify known CVEs and security issues
- **Dependency Analysis**: Map dependency trees and identify conflicts
- **Package Comparison**: Compare multiple packages side-by-side
- **Quality Assessment**: Evaluate package quality, maintenance, popularity
- **Version Analysis**: Check for updates and breaking changes
- **TypeScript Support**: Verify TypeScript type definitions
- **License Compliance**: Check license compatibility
- **Size Analysis**: Analyze bundle size impact
- **Download Trends**: Track package popularity over time
- **Maintainer Insights**: Review maintainer activity and reputation

### Use Cases

✅ **Security Audits**: Scan projects for vulnerable dependencies
✅ **Package Selection**: Compare alternatives before adoption
✅ **Dependency Management**: Identify outdated or risky packages
✅ **Compliance Checking**: Verify license compatibility
✅ **Performance Optimization**: Analyze and reduce bundle sizes

### When to Use

- Before adding new package dependencies
- When conducting security audits
- When comparing package alternatives
- When troubleshooting dependency conflicts
- When optimizing application bundle size

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
    "npm-sentinel": {
      "command": "npx",
      "args": [
        "-y",
        "@nekzus/mcp-server"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "npm-sentinel" is listed

### Step 4: Test Installation

In Claude Desktop:

```
Check vulnerabilities for the package "express"
```

Claude will use `npmVulnerabilities` tool to scan for security issues.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `NPM_REGISTRY` | registry.npmjs.org | NPM registry URL |
| `CACHE_TTL` | `3600` | Cache duration (seconds) |
| `LOG_LEVEL` | `info` | Logging verbosity |

### Example Configuration

```json
{
  "mcpServers": {
    "npm-sentinel": {
      "command": "npx",
      "args": ["-y", "@nekzus/mcp-server"],
      "env": {
        "CACHE_TTL": "7200",
        "LOG_LEVEL": "debug"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Rate limit exceeded"

**Symptoms**: Error when querying multiple packages

**Solutions**:

1. **Reduce query frequency**: Batch requests together

2. **Increase cache TTL**:
   ```json
   {
     "env": {
       "CACHE_TTL": "7200"
     }
   }
   ```

### Issue 2: Vulnerability data outdated

**Symptoms**: Known vulnerabilities not showing

**Cause**: Cache outdated or registry delay

**Solutions**:

1. **Clear cache**: Set `CACHE_TTL` to `0` temporarily

2. **Check NPM registry**: Verify vulnerability is published

### Issue 3: Package not found

**Symptoms**: Error "Package not found on registry"

**Solutions**:

1. **Verify package name**: Check spelling and case

2. **Check registry access**: Ensure internet connection

3. **Try alternative registry**: Configure custom NPM_REGISTRY

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @Nekzus/npm-sentinel-mcp --client claude
```

### Method 2: Docker

```bash
docker run -p 3000:3000 nekzus/npm-sentinel-mcp:latest
```

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `npmVulnerabilities` | Check vulnerabilities |
| `npmDeps` | Analyze dependencies |
| `npmVersions` | Get all versions |
| `npmLatest` | Get latest version & changelog |
| `npmTypes` | Check TypeScript types availability |
| `npmSize` | Get package size info |
| `npmTrends` | Get download trends |
| `npmCompare` | Compare multiple packages |
| `npmMaintainers` | Get maintainers info |
| `npmScore` | Get quality score |
| `npmSearch` | Search packages |
| `npmLicenseCompatibility` | Check license compatibility |
| `npmQuality` | Analyze quality metrics |
| `npmMaintenance` | Analyze maintenance metrics |

---

## 🎯 Usage Examples

### Example 1: Vulnerability Scan

**Prompt**:
```
Check vulnerabilities for express, axios, and lodash
```

**Result**: Lists known CVEs with severity levels (critical, high, medium, low)

### Example 2: Package Comparison

**Prompt**:
```
Compare axios vs fetch vs node-fetch for making HTTP requests
```

**Result**: Side-by-side comparison of size, performance, maintenance, popularity

### Example 3: Dependency Analysis

**Prompt**:
```
Analyze dependencies for next@14.0.0
```

**Result**: Dependency tree with versions, circular dependencies, outdated packages

---

## 🔗 Related Resources

- **Official Repository**: [Nekzus/npm-sentinel-mcp](https://github.com/Nekzus/npm-sentinel-mcp)
- **NPM Package**: [@nekzus/mcp-server](https://www.npmjs.com/package/@nekzus/mcp-server)
- **NPM Registry**: [npmjs.com](https://www.npmjs.com)
- **Security Advisories**: [github.com/advisories](https://github.com/advisories)

---

## 💡 Tips & Best Practices

1. **Scan before installation**: Always check vulnerabilities first
2. **Compare alternatives**: Use `npmCompare` for package selection
3. **Monitor trends**: Check `npmTrends` for package health

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Internet connection active
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "npm-sentinel"
- [ ] NPM registry accessible

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/Nekzus/npm-sentinel-mcp/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (@nekzus/mcp-server)
**Status**: ✅ Stable

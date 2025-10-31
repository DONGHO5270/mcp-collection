# github-mcp Server

> Official GitHub integration: repository management, file operations, and API access

[![GitHub](https://img.shields.io/badge/GitHub-github%2Fgithub--mcp--server-blue)](https://github.com/github/github-mcp-server)
[![NPM](https://img.shields.io/badge/NPM-%40modelcontextprotocol%2Fserver--github-red)](https://www.npmjs.com/package/@modelcontextprotocol/server-github)
[![Status](https://img.shields.io/badge/Status-Official-green)]()

## 📌 What is github-mcp?

**github-mcp** is GitHub's official MCP server providing comprehensive GitHub integration for AI assistants. It enables repository management, file operations, issue/PR handling, and search capabilities through GitHub's API, all accessible via Personal Access Token authentication.

### Key Features

- **Repository Management**: Create, update, list repositories
- **File Operations**: Read, write, update files in repositories
- **Issue & PR Management**: Create, update, search issues and pull requests
- **Branch Operations**: Create, delete, list branches
- **Search Capabilities**: Search repositories, code, issues, users
- **GitHub API Integration**: Full access to GitHub REST API v3

### Use Cases

✅ **Automated PR Creation**: Generate pull requests from code changes
✅ **Issue Management**: Create and track issues programmatically
✅ **Code Search**: Find code patterns across repositories
✅ **Repository Setup**: Automate repository initialization
✅ **Branch Management**: Create feature branches and manage workflow

### When to Use

- When need programmatic access to GitHub repositories
- When automating issue and PR workflows
- When searching code across repositories
- When managing branches and releases
- When integrating GitHub data into AI workflows

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **npm**: v8.0.0 or higher
- **Claude Desktop**: Latest version
- **GitHub PAT**: Personal Access Token with appropriate scopes

### Step 1: Create GitHub Personal Access Token

1. Go to [GitHub Settings > Tokens](https://github.com/settings/tokens)
2. Click "Generate new token" (classic)
3. Select scopes:
   - `repo` (full control of private repositories)
   - `read:org` (read org data)
   - `workflow` (update GitHub Actions workflows)
4. Generate token and copy it

### Step 2: Open Configuration

**macOS/Linux**:
```bash
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**Windows**:
```bash
code %APPDATA%\Claude\claude_desktop_config.json
```

### Step 3: Add Configuration

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_your_token_here"
      }
    }
  }
}
```

**⚠️ Security**: Never commit this file to public repositories

### Step 4: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "github" is listed

### Step 5: Test Installation

In Claude Desktop:

```
List my GitHub repositories
```

Claude will use `search_repositories` tool to fetch your repositories.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GITHUB_PERSONAL_ACCESS_TOKEN` | Yes | GitHub PAT for authentication |
| `GITHUB_API_URL` | No | Custom API URL (for Enterprise) |

### Example Configuration

**With custom API URL** (for GitHub Enterprise):
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_your_token_here",
        "GITHUB_API_URL": "https://github.your-company.com/api/v3"
      }
    }
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Unauthorized: Bad credentials"

**Symptoms**: Error 401 when accessing repositories

**Solutions**:

1. **Verify token**:
   - Check token is correct in config
   - Ensure token hasn't expired (max 90 days)
   - Regenerate token if needed

2. **Check scopes**:
   - Token must have `repo` scope
   - Add `workflow` scope if modifying Actions

### Issue 2: "Resource not found"

**Symptoms**: Error 404 when accessing repository

**Cause**: Insufficient permissions or repository doesn't exist

**Solutions**:

1. **Check repository access**: Ensure you have access to the repository

2. **Verify repository name**: Use format `owner/repo`

3. **Check organization permissions**: Some orgs restrict API access

### Issue 3: Rate limit exceeded

**Symptoms**: Error 403 with "rate limit exceeded" message

**Cause**: GitHub API rate limits (5000 requests/hour for authenticated users)

**Solutions**:

1. **Wait for rate limit reset**: Check `X-RateLimit-Reset` header

2. **Optimize requests**: Reduce number of API calls

3. **Use GraphQL API**: More efficient for complex queries

---

## 🔄 Alternative Methods

### Method 1: Smithery Installation

```bash
npx -y @smithery/cli install @modelcontextprotocol/server-github --client claude
```

**Note**: You'll still need to add `GITHUB_PERSONAL_ACCESS_TOKEN` to config

### Method 2: Alternative Package

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@skhatri/github-mcp"],
      "env": {
        "GITHUB_TOKEN": "ghp_your_token_here"
      }
    }
  }
}
```

**Supports**: Personal Access Tokens and GitHub App Installation Tokens

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `create_repository` | Create new repository |
| `get_file_contents` | Read file from repository |
| `push_files` | Create/update files |
| `create_issue` | Create new issue |
| `create_pull_request` | Create new PR |
| `search_repositories` | Search repositories |
| `search_code` | Search code |
| `search_issues` | Search issues/PRs |
| `create_branch` | Create new branch |
| `list_commits` | List repository commits |

---

## 🎯 Usage Examples

### Example 1: Create Pull Request

**Prompt**:
```
Create a PR in my-org/my-repo from feature-branch to main with title "Add new feature" and description "This PR adds feature X"
```

**Result**: Creates PR with specified parameters, returns PR URL and number

### Example 2: Search Code

**Prompt**:
```
Search for "fetch API" usage in my JavaScript repositories
```

**Result**: Returns code snippets matching query across your JS repos

---

## 🔗 Related Resources

- **Official Repository**: [github/github-mcp-server](https://github.com/github/github-mcp-server)
- **NPM Package**: [@modelcontextprotocol/server-github](https://www.npmjs.com/package/@modelcontextprotocol/server-github)
- **GitHub API Docs**: [docs.github.com/rest](https://docs.github.com/rest)
- **Create PAT**: [github.com/settings/tokens](https://github.com/settings/tokens)

---

## 💡 Tips & Best Practices

1. **Use fine-grained PATs** for better security (scope to specific repositories)
2. **Rotate tokens regularly** (GitHub enforces 90-day max)
3. **Never commit tokens** to version control

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] GitHub PAT created with correct scopes
- [ ] Token not expired (check expiration date)
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "github"

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/github/github-mcp-server/issues)
- **Documentation**: [GitHub REST API Docs](https://docs.github.com/rest)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (@modelcontextprotocol/server-github)
**Status**: ✅ Official Release

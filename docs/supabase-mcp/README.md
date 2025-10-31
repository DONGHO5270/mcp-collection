# supabase-mcp Server

> Official Supabase integration: database management, migrations, branches, and TypeScript types

[![GitHub](https://img.shields.io/badge/GitHub-supabase--community%2Fsupabase--mcp-blue)](https://github.com/supabase-community/supabase-mcp)
[![NPM](https://img.shields.io/badge/NPM-%40supabase%2Fmcp--server-red)](https://www.npmjs.com/package/@supabase/mcp-server)
[![Status](https://img.shields.io/badge/Status-Official-green)]()

## 📌 What is supabase-mcp?

**supabase-mcp** is Supabase's official MCP server that bridges AI assistants with Supabase projects, enabling seamless database management, schema design, query execution, migrations, and TypeScript type generation—all through natural language interactions with Claude or other AI tools.

### Key Features

- **Database Operations**: Execute SQL queries (SELECT, INSERT, UPDATE, DELETE)
- **Schema Management**: Design tables, generate migrations, apply changes
- **TypeScript Integration**: Auto-generate types from database schema
- **Project Management**: Create projects, manage branches, configurations
- **Debug Tools**: Access logs, monitor performance, troubleshoot issues
- **Security Controls**: Read-only mode, project scoping, tool customization
- **Branch Development**: Test changes in safe development branches

### Use Cases

✅ **Schema Design**: AI-assisted database schema creation
✅ **Query Execution**: Run reports and data queries through AI
✅ **Migration Management**: Generate and apply database migrations
✅ **Type Safety**: Keep frontend types synced with database
✅ **Troubleshooting**: Pull logs and debug issues from editor

### When to Use

- When building Supabase-powered applications
- When need AI-assisted database management
- When automating schema migrations
- When maintaining TypeScript type definitions
- When debugging Supabase projects

---

## 🔧 Manual Installation

### Prerequisites

- **Node.js**: v18.0.0 or higher
- **Supabase Account**: Active project with API access
- **Personal Access Token**: From Supabase Dashboard
- **Claude Desktop**: Latest version

### Step 1: Create Supabase Access Token

1. Go to [Supabase Dashboard](https://supabase.com/dashboard/account/tokens)
2. Click "Generate new token"
3. Name: "MCP Server"
4. Copy the token (starts with `sbp_`)

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
    "supabase": {
      "command": "npx",
      "args": [
        "-y",
        "@supabase/mcp-server@latest"
      ],
      "env": {
        "SUPABASE_ACCESS_TOKEN": "sbp_your_token_here"
      }
    }
  }
}
```

**⚠️ Security**: Never commit this file with your token

### Step 4: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "supabase" is listed

### Step 5: Test Installation

In Claude Desktop:
```
List my Supabase projects
```

Claude will use `list_projects` tool to fetch your projects.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `SUPABASE_ACCESS_TOKEN` | Yes | Personal access token from dashboard |
| `SUPABASE_PROJECT_REF` | No | Scope to specific project |

### Project Scoping (Recommended)

Limit access to single project:
```json
{
  "env": {
    "SUPABASE_ACCESS_TOKEN": "sbp_your_token",
    "SUPABASE_PROJECT_REF": "your_project_ref"
  }
}
```

**Benefits**: Prevents LLM access to other projects, reduces attack surface

### Read-Only Mode

Enable read-only for safety:
```bash
npx @supabase/mcp-server@latest --read-only
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Unauthorized: Invalid token"

**Symptoms**: Error 401 when accessing Supabase

**Solutions**:

1. **Verify token**: Check token is correct and not expired

2. **Regenerate token**: Create new token from dashboard

3. **Check scopes**: Ensure token has necessary permissions

### Issue 2: "Project not found"

**Symptoms**: Error 404 when accessing project

**Solutions**:

1. **Verify project ref**: Check `SUPABASE_PROJECT_REF` is correct

2. **Check project status**: Ensure project is active (not paused)

---

## 🔄 Alternative Methods

### Method 1: With Tool Customization

Enable only specific tool groups:
```bash
npx @supabase/mcp-server@latest --features=database,docs
```

Available groups: `account`, `docs`, `database`, `debug`, `development`, `functions`, `storage`, `branching`

**Pros**: Reduced attack surface
**Cons**: Limited functionality

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `list_projects` | List all Supabase projects |
| `get_project` | Get project details |
| `create_project` | Create new project |
| `execute_sql` | Run SQL queries |
| `apply_migration` | Apply database migration |
| `list_migrations` | List all migrations |
| `generate_typescript_types` | Generate TypeScript types |
| `get_logs` | Fetch project logs |
| `create_branch` | Create development branch |
| `list_branches` | List all branches |
| `merge_branch` | Merge branch to production |

---

## 🎯 Usage Examples

### Example 1: Execute Query

**Prompt**:
```
Query the users table and show me all users created in the last 7 days
```

**Result**: Executes `SELECT * FROM users WHERE created_at > NOW() - INTERVAL '7 days'`

### Example 2: Generate Types

**Prompt**:
```
Generate TypeScript types for my database schema
```

**Result**: Returns TypeScript interfaces for all tables, synced with current schema

---

## 🔗 Related Resources

- **Official Repository**: [supabase-community/supabase-mcp](https://github.com/supabase-community/supabase-mcp)
- **NPM Package**: [@supabase/mcp-server](https://www.npmjs.com/package/@supabase/mcp-server)
- **Supabase Docs**: [supabase.com/docs](https://supabase.com/docs)
- **Access Tokens**: [Dashboard Tokens](https://supabase.com/dashboard/account/tokens)

---

## 💡 Tips & Best Practices

1. **Use project scoping** to limit access to single project
2. **Enable read-only mode** for safer operations

---

## 🐛 Troubleshooting Checklist

- [ ] Node.js ≥ 18.0.0
- [ ] Supabase access token created
- [ ] Token not expired (check expiration date)
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "supabase"

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/supabase-community/supabase-mcp/issues)
- **Supabase Support**: [supabase.com/support](https://supabase.com/support)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (@supabase/mcp-server)
**Status**: ✅ Official Supabase Release

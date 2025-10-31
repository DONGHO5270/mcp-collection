# python-toolbox-mcp Server

> Comprehensive Python development toolkit: code analysis, formatting, execution, and dependency management

[![GitHub](https://img.shields.io/badge/GitHub-gianlucamazza%2Fmcp--python--toolbox-blue)](https://github.com/gianlucamazza/mcp_python_toolbox)
[![PyPI](https://img.shields.io/badge/PyPI-mcp--toolbox-red)](https://pypi.org/project/mcp-toolbox/)
[![Status](https://img.shields.io/badge/Status-Stable-green)]()

## 📌 What is python-toolbox-mcp?

**python-toolbox-mcp** is a comprehensive MCP server that provides AI assistants with professional Python development capabilities. It enables Claude to manage Python projects, analyze code structure, format source files, execute scripts safely, and handle dependencies and virtual environments—all through a standardized interface.

### Key Features

- **File & Directory Management**: Read, write, update Python project files
- **Code Analysis**: Analyze Python file structure (classes, functions, imports)
- **Code Formatting**: Format Python code with Black or autopep8
- **Linting**: Run pylint/flake8 for code quality checks
- **Safe Execution**: Execute Python scripts in isolated environments
- **Virtual Environment Management**: Create and manage venv/virtualenv
- **Dependency Management**: Install packages, list dependencies, check conflicts
- **Package Operations**: Search PyPI, check versions, view documentation

### Use Cases

✅ **Code Quality**: Analyze and format Python codebases automatically
✅ **Development Workflow**: Manage dependencies and virtual environments
✅ **Script Execution**: Run Python code safely with result capture
✅ **Project Setup**: Initialize Python projects with best practices
✅ **Refactoring Support**: Analyze code structure before changes

### When to Use

- When need Python code analysis and formatting
- When managing Python project dependencies
- When executing Python scripts through AI assistance
- When setting up Python development environments
- When conducting code quality checks

---

## 🔧 Manual Installation

### Prerequisites

- **Python**: v3.10 or higher
- **pip**: Latest version
- **Claude Desktop**: Latest version

### Step 1: Install Package

```bash
pip install mcp-toolbox
```

Or using uvx (recommended):
```bash
uvx --prerelease=allow mcp-toolbox@latest
```

### Step 2: Configure Claude Desktop

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
    "python-toolbox": {
      "command": "uvx",
      "args": [
        "--prerelease=allow",
        "mcp-toolbox@latest",
        "stdio"
      ]
    }
  }
}
```

**Alternative** (using pip):
```json
{
  "mcpServers": {
    "python-toolbox": {
      "command": "python",
      "args": [
        "-m",
        "mcp_toolbox"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

1. Quit Claude Desktop completely
2. Relaunch Claude Desktop
3. Check MCP icon (bottom-right)
4. Verify "python-toolbox" is listed

### Step 4: Test Installation

In Claude Desktop:
```
Analyze my Python file at C:/Projects/my-app/main.py
```

Claude will use `analyze_python_file` to extract classes, functions, imports.

---

## ⚙️ Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `VENV_DIR` | `.venv` | Virtual environment directory |
| `MAX_EXECUTION_TIME` | `30` | Script timeout (seconds) |
| `FORMATTER` | `black` | Code formatter (black/autopep8) |

Example with custom settings:
```json
{
  "env": {
    "MAX_EXECUTION_TIME": "60",
    "FORMATTER": "black"
  }
}
```

---

## 🚨 Common Issues & Solutions

### Issue 1: "Command not found: uvx"

**Symptoms**: Error launching server

**Solutions**:

1. **Install uv**:
   ```bash
   pip install uv
   ```

2. **Use pip alternative**:
   ```json
   {
     "command": "python",
     "args": ["-m", "mcp_toolbox"]
   }
   ```

### Issue 2: Script execution fails

**Symptoms**: Error "Execution timeout" or "Permission denied"

**Solutions**:

1. **Increase timeout**:
   ```json
   {
     "env": {
       "MAX_EXECUTION_TIME": "120"
     }
   }
   ```

2. **Check script permissions** and verify Python path

---

## 🔄 Alternative Methods

### Method 1: Direct pip Installation

```bash
pip install mcp-toolbox
python -m mcp_toolbox
```

Configure with:
```json
{
  "command": "python",
  "args": ["-m", "mcp_toolbox"]
}
```

**Pros**: Simple, no extra tools
**Cons**: Manual version management

---

## 📚 Available Tools

| Tool | Description |
|------|-------------|
| `read_file` | Read file contents with optional line range |
| `write_file` | Write content to file (create/overwrite) |
| `delete_file` | Delete a file |
| `list_directory` | List directory contents |
| `analyze_python_file` | Extract classes, functions, imports |
| `format_code` | Format Python code (Black/autopep8) |
| `lint_code` | Run linting (pylint/flake8) |
| `execute_python` | Execute Python code safely |
| `create_venv` | Create virtual environment |
| `install_dependencies` | Install packages from requirements |
| `list_packages` | List installed packages |
| `check_conflicts` | Check dependency conflicts |

---

## 🎯 Usage Examples

### Example 1: Analyze Python File

**Prompt**:
```
Analyze the structure of my Python file at C:/Projects/app/models.py
```

**Result**: Returns classes (User, Product), functions (validate_email), imports, method signatures

### Example 2: Format and Execute

**Prompt**:
```
Format this code with Black and execute: def calc(x,y): return x+y
```

**Result**: Returns formatted code + execution result

---

## 🔗 Related Resources

- **Official Repository**: [gianlucamazza/mcp_python_toolbox](https://github.com/gianlucamazza/mcp_python_toolbox)
- **PyPI Package**: [mcp-toolbox](https://pypi.org/project/mcp-toolbox/)
- **Python Documentation**: [python.org](https://www.python.org)
- **Black Formatter**: [black.readthedocs.io](https://black.readthedocs.io)

---

## 💡 Tips & Best Practices

1. **Use virtual environments** for isolated dependency management
2. **Format before commit** to maintain code consistency

---

## 🐛 Troubleshooting Checklist

- [ ] Python ≥ 3.10
- [ ] `pip install mcp-toolbox` completed
- [ ] JSON config syntax valid
- [ ] Claude Desktop fully restarted
- [ ] MCP icon shows "python-toolbox"
- [ ] File paths are absolute, not relative

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/gianlucamazza/mcp_python_toolbox/issues)
- **Premium Support**: [MCP Collection Premium](https://gumroad.com/l/mcp-collection-premium)

---

**Last Updated**: 2025-10-31
**Version**: Latest (mcp-toolbox)
**Status**: ✅ Stable

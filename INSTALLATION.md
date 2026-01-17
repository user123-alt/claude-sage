# Installation Guide

## 🚀 Method 1: Let Claude Do It (Recommended)

The easiest way to install this workflow system is to let Claude Code install it for you.

### Steps:

1. **Open Claude Code CLI:**
   ```bash
   claude
   ```

2. **Give Claude this exact message:**
   ```
   Install the Claude Professional Workflow system from:
   https://github.com/arikusi/claude-sage

   Please:
   1. Clone the repository to a temporary location
   2. Copy all files from agents/ to ~/.claude/agents/
   3. Copy all files from commands/ to ~/.claude/commands/
   4. Copy WORKFLOW-GUIDE.md to ~/.claude/
   5. Merge settings.template.json with my existing ~/.claude/settings.json
   6. Show me what was installed
   7. Clean up the temporary clone
   ```

3. **Done!** Claude will handle everything.

---

## 🛠️ Method 2: Manual Installation

If you prefer manual installation:

### On macOS/Linux:

```bash
# Clone the repository
git clone https://github.com/arikusi/claude-sage
cd claude-sage

# Create directories if they don't exist
mkdir -p ~/.claude/agents
mkdir -p ~/.claude/commands

# Copy agents
cp agents/*.md ~/.claude/agents/

# Copy commands
cp commands/*.md ~/.claude/commands/

# Copy workflow guide
cp WORKFLOW-GUIDE.md ~/.claude/

# Merge settings (careful - don't overwrite existing settings!)
# Option 1: Manual merge (recommended)
cat settings.template.json
# Then manually add to your ~/.claude/settings.json

# Option 2: Backup and replace (only if no existing settings)
cp settings.template.json ~/.claude/settings.json

# Clean up
cd ..
rm -rf claude-sage
```

### On Windows (PowerShell):

```powershell
# Clone the repository
git clone https://github.com/arikusi/claude-sage
cd claude-sage

# Create directories if they don't exist
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\agents"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\commands"

# Copy agents
Copy-Item -Path "agents\*.md" -Destination "$env:USERPROFILE\.claude\agents\"

# Copy commands
Copy-Item -Path "commands\*.md" -Destination "$env:USERPROFILE\.claude\commands\"

# Copy workflow guide
Copy-Item -Path "WORKFLOW-GUIDE.md" -Destination "$env:USERPROFILE\.claude\"

# Settings (manual merge recommended)
Get-Content settings.template.json
# Manually merge with your existing settings.json

# Clean up
cd ..
Remove-Item -Recurse -Force claude-sage
```

---

## ✅ Verify Installation

```bash
# Check agents
ls ~/.claude/agents/

# Should show:
# - problem-analyst.md
# - solution-architect.md
# - horizon-explorer.md
# - controlled-fixer.md

# Check commands
ls ~/.claude/commands/

# Should show:
# - analyze.md
# - architect.md
# - explore.md
# - fix.md
# - setup-project.md

# Check workflow guide
ls ~/.claude/WORKFLOW-GUIDE.md

# Test an agent
claude
> "/analyze test the problem-analyst agent"
```

---

## 🔧 Configuration

### ⚡ MCP Servers - HIGHLY RECOMMENDED!

**You really, really want these.** The workflow system works without them, but you'd be missing out on *massive* capabilities—especially for the `horizon-explorer` agent.

#### 🔍 Exa (Code & Web Search) - ESSENTIAL
This is what makes `horizon-explorer` so powerful. Without it, you're basically driving with your eyes closed.

**Step 1:** Get your FREE API key from [exa.ai](https://exa.ai)

**Step 2:** Install with one command:
```bash
claude mcp add -s user exa npx exa-mcp-server -e EXA_API_KEY=your-exa-api-key
```

Replace `your-exa-api-key` with your actual API key.

**What you get:**
- `mcp__exa__get_code_context_exa`: Fresh code examples, API docs, real implementations
- `mcp__exa__web_search_exa`: Bleeding-edge solutions, case studies, industry insights

#### 📚 Context7 (Auto-documentation) - ESSENTIAL
Up-to-date library documentation. Claude will automatically fetch the latest docs when you're working with any library.

```bash
claude mcp add context7
# Follow the prompts
```

**What you get:**
- Latest API references
- Version-specific documentation
- Migration guides

#### 🤖 DeepSeek (R1 Model) - OPTIONAL
If you want access to DeepSeek's reasoning model, you can use this MCP server:

**Recommended:** [arikusi/deepseek-mcp-server](https://github.com/arikusi/deepseek-mcp-server)

Follow the **Manual Installation** instructions in the repository README.

_(You can also use other DeepSeek MCP servers if you prefer. Contributions to the above project are very welcome!)_

---

### ⚠️ Without MCP Servers

If you skip MCP setup:
- ✅ Basic workflow still works (analyze → architect → fix)
- ❌ `horizon-explorer` loses 80% of its research power
- ❌ No automatic library documentation
- ❌ No fresh code examples from the wild

**Bottom line:** Take 5 minutes to set these up. You'll thank yourself later.

---

## 📝 Settings Merge Guide

Your `~/.claude/settings.json` should include:

```json
{
  "model": "sonnet",
  "alwaysThinkingEnabled": true,

  "permissions": {
    "defaultMode": "default",
    "allow": [
      "Bash(npm:*)",
      "Bash(git:*)",
      "Bash(python:*)",
      "Bash(node:*)",
      "Read(*)",
      "Grep(*)",
      "Glob(*)"
    ],
    "deny": [
      "Bash(rm:-rf:*)",
      "Bash(rm:-fr:*)",
      "Bash(del:*)"
    ]
  },

  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'File updated: $FILE'"
          }
        ]
      }
    ]
  },

  "env": {
    "MAX_THINKING_TOKENS": "31999",
    "ENABLE_TOOL_SEARCH": "auto"
  }
}
```

**Important:** If you have existing settings, merge carefully. Don't overwrite your current configuration.

---

## 🎯 First Steps After Installation

### 1. Test the System

```bash
claude
> "/analyze why is my test suite slow?"
```

You should see problem-analyst activate and analyze without making any changes.

### 2. Read the Workflow Guide

```bash
cat ~/.claude/WORKFLOW-GUIDE.md
```

### 3. Try a Complete Workflow

```bash
claude
> "I have a bug in my authentication code"
> "/analyze [describe the bug]"
# Review the analysis
> "Looks good, please fix it"
> "/fix"
# controlled-fixer will make test-driven changes
```

---

## 🚨 Troubleshooting

### Problem: Agents not found

**Solution:**
```bash
ls ~/.claude/agents/
# If empty, re-run installation
```

### Problem: Commands don't work

**Solution:**
```bash
ls ~/.claude/commands/
# Verify files exist
# Restart Claude Code CLI
```

### Problem: Settings conflict

**Solution:**
```bash
# Backup current settings
cp ~/.claude/settings.json ~/.claude/settings.json.backup

# Manually merge settings.template.json
# Or ask Claude to help:
claude
> "Merge settings.template.json with my current settings.json"
```

### Problem: MCP servers not working

**Solution:**
```bash
# List configured MCP servers
claude mcp list

# Re-add if needed
claude mcp add context7
```

---

## 🔄 Updating

To update to the latest version:

```bash
claude
> "Update the Claude Professional Workflow system from:
   https://github.com/arikusi/claude-sage

   Back up existing agents first, then replace with new versions."
```

---

## 🗑️ Uninstallation

```bash
# Remove agents
rm ~/.claude/agents/problem-analyst.md
rm ~/.claude/agents/solution-architect.md
rm ~/.claude/agents/horizon-explorer.md
rm ~/.claude/agents/controlled-fixer.md

# Remove commands
rm ~/.claude/commands/analyze.md
rm ~/.claude/commands/architect.md
rm ~/.claude/commands/explore.md
rm ~/.claude/commands/fix.md
rm ~/.claude/commands/setup-project.md

# Remove guide
rm ~/.claude/WORKFLOW-GUIDE.md

# Settings remain (manual cleanup if desired)
```

---

## 📞 Need Help?

1. **Check installation**: Verify all files are in place
2. **Read WORKFLOW-GUIDE.md**: Comprehensive documentation
3. **Ask Claude**: `claude` then "Help me troubleshoot the professional workflow system"
4. **File an issue**: [GitHub Issues](https://github.com/arikusi/claude-sage/issues)

---

**Installation complete!** 🎉

Start with `/analyze` and build quality software.

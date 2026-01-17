# Instructions for Claude Code

This repository contains a professional workflow system for Claude Code CLI.

## Installation Instructions

When a user asks you to install this workflow system:

### Steps:

1. **Verify current location:**
   ```bash
   pwd
   ls
   ```

2. **Clone if needed (temporary location):**
   ```bash
   git clone [repo-url] /tmp/claude-workflow-install
   cd /tmp/claude-workflow-install
   ```

3. **Create directories:**
   ```bash
   mkdir -p ~/.claude/agents
   mkdir -p ~/.claude/commands
   ```

4. **Copy agents:**
   ```bash
   cp agents/*.md ~/.claude/agents/
   ```

5. **Copy commands:**
   ```bash
   cp commands/*.md ~/.claude/commands/
   ```

6. **Copy workflow guide:**
   ```bash
   cp WORKFLOW-GUIDE.md ~/.claude/
   ```

7. **Settings merge (CAREFUL):**
   ```bash
   # Read existing settings first
   cat ~/.claude/settings.json

   # Then show template
   cat settings.template.json

   # Ask user: "Should I merge these settings or show you how to merge manually?"
   ```

8. **Verify installation:**
   ```bash
   ls -la ~/.claude/agents/
   ls -la ~/.claude/commands/
   ls ~/.claude/WORKFLOW-GUIDE.md
   ```

9. **Clean up:**
   ```bash
   cd ~
   rm -rf /tmp/claude-workflow-install
   ```

10. **Report:**
    ```
    ✅ Installation complete!

    Installed agents:
    - problem-analyst
    - solution-architect
    - horizon-explorer
    - controlled-fixer

    Installed commands:
    - /analyze
    - /architect
    - /explore
    - /fix
    - /setup-project

    Documentation:
    - ~/.claude/WORKFLOW-GUIDE.md

    ⚠️  IMPORTANT - Don't skip this:
    Install MCP servers for full power (Context7 + Exa)
    See: INSTALLATION.md#-mcp-servers---highly-recommended

    Without MCPs, horizon-explorer loses 80% of its capabilities!

    Next steps:
    1. Set up MCP servers (5 minutes, huge impact!)
    2. Read WORKFLOW-GUIDE.md
    3. Try: /analyze [describe a problem]
    4. Enjoy professional workflows!
    ```

## Usage Instructions

When users want to use the workflow:

### Basic Commands

- `/analyze` - Deep problem analysis (no code changes)
- `/architect` - Strategic planning (ultrathink mode)
- `/explore` - Alternative perspectives
- `/fix` - Careful implementation (with approval)

### Workflow Pattern

1. **Always analyze first:** `/analyze [problem]`
2. **For critical decisions:** `/architect [decision]`
3. **When stuck:** `/explore [context]`
4. **Only after approval:** `/fix`

### Agent Calling

If user says "analyze this bug" or similar:
```
Use the Skill tool to call: analyze
Or directly: "I'll call the problem-analyst agent..."
```

## Important Notes

- **Never skip analysis** - problem-analyst must run first
- **No quick fixes** - controlled-fixer only runs with approval
- **Ultrathink for critical** - solution-architect uses deep thinking
- **Fresh perspectives** - horizon-explorer has Exa MCP access

## File Structure

```
agents/
  problem-analyst.md      # Analysis only, no code changes
  solution-architect.md   # Ultrathink strategic planning
  horizon-explorer.md     # Alternative research
  controlled-fixer.md     # Careful implementation

commands/
  analyze.md             # Calls problem-analyst
  architect.md           # Calls solution-architect
  explore.md             # Calls horizon-explorer
  fix.md                 # Calls controlled-fixer
  setup-project.md       # Project initialization

WORKFLOW-GUIDE.md        # Comprehensive documentation
settings.template.json   # Configuration template
```

## MCP Requirements

For full functionality:
- ✅ context7 (documentation)
- ✅ exa (code & web search)
- ⚠️ deepseek (optional) - Recommended: https://github.com/arikusi/deepseek-mcp-server

## Philosophy

**"Analyze First, Fix Later"**

1. Understand deeply (problem-analyst)
2. Plan strategically (solution-architect)
3. Consider alternatives (horizon-explorer)
4. Execute carefully (controlled-fixer)

No quick fixes. Quality over speed.

# Claude Sage 🧙‍♂️

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/arikusi/claude-sage/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-v2.0%2B-purple.svg)](https://code.anthropic.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Author](https://img.shields.io/badge/by-arikusi-orange.svg)](https://github.com/arikusi)

> **"Analyze First, Fix Later"** - Production-grade workflow system for Claude Code CLI

A professional agent-based workflow system for Claude Code that emphasizes careful analysis, strategic planning, and controlled implementation. No more quick fixes that become technical debt.

---

## 📢 Hey there! A quick note before you start

**Language Notice:** I originally wrote this system in Turkish (my native language) since that's how I work with Claude daily. Here's the thing though—Claude is *ridiculously* good at understanding Turkish (and most languages, really), so **you can absolutely use this as-is** without translating anything. The agents will understand you perfectly whether you speak to them in English, Turkish, Spanish, or whatever language you prefer.

That said, if you'd rather work in English, feel free to translate the agent instructions before installation. It's totally up to you and your workflow preferences!

**MCP Servers - Seriously, install these:** I *highly* recommend setting up the MCP servers (especially **Context7** and **Exa**). They're what make the `horizon-explorer` agent so powerful. Without them, you're missing out on:
- 🔍 **Exa Code Context**: Fresh, real-world code examples and API documentation
- 🌐 **Exa Web Search**: Bleeding-edge solutions and industry insights
- 📚 **Context7**: Up-to-date library documentation

Trust me, these aren't optional nice-to-haves—they're game-changers. See [Installation Guide](INSTALLATION.md#required-mcp-servers) for setup instructions.

---

## 🎯 Core Philosophy

**Stop rushing into fixes. Start building right.**

This system replaces the "quick fix" mentality with a structured, multi-agent approach:
1. **Analyze** the problem deeply (no code changes)
2. **Architect** the solution strategically (ultrathink mode)
3. **Explore** alternative perspectives (when stuck)
4. **Fix** carefully with explicit approval (test-driven)

---

## ⚡ Quick Start

**Installation is dead simple. Just give Claude this repository URL:**

```bash
# Open Claude Code CLI
claude

# Then say:
"Clone this repository and install the professional workflow system:
https://github.com/arikusi/claude-sage

Copy agents to ~/.claude/agents/
Copy commands to ~/.claude/commands/
Copy settings.template.json to ~/.claude/settings.json (merge with existing)
Copy WORKFLOW-GUIDE.md to ~/.claude/"
```

That's it! Claude will set everything up for you.

---

## 🤖 The Agent Team

### 1. **problem-analyst**
- **Role**: Forensic investigator
- **Tools**: Read, Grep, Glob, Bash (read-only)
- **Powers**: ❌ Cannot write/edit code
- **Purpose**: Deep root cause analysis, impact assessment, reporting

**When to use:** `/analyze [problem description]`

### 2. **solution-architect**
- **Role**: Strategic architect
- **Tools**: Read, Grep, Glob, Bash (read-only)
- **Powers**: ❌ Cannot write/edit code, Ultrathink mode enabled
- **Purpose**: Architecture decisions, trade-off analysis, 3+ alternative approaches

**When to use:** `/architect [architectural decision]`

### 3. **horizon-explorer**
- **Role**: Lateral thinker
- **Tools**: Read, Grep, Glob, Bash, Exa MCP, Context7, WebSearch
- **Powers**: ❌ Cannot write/edit code, Research superpowers
- **Purpose**: Alternative perspectives, unconventional solutions, "are we looking in the right place?"

**When to use:** `/explore [stuck problem]`

### 4. **controlled-fixer**
- **Role**: Careful surgeon
- **Tools**: Read, Grep, Glob, Edit, Write, Bash
- **Powers**: ✅ Can modify code (ONLY with explicit approval)
- **Purpose**: Test-driven, reversible, minimal-impact fixes

**When to use:** `/fix` (after analysis and approval)

---

## 📋 Quick Commands

| Command | Calls | What It Does | Modifies Code? |
|---------|-------|--------------|----------------|
| `/analyze` | problem-analyst | Deep problem analysis + report | ❌ No |
| `/architect` | solution-architect | Strategic planning (ultrathink) | ❌ No |
| `/explore` | horizon-explorer | Alternative approaches | ❌ No |
| `/fix` | controlled-fixer | Careful implementation | ✅ Yes (if approved) |
| `/setup-project` | — | Initialize Claude for new project | ✅ Yes |

---

## 🔄 Standard Workflows

### Workflow 1: Simple Bug Fix

```
1. /analyze "npm test failing on auth module"
   → problem-analyst: detailed analysis + root cause

2. You: "Okay, proceed with the fix"
   → /fix
   → controlled-fixer: test-driven fix + validation
```

### Workflow 2: Critical Architectural Decision

```
1. /analyze "should we migrate to microservices?"
   → problem-analyst: current state analysis

2. /architect "microservices migration strategy"
   → solution-architect: 3+ approaches, trade-offs, risks

3. You: decide which approach

4. /fix [chosen approach]
   → controlled-fixer: careful implementation
```

### Workflow 3: Stuck for Hours

```
1. /explore "we can't solve the race condition in our queue"
   → horizon-explorer: alternative patterns, different tech stacks
   → "Are we looking in the right place?"

2. /analyze [new perspective]
   → problem-analyst: re-analyze with new insights

3. /architect [solution]
   → solution-architect: strategic plan

4. /fix
   → controlled-fixer: implementation
```

---

## 🎓 Best Practices

### DO ✅

1. **Always start with /analyze** - Never skip understanding
2. **Use /architect for critical changes** - Get strategic guidance
3. **Call /explore when stuck** - Fresh perspective
4. **Approve before /fix** - Controlled changes only
5. **Request "ultrathink"** - For complex decisions

### DON'T ❌

1. **Skip analysis** - Understanding > Speed
2. **Quick fixes** - Today's shortcut = Tomorrow's debt
3. **Single perspective** - Use /explore when uncertain
4. **Untested production changes** - controlled-fixer enforces tests
5. **Breaking changes without warning** - Agents will flag

---

## 🛠️ Features

### Intelligent Permissions
```json
{
  "allow": ["Bash(git:*)", "Bash(npm:*)"],
  "deny": ["Bash(rm:-rf:*)"]
}
```

### Post-Tool Hooks
```json
{
  "PostToolUse": [{
    "matcher": "Edit|Write",
    "hooks": [{"command": "prettier --write $FILE"}]
  }]
}
```

### Extended Thinking
```json
{
  "env": {
    "MAX_THINKING_TOKENS": "31999"
  }
}
```

### MCP Integration (Highly Recommended!)
The workflow system is *significantly* more powerful with MCP servers:

- **Exa Code Context** 🔍: Real-world code examples, API documentation, implementation patterns
- **Exa Web Search** 🌐: Bleeding-edge solutions, case studies, industry insights
- **Context7** 📚: Automatic, up-to-date library documentation

**Without MCPs:** Basic workflow works, but `horizon-explorer` loses 80% of its research capabilities.
**With MCPs:** Full-powered alternative research, fresh code examples, and comprehensive documentation.

[Setup takes 5 minutes →](INSTALLATION.md#-mcp-servers---highly-recommended)

---

## 📚 Documentation

- **WORKFLOW-GUIDE.md**: Comprehensive workflow documentation
- **Agent files**: Each agent has detailed instructions
- **Command files**: Slash command definitions

---

## 🔍 Agent Decision Matrix

| Scenario | Agent | Why |
|----------|-------|-----|
| "Why is this failing?" | problem-analyst | Analysis without changes |
| "Should we use GraphQL or REST?" | solution-architect | Strategic trade-offs |
| "We've been stuck for 3 hours" | horizon-explorer | New perspective |
| "Implement the approved fix" | controlled-fixer | Careful execution |
| "Cron job failing intermittently" | problem-analyst → architect | Race conditions need deep analysis |
| "Database migration strategy" | architect | Critical architectural decision |

---

## 🚀 Advanced Usage

### For Teams

1. Clone to your project:
   ```bash
   git clone https://github.com/arikusi/claude-sage .claude-setup
   ```

2. Project-specific setup:
   ```bash
   cp -r .claude-setup/agents .claude/agents/
   cp -r .claude-setup/commands .claude/commands/
   ```

3. Commit `.claude/` to version control (except `.local.json`)

### Custom Agents

Add your own agents to `~/.claude/agents/`:

```markdown
---
name: your-agent
description: What it does
tools: Read, Grep
disallowedTools: Write, Edit
model: sonnet
---

# Your Agent Instructions

...
```

---

## 🤝 Contributing

Improvements welcome! This system is designed to evolve with your team's needs.

**Ideas for contributions:**
- Additional specialized agents (security-auditor, performance-profiler, etc.)
- Enhanced hooks (pre-commit, linting, etc.)
- Project-specific templates
- Integration examples

---

## 📊 Why This System?

### Traditional Approach
```
Problem → Quick Fix → Technical Debt → More Problems
```

### Professional Workflow
```
Problem → Analysis → Strategic Plan → Approved Fix → Quality Code
```

### Results
- ✅ Fewer regressions
- ✅ Better architecture decisions
- ✅ Less technical debt
- ✅ Team alignment
- ✅ Maintainable codebase

---

## 🎯 Perfect For

- ✅ Production systems (careful changes required)
- ✅ Team environments (approval workflows)
- ✅ Complex codebases (deep analysis needed)
- ✅ Critical infrastructure (can't afford mistakes)
- ✅ Learning projects (understand before changing)

---

## 📞 Support

**Having issues?**

```bash
# Check installation
ls ~/.claude/agents/
ls ~/.claude/commands/

# Verify settings
cat ~/.claude/settings.json

# Test an agent
claude
> "Call problem-analyst and analyze this test failure"
```

**Common Issues:**

1. **Agent not found**: Check `~/.claude/agents/` directory
2. **Command not working**: Verify `~/.claude/commands/` directory
3. **Settings conflict**: Merge carefully with existing settings

---

## 🏆 Success Stories

> "We were about to make a breaking API change. /architect helped us find a backward-compatible approach that saved us from a disaster." - Backend Team

> "Spent 5 hours debugging. Called /explore and realized we were looking at the wrong service entirely." - DevOps Engineer

> "No more 'quick fixes' in production. Every change is analyzed first." - Platform Team

---

## 📜 License

MIT - Use freely, contribute generously, build carefully.

---

## 🔮 Roadmap

- [ ] Additional agents (security, performance, docs)
- [ ] Pre-built hooks library
- [ ] Project templates (React, Node.js, Python, etc.)
- [ ] CI/CD integration examples
- [ ] VS Code extension integration
- [ ] Team collaboration features

---

**Remember:** *"Quick fix bugün, big problem yarın."*

Build it right the first time. Your future self will thank you.

---

**Version:** 1.0.0
**Last Updated:** 2026-01-17
**Maintained by:** Community
**Built for:** Claude Code CLI v2.0+

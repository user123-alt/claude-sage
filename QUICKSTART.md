# Quick Start Guide

Get up and running with Claude Professional Workflow in 5 minutes.

> **🚨 Don't skip:** After installing, set up MCP servers (Context7 + Exa). They're what make this system truly powerful. [See why →](INSTALLATION.md#-mcp-servers---highly-recommended)

## ⚡ 60-Second Installation

```bash
# Open Claude Code
claude

# Paste this:
Install Claude Professional Workflow from this repository:
[https://github.com/arikusi/claude-sage]
```

Claude will install everything automatically.

## 🎯 Your First Workflow

### Example 1: Debug a Bug

```bash
claude

You: "I'm getting a TypeError in my API handler"

Claude: [analyzing the problem]

You: "/analyze the TypeError in api/users.js line 45"

# problem-analyst will:
# - Read the code
# - Trace the error
# - Find root cause
# - Report WITHOUT changing code

Claude: [detailed analysis report]

You: "Looks good, fix it please"

# Now use /fix
You: "/fix"

# controlled-fixer will:
# - Make minimal changes
# - Run tests
# - Verify the fix
# - Report results
```

### Example 2: Architectural Decision

```bash
You: "Should we use GraphQL or REST for our new microservice?"

You: "/architect compare GraphQL vs REST for microservices"

# solution-architect will:
# - Analyze your codebase
# - Consider 3+ approaches
# - Trade-off matrix
# - Risk analysis
# - Recommendations

Claude: [comprehensive architectural analysis with ultrathink]

You: [choose approach based on analysis]
```

### Example 3: Stuck on a Problem

```bash
You: "We've been debugging this race condition for 3 hours"

You: "/explore race condition in message queue"

# horizon-explorer will:
# - Search alternative patterns (Exa Code Context)
# - Check how others solved it (Exa Web Search)
# - Suggest unconventional approaches
# - Ask "Are we looking in the right place?"

Claude: [fresh perspectives + alternative solutions]

You: "/analyze [chosen alternative]"
```

## 📋 Command Cheat Sheet

| Command | When | What |
|---------|------|------|
| `/analyze [issue]` | Always start here | Deep analysis, no changes |
| `/architect [decision]` | Critical choices | Strategic planning + ultrathink |
| `/explore [problem]` | When stuck | Alternative perspectives |
| `/fix` | After approval | Careful implementation |

## 🎓 The Golden Rule

```
┌─────────────────────────────────┐
│  Never /fix before /analyze     │
│                                 │
│  Understanding > Speed          │
└─────────────────────────────────┘
```

## 🔄 Basic Workflow Pattern

```
Problem
  ↓
/analyze (understand)
  ↓
Review Analysis
  ↓
Critical? → YES → /architect (plan)
  ↓         NO ↓
  ↓         /fix (implement)
  ↓
/fix (implement)
```

## 🚨 Common Mistakes

### ❌ DON'T DO THIS:

```bash
You: "Fix the bug in auth.js"
# Wrong! No analysis first
```

### ✅ DO THIS:

```bash
You: "/analyze bug in auth.js line 23"
# Analyze first
# Then after review:
You: "/fix"
```

## 🎯 Real-World Examples

### Bug Fix

```
Problem: "npm test failing on AuthService"

Flow:
1. /analyze "test failures in AuthService"
2. Review: Root cause is missing await
3. /fix
4. Done ✅
```

### Feature Addition

```
Problem: "Add rate limiting to API"

Flow:
1. /architect "rate limiting strategy for Express API"
2. Review: 3 options (Redis, in-memory, middleware)
3. Choose: Redis-based
4. /fix
5. Done ✅
```

### Performance Issue

```
Problem: "Database queries are slow"

Flow:
1. /analyze "slow queries in UserRepository"
2. Review: N+1 query problem
3. /architect "fix N+1 with optimal strategy"
4. Review: Use DataLoader or JOIN
5. /fix
6. Done ✅
```

### Stuck Debugging

```
Problem: "Can't find why cache is stale"

Flow:
1. /analyze "cache staleness in SessionManager"
2. Review: Symptom found but root cause unclear
3. /explore "cache invalidation patterns"
4. Insight: TTL vs event-based invalidation
5. /analyze "event-based cache invalidation"
6. Review: Clear path forward
7. /fix
8. Done ✅
```

## 💡 Pro Tips

### Tip 1: Always Include Context

❌ Bad: `/analyze the bug`
✅ Good: `/analyze TypeError in api/users.js:45 when POST /users`

### Tip 2: Use "ultrathink" for Complex Problems

```bash
You: "Analyze this race condition with ultrathink"
# Triggers extended thinking mode (31,999 tokens)
```

### Tip 3: Chain Workflows

```bash
You: "/analyze [problem]"
# Review
You: "This seems critical, /architect [approach]"
# Review
You: "Approach B looks best, /fix with approach B"
```

### Tip 4: Background Research

```bash
You: "/explore latest patterns for [technology] in 2026"
# horizon-explorer uses Exa to find cutting-edge solutions
```

## 📚 Next Steps

1. **Read WORKFLOW-GUIDE.md** for comprehensive documentation
2. **Try each command** with real problems
3. **Experiment** with different workflows
4. **Share feedback** via issues

## 🆘 Need Help?

```bash
# In Claude Code:
You: "Show me examples of /analyze usage"
You: "What's the difference between /analyze and /architect?"
You: "Help me understand the workflow system"
```

## 🎉 You're Ready!

Start with a real problem:

```bash
claude

You: "/analyze [your actual problem]"
```

**Remember:** Analyze first, fix later. Quality over speed.

---

**Happy coding!** 🚀

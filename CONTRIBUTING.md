# Contributing to Claude Professional Workflow

Thank you for considering contributing! This project thrives on community improvements.

## 🎯 Philosophy

All contributions should align with our core principle:

**"Analyze First, Fix Later" - Quality over Speed**

## 🤝 How to Contribute

### 1. Report Issues

Found a bug or have an idea?

```bash
# Open an issue with:
- Clear description
- Steps to reproduce (for bugs)
- Expected vs actual behavior
- Your environment (OS, Claude Code version)
```

### 2. Suggest New Agents

Have an idea for a new agent?

**Template:**
```markdown
## Agent Name: [name]

**Purpose:** [what problem does it solve?]

**Tools:** [which tools does it need?]

**Code Changes:** [can it modify code? Yes/No]

**When to Use:** [specific scenarios]

**Example:**
```
/[command-name] [example usage]
```
```

### 3. Improve Documentation

Documentation improvements are always welcome:
- Fix typos
- Clarify instructions
- Add examples
- Translate (if multilingual)

### 4. Submit Code

#### Before You Start

1. **Read the existing agents** to understand the pattern
2. **Test locally** before submitting
3. **Follow the philosophy** - no quick fixes

#### Agent Development Guidelines

**Agent Template:**
```markdown
---
name: agent-name
description: Brief description for Claude to understand when to use this
tools: Read, Grep, Glob  # Only what's needed
disallowedTools: Write, Edit  # If read-only
model: sonnet
permissionMode: default
---

# Agent Name - Clear Purpose

## Ne Zaman Çağrılırsın

- Scenario 1
- Scenario 2

## Yetki Sınırları

- ❌ What it cannot do
- ✅ What it can do

## Çalışma Yaklaşımı

### 1. First Step
[Clear instructions]

### 2. Second Step
[Clear instructions]

## Çıktı Formatı

### 📋 REPORT TITLE

[Structured output format]

## Önemli İlkeler

1. Principle 1
2. Principle 2
```

**Key Rules:**
- **Read-only agents**: Use `disallowedTools: Write, Edit, NotebookEdit`
- **Code-changing agents**: Require explicit approval in instructions
- **Clear triggers**: Description should help Claude know when to use it
- **Structured output**: Always provide clear report format

#### Command Development Guidelines

**Command Template:**
```markdown
---
description: Brief description (shows in command palette)
---

[Clear instructions for what the command should do]

[Call the appropriate agent]

[Explain expected behavior]
```

### 5. Pull Request Process

1. **Fork** the repository
2. **Create a branch**: `git checkout -b feature/agent-name`
3. **Make changes**
4. **Test thoroughly**:
   ```bash
   # Copy to your ~/.claude/
   cp agents/new-agent.md ~/.claude/agents/

   # Test in Claude Code
   claude
   > "Test the new agent: [usage example]"
   ```
5. **Commit**: Clear, descriptive messages
6. **Push**: `git push origin feature/agent-name`
7. **Open PR**: Describe what, why, and how

#### PR Checklist

- [ ] Agent/command tested locally
- [ ] Documentation updated
- [ ] CHANGELOG.md updated
- [ ] Follows existing patterns
- [ ] No breaking changes (or clearly documented)
- [ ] Clear use case examples

## 🎨 Coding Standards

### Agent Standards

1. **Naming**: Lowercase with hyphens (`problem-analyst`, not `ProblemAnalyst`)
2. **Description**: Action-oriented, clear triggers
3. **Tools**: Minimal necessary set
4. **Structure**: Follow existing templates
5. **Language**: English or Turkish (consistent within file)

### Documentation Standards

1. **Clear examples**: Show, don't just tell
2. **Real scenarios**: Use practical use cases
3. **Consistent formatting**: Match existing style
4. **Updated CHANGELOG**: Document all changes

## 🚀 Ideas for Contributions

### New Agents (Wishlist)

- **security-auditor**: Security vulnerability scanning
- **performance-profiler**: Performance analysis and optimization
- **test-writer**: Automated test generation
- **doc-generator**: Documentation generation
- **refactor-planner**: Refactoring strategy

### New Features

- **Hooks library**: Pre-built hooks for common tasks
- **Project templates**: React, Node.js, Python, Rust templates
- **CI/CD examples**: GitHub Actions, GitLab CI integration
- **Team features**: Shared configurations, approval workflows

### Improvements

- **Better error handling** in agents
- **More examples** in WORKFLOW-GUIDE.md
- **Video tutorials** (external links)
- **Integration guides** for popular frameworks

## ❓ Questions?

- Open an issue with `[Question]` prefix
- Check existing issues first
- Be specific about your use case

## 🎯 Agent Quality Criteria

A good agent:

1. **Has a clear, specific purpose**
2. **Knows when NOT to run** (specific triggers)
3. **Follows "analyze first" philosophy**
4. **Provides structured output**
5. **Includes examples**
6. **Respects permission boundaries**
7. **Integrates with existing workflow**

## 📜 Code of Conduct

- **Be respectful** - Constructive feedback only
- **Be patient** - We all learn together
- **Be clear** - Specific, actionable feedback
- **Be collaborative** - We're building together

## 🏆 Recognition

Contributors will be:
- Listed in CHANGELOG.md
- Mentioned in release notes
- Credited in agent files (if substantial contribution)

---

**Thank you for helping build better software workflows!** 🚀

Every contribution makes Claude Code more powerful for everyone.

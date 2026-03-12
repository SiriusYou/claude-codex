# Advanced Configuration Guide

**[中文](advanced-zh.md) | English**

## 🔧 Workflow Configuration

### Strict Tool Call Order

As required by CLAUDE.md, tools must be executed in the following strict order:

```json
{
  "workflow": {
    "execution_order": [
      "sequential-thinking",
      "shrimp-task-manager",
      "codex"
    ],
    "working_directory": ".claude"
  }
}
```

### Separation of Responsibilities

**Primary AI (Claude Code) Responsibilities**:
- ✅ Task planning and decomposition (using shrimp-task-manager)
- ✅ Direct code writing (using Read/Edit/Write)
- ✅ Simple logic implementation (<10 lines of core logic)
- ✅ Final decision confirmation (based on Codex suggestions)
- ✅ Decision logging (operations-log.md)

**Codex (Support AI) Responsibilities**:
- ✅ Deep reasoning analysis (using sequential-thinking)
- ✅ Comprehensive code retrieval (thorough codebase scanning)
- ✅ Complex logic design (>10 lines of core logic)
- ✅ Context collection and analysis (output to `.claude/context-*.json`)
- ✅ Quality review scoring (code review, risk identification)

## 📁 Directory Structure Standards

All working files must be written to the project-local `.claude/` directory:

```
<project>/.claude/
├── context-initial.json        ← Initial collection (Codex output)
├── context-question-N.json     ← Deep analysis (Codex output)
├── coding-progress.json        ← Real-time coding status (Primary AI output)
├── operations-log.md           ← Decision log (Primary AI output)
├── review-report.md            ← Review report (Codex output)
├── codex-sessions.json         ← Session management (Codex persistence)
├── shrimp/                     ← Task management data
├── codex/                      ← Codex working data
├── context/                    ← Context data
├── logs/                       ← Log files
└── cache/                      ← Cache data
```

## 🔄 Standard Workflow (6 Steps)

### 1. Analyze Requirements
- Use sequential-thinking for deep requirement understanding
- Codex performs comprehensive context collection

### 2. Gather Context
- Codex executes structured quick scan
- Output to `.claude/context-initial.json`
- Primary AI identifies key questions

### 3. Select Tools
- Choose the right tool combination based on task complexity
- Follow the strict tool call order

### 4. Execute Task
- Primary AI codes directly (simple logic)
- Complex logic delegated to Codex for design
- Real-time updates to `coding-progress.json`

### 5. Verify Quality
- Codex uses sequential-thinking for deep review
- Generates scores and suggestions (written to `.claude/review-report.md`)
- Primary AI makes quick decisions based on suggestions

### 6. Store Knowledge
- Record decision process in `operations-log.md`
- Update context files
- Maintain session state

## 🎯 Codex Call Specifications

### First Call
```javascript
mcp__codex__codex(
  model="gpt-5-codex",
  sandbox="danger-full-access",
  approval-policy="on-failure",
  prompt="[TASK_MARKER: YYYYMMDD-HHMMSS-XXXX]\nObjective: [Task description]\nOutput: [Deliverables list]"
)
```

### Continue Session
```javascript
mcp__codex__codex-reply(conversationId="<ID>", prompt="[Instructions]")
```

### conversationId Management
- Primary AI generates task_marker: `[TASK_MARKER: YYYYMMDD-HHMMSS-XXXX]`
- Codex queries and persists to `.claude/codex-sessions.json`
- Response ends with: `[CONVERSATION_ID]: <conversationId>`

## 📊 Quality Review Scoring System

### Scoring Dimensions
- **Technical Dimension** (code quality, test coverage, standard compliance)
- **Strategic Dimension** (requirement matching, architecture consistency, risk assessment)
- **Overall Score** (0-100)

### Decision Rules
- ≥90 with "pass" recommendation → Approve directly
- <80 with "reject" recommendation → Reject directly
- 80-89 or "needs discussion" recommendation → Careful review before decision

## ⚡ Automated Execution Strategy

### Default Auto-Execute (No Confirmation Needed)
- ✅ All file read/write operations
- ✅ Standard tool calls (code-index, exa, grep, etc.)
- ✅ Code writing, modification, refactoring
- ✅ Documentation generation and updates
- ✅ Test execution and verification scripts
- ✅ Task planning and decomposition, context collection
- ✅ Calling mcp__codex__codex or codex-reply

### Exceptions Requiring Confirmation
- ⚠️ Deleting core configuration files
- ⚠️ Destructive database schema changes
- ⚠️ Git push to remote repository
- ⚠️ Strategy adjustment needed after 3 consecutive identical errors

## 🔍 Advanced Feature Configuration

### Exa Search Configuration
```json
{
  "exa": {
    "command": "npx",
    "args": ["-y", "exa-mcp-server"],
    "env": {
      "EXA_API_KEY": "your-api-key-here",
      "WORKING_DIR": ".claude"
    }
  }
}
```

### Chrome DevTools Integration
```json
{
  "chrome-devtools": {
    "command": "npx",
    "args": ["chrome-devtools-mcp@latest"],
    "env": {
      "WORKING_DIR": ".claude"
    }
  }
}
```

### Code Index Configuration
```json
{
  "code-index": {
    "command": "uvx",
    "args": ["code-index-mcp"],
    "env": {
      "WORKING_DIR": ".claude"
    }
  }
}
```

## 🛠️ Troubleshooting

### Common Issues
1. **Wrong tool call order** → Check workflow.execution_order configuration
2. **Path convention issues** → Ensure all tools use the `.claude/` directory
3. **Session management failures** → Check `.claude/codex-sessions.json` file
4. **Permission issues** → Ensure `.claude/` directory has write permissions

### Debug Commands
```bash
# Verify configuration
./verify-config.sh

# Check tool call order
grep -A 10 "execution_order" .claude/claude_desktop_config.json

# View session state
cat .claude/codex-sessions.json

# Check working directory permissions
ls -la .claude/
```

## 📈 Performance Optimization

### Recommended Settings
- Use SSD storage for improved I/O performance
- Configure sufficient memory (8GB+ recommended)
- Regularly clean the `.claude/cache/` directory
- Use local caching to reduce redundant computation

### Monitoring Metrics
- Tool response time
- Session success rate
- Code review quality scores
- Task completion time

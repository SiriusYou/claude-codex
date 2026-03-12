# API Reference

**[中文](api-zh.md) | English**

## 🔧 MCP Server API

### Sequential-thinking

**Function**: Deep reasoning analysis tool

**Invocation**:
```javascript
// MCP tool call
sequential-thinking.prompt = "Question requiring deep analysis"

// Direct call
npx -y @modelcontextprotocol/server-sequential-thinking
```

**Configuration**:
```json
{
  "type": "stdio",
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"],
  "env": {
    "WORKING_DIR": ".claude"
  }
}
```

**Output Format**:
- Thought process analysis
- Risk identification
- Implementation suggestions
- Boundary condition analysis

### Shrimp Task Manager

**Function**: Task planning and decomposition tool

**Invocation**:
```javascript
// MCP tool call
shrimp-task-manager.create_task({
  name: "Task name",
  description: "Task description",
  priority: "high|medium|low"
})
```

**Configuration**:
```json
{
  "command": "npx",
  "args": ["-y", "mcp-shrimp-task-manager"],
  "env": {
    "DATA_DIR": ".claude/shrimp",
    "TEMPLATES_USE": "en",
    "ENABLE_GUI": "false"
  }
}
```

**Data Structure**:
```json
{
  "task_id": "task-123",
  "name": "Task name",
  "status": "pending|in_progress|completed",
  "priority": "high|medium|low",
  "created_at": "2025-11-05T10:30:00Z",
  "subtasks": []
}
```

### Codex

**Function**: Deep code analysis and generation

**Invocation**:
```javascript
// First call
mcp__codex__codex(
  model="gpt-5-codex",
  sandbox="danger-full-access",
  approval-policy="on-failure",
  prompt="[TASK_MARKER: YYYYMMDD-HHMMSS-XXXX]\nTask description"
)

// Continue session
mcp__codex__codex-reply(conversationId="<ID>", prompt="Follow-up instructions")
```

**Configuration**:
```json
{
  "type": "stdio",
  "command": "codex",
  "args": ["mcp-server"],
  "env": {
    "WORKING_DIR": ".claude"
  }
}
```

**Supported Analysis Types**:
- Codebase scanning and retrieval
- Complex logic design (>10 lines of core logic)
- Quality review and scoring
- Context collection and analysis

### Code Index

**Function**: Code indexing and search

**Invocation**:
```bash
uvx code-index-mcp
```

**Configuration**:
```json
{
  "command": "uvx",
  "args": ["code-index-mcp"],
  "env": {
    "WORKING_DIR": ".claude"
  }
}
```

**Search Syntax**:
- Filename search: `filename:component`
- Content search: `content:function_name`
- Type search: `type:class|function|variable`

### Chrome DevTools

**Function**: Browser debugging tool integration

**Invocation**:
```bash
npx chrome-devtools-mcp@latest
```

**Configuration**:
```json
{
  "command": "npx",
  "args": ["chrome-devtools-mcp@latest"],
  "env": {
    "WORKING_DIR": ".claude"
  }
}
```

**Supported Operations**:
- Page screenshots
- Console log retrieval
- Network request monitoring
- DOM manipulation

### Exa Search

**Function**: Web search and content retrieval

**Invocation**:
```bash
npx -y exa-mcp-server
```

**Configuration**:
```json
{
  "command": "npx",
  "args": ["-y", "exa-mcp-server"],
  "env": {
    "EXA_API_KEY": "your-api-key-here",
    "WORKING_DIR": ".claude"
  }
}
```

**Search Parameters**:
- `query`: Search keywords
- `num_results`: Number of results to return (default 10)
- `include_domains`: Limit search to specific domains
- `exclude_domains`: Exclude specific domains from search

## 📁 Data File API

### Context Files

**context-initial.json**:
```json
{
  "scan_type": "initial",
  "timestamp": "2025-11-05T10:30:00Z",
  "project_location": "Which module/file the feature is in",
  "current_implementation": "How it is currently implemented",
  "similar_cases": ["Similar case 1", "Similar case 2"],
  "tech_stack": ["Framework", "Language", "Dependencies"],
  "testing_info": "Existing test files and verification methods",
  "observations": {
    "anomalies": ["Discovered anomalies"],
    "info_gaps": ["Information gaps"],
    "suggestions": ["Suggested areas for deeper investigation"],
    "risks": ["Potential risks"]
  }
}
```

**context-question-N.json**:
```json
{
  "question_id": "question-1",
  "target_question": "Specific question to resolve",
  "analysis_depth": "deep",
  "evidence": ["Code snippet evidence"],
  "conclusions": ["Analysis conclusions"],
  "recommendations": ["Recommended actions"],
  "timestamp": "2025-11-05T10:35:00Z"
}
```

### Coding Progress File

**coding-progress.json**:
```json
{
  "current_task_id": "task-123",
  "files_modified": ["src/foo.ts", "docs/bar.md"],
  "last_update": "2025-11-05T10:30:00Z",
  "status": "coding|review_needed|completed",
  "pending_questions": ["How to handle edge case X?"],
  "complexity_estimate": "simple|moderate|complex",
  "progress_percentage": 75
}
```

### Session Management File

**codex-sessions.json**:
```json
{
  "sessions": [
    {
      "task_marker": "20251105-1030-001",
      "conversation_id": "conv-123",
      "timestamp": "2025-11-05T10:30:00Z",
      "description": "Task description",
      "status": "active|completed|error"
    }
  ]
}
```

### Review Report File

**review-report.md**:
```markdown
# Code Review Report

## Metadata
- Review Time: 2025-11-05 10:30
- Reviewer: Codex
- Task ID: task-123

## Score Details
- Technical Dimension: 85/100
- Strategic Dimension: 90/100
- Overall Score: 87/100

## Recommendation
Pass / Reject / Needs Discussion

## Checklist Results
- [x] Requirement field completeness
- [x] Code quality standards
- [ ] Test coverage complete

## Risks and Blockers
- Risk point 1
- Blocking issue 1

## Supporting Evidence
1. Evidence 1
2. Evidence 2
```

### Operations Log File

**operations-log.md**:
```markdown
# Operations Log

## 2025-11-05 10:30 - Task Started
- Operation: Start new task
- Tool: sequential-thinking
- Output: Initial analysis complete

## 2025-11-05 10:35 - Context Collection
- Operation: Invoke Codex for code scanning
- Tool: mcp__codex__codex
- Session ID: conv-123
- Output: context-initial.json generated

## 2025-11-05 10:40 - Decision Record
- Decision: Adopt Plan A
- Reason: Better performance, lower maintenance cost
- Overrode Codex suggestion: Yes
- Justification: Special project requirements
```

## 🔄 Workflow API

### Standard Workflow Call

```javascript
// 1. sequential-thinking
sequential_thinking("Analyze task requirements and risks")

// 2. Codex context collection
codex_context_collection({
  type: "structured_scan",
  output_file: ".claude/context-initial.json"
})

// 3. shrimp-task-manager planning
task_manager_create_plan({
  context: ".claude/context-initial.json",
  output_file: ".claude/task-plan.json"
})

// 4. Primary AI coding + Codex review
main_ai_implementation({
  plan: ".claude/task-plan.json"
})
codex_review({
  files: ["src/file1.ts", "src/file2.ts"],
  output_file: ".claude/review-report.md"
})
```

### Error Handling

```javascript
try {
  // Execute workflow
  await execute_workflow()
} catch (error) {
  // Log to operations-log.md
  log_operation("error", error.message)

  // Retry mechanism (up to 3 times)
  if (retry_count < 3) {
    await retry_workflow()
  } else {
    // Escalate to primary AI
    report_to_main_ai(error)
  }
}
```

## 📊 Monitoring API

### Performance Metrics

```javascript
// Get tool response time
const response_time = get_tool_metrics("sequential-thinking")

// Get session success rate
const success_rate = get_session_metrics()

// Get code review quality scores
const quality_scores = get_review_metrics()
```

### Health Check

```javascript
// Check MCP server status
const health_status = {
  "sequential-thinking": check_server_health("sequential-thinking"),
  "codex": check_server_health("codex"),
  "shrimp-task-manager": check_server_health("shrimp-task-manager")
}

// Check file system permissions
const fs_permissions = check_permissions(".claude/")
```

## 🔧 Configuration API

### Dynamic Configuration Updates

```javascript
// Update working directory
update_config("working_directory", ".claude")

// Add new MCP server
add_mcp_server({
  name: "new-tool",
  config: {...}
})

// Update tool call order
update_execution_order([
  "sequential-thinking",
  "shrimp-task-manager",
  "codex",
  "new-tool"
])
```

### Configuration Validation

```javascript
// Validate configuration completeness
const validation_result = validate_config({
  required_fields: ["workflow", "mcpServers"],
  path_checks: [".claude"],
  permission_checks: ["read", "write"]
})
```

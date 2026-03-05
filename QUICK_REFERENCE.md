# Quick Tool Reference Card

## Tool Call Format

```json
{
  "tool_calls": [
    {
      "id": "call_1",
      "type": "function",
      "function": {
        "name": "TOOL_NAME",
        "arguments": "{\"param\": \"value\"}"
      }
    }
  ]
}
```

## Essential Tool Calls

### Read a file
```json
{"name": "read", "arguments": {"filePath": "/project/src/index.ts"}}
```

### Write a new file
```json
{"name": "write", "arguments": {"filePath": "/project/src/utils.ts", "content": "// code"}}
```

### Edit existing file
```json
{"name": "edit", "arguments": {"filePath": "/project/src/index.ts", "oldString": "old", "newString": "new"}}
```

### Find files by pattern
```json
{"name": "glob", "arguments": {"pattern": "src/**/*.ts"}}
```

### Search in files
```json
{"name": "grep", "arguments": {"pattern": "function\\s+\\w+", "include": "*.ts"}}
```

### Run shell command
```json
{"name": "bash", "arguments": {"command": "npm install", "workdir": "/project", "description": "Install deps"}}
```

### List directory
```json
{"name": "list", "arguments": {"path": "/project/src"}}
```

### Fetch web page
```json
{"name": "webfetch", "arguments": {"url": "https://docs.example.com"}}
```

### Ask question
```json
{"name": "question", "arguments": {"questions": [{"header": "Option", "question": "Which?", "options": [{"label": "A", "description": "Option A"}, {"label": "B", "description": "Option B"}]}]}}
```

### Manage todos
```json
{"name": "todowrite", "arguments": {"todos": [{"content": "Task 1", "status": "in_progress", "priority": "high"}]}}
```

## Common Mistakes to Avoid

| Mistake | Correct |
|---------|---------|
| `cd /path && cmd` | `cmd` with `workdir: "/path"` |
| `cat file.txt` | `read` with `filePath` |
| Relative path | Absolute path `/project/...` |
| Edit without read | Read first, then edit |
| Missing description | Always add description |
| Chain commands with `;` | Use `&&` for dependent |

## Remember

1. **Read before Edit** - Mandatory
2. **Absolute paths** - Always
3. **Use workdir** - Not cd
4. **Parallel when independent** - Faster
5. **Add descriptions** - For clarity

# OpenCode Local Setup with LM Studio

This directory contains essential configuration files to set up OpenCode with a local Qwen model using LM Studio.

## Files Included

| File | Purpose |
|------|---------|
| `opencode.json` | Main configuration for LM Studio + Qwen |
| `SYSTEM_PROMPT.md` | Comprehensive tool usage & AI knowledge |
| `AGENTS.md` | OpenCode project rules |
| `QUICK_REFERENCE.md` | Quick tool call format reference |
| `README.md` | This setup guide |

---

## Quick Setup

### 1. Prerequisites

- **OpenCode installed**: `npm install -g opencode`
- **LM Studio installed**: https://lmstudio.ai
- **Qwen model downloaded**: Search and download in LM Studio

### 2. Configure LM Studio

1. Open LM Studio
2. Search for and download a Qwen model:
   - `Qwen2.5-Coder-14B` (recommended for coding)
   - `Qwen2.5-7B` (faster, less VRAM)
   - `Qwen3-14B` (latest, strong reasoning)
3. Click "Start Server" or use the chat UI
4. **Important**: Set context length to at least 16384 (16K) or higher
5. Server runs at `http://localhost:1234/v1`

### 3. Copy Configuration

```cmd
REM Windows
copy opencode.json %USERPROFILE%\.config\opencode\opencode.json
copy SYSTEM_PROMPT.md %USERPROFILE%\.config\opencode\SYSTEM_PROMPT.md
copy AGENTS.md %USERPROFILE%\.config\opencode\AGENTS.md
```

```bash
# Linux/Mac
cp opencode.json ~/.config/opencode/opencode.json
cp SYSTEM_PROMPT.md ~/.config/opencode/SYSTEM_PROMPT.md
cp AGENTS.md ~/.config/opencode/AGENTS.md
```

### 4. Start OpenCode

```cmd
opencode
```

---

## Configuration Details

### opencode.json (LM Studio)

```json
{
  "provider": {
    "lmstudio": {
      "options": {
        "baseURL": "http://localhost:1234/v1"
      }
    }
  },
  "model": "lmstudio-community/Qwen2.5-14B-Coder-Q5_K_M",
  "permission": {
    "bash": "allow",
    "read": "allow",
    "write": "allow",
    "edit": "allow",
    "glob": "allow",
    "grep": "allow",
    "list": "allow",
    "webfetch": "allow",
    "question": "allow",
    "todowrite": "allow",
    "todoread": "allow",
    "skill": "allow",
    "lsp": "allow"
  }
}
```

### Changing the Model

1. Download new model in LM Studio
2. Update `opencode.json`: Change the `model` field
3. Restart OpenCode

---

## Features Included

### Core Capabilities
- File operations (read, write, edit)
- Code search (grep, glob)
- Shell commands (bash)
- Web fetch (requires internet)
- Task management (todowrite)
- LSP support

### Advanced AI Features
- RAG (Retrieval Augmented Generation)
- Vector database integration
- MCP servers support
- Agent2Agent communication
- Prompt caching
- Spec-driven development

### Deep Learning
- PyTorch, TensorFlow, JAX
- Transformer models
- Training pipelines
- Model deployment
- MLOps tools

---

## Model Recommendations

### For Coding (Best)
- Qwen2.5-Coder-14B (16GB+ VRAM)
- Qwen2.5-Coder-7B (8GB VRAM)

### For General
- Qwen2.5-14B
- Qwen2.5-7B
- Qwen3-14B (latest)

### For Speed
- Qwen2.5-0.5B
- Qwen2.5-1.8B

---

## Web Fetch Issue

**The web fetch limitation:**

1. **With internet**: `webfetch` works if machine has connectivity
2. **Fully offline**: `webfetch` won't work

### To make web fetch work:
1. Ensure machine has internet access
2. Check firewall isn't blocking LM Studio
3. LM Studio must be able to make HTTP requests

---

## Troubleshooting

### Model doesn't respond to tools
1. Ensure system prompt is loaded
2. Check context length (need 16K+)
3. Verify model supports function calling

### Tool calls fail
1. Verify model supports tool calling
2. Qwen 2.5+ models have good support

### Web fetch not working
1. Check connectivity: `ping google.com`
2. Verify no firewall
3. Try: `curl https://example.com`

### Context length issues
1. Set context to 32K or higher in LM Studio
2. Break large tasks into smaller steps

---

## Advanced: Adding MCP Servers

Add MCP servers to `opencode.json`:

```json
{
  "mcp": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed"]
    }
  }
}
```

### Popular MCP Servers

| Server | Purpose |
|--------|---------|
| github | GitHub operations |
| filesystem | File access |
| fetch | Web content |
| brave-search | Web search |
| slack | Slack integration |
| postgres | Database queries |

---

## Advanced: RAG Setup

To add RAG capabilities:

1. Install dependencies:
```bash
pip install langchain langchain-community chromadb sentence-transformers
```

2. Create knowledge base:
```python
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import HuggingFaceEmbeddings

embeddings = HuggingFaceEmbeddings(model_name="BAAI/bge-small-en")
vectorstore = Chroma.from_documents(documents, embeddings)
```

---

## GitHub Operations

The model can perform all Git operations:

```bash
git status
git add .
git commit -m 'feat: add model'
git push
gh pr create
gh issue list
```

---

## For Transfer to Your System

Copy all files in this directory to your local AI system:

1. `%USERPROFILE%\.config\opencode\` (Windows)
2. `~/.config/opencode/` (Linux/Mac)

Required files:
- `opencode.json` - Main config
- `SYSTEM_PROMPT.md` - Tool instructions & AI knowledge
- `AGENTS.md` - Project rules

---

For more help: https://opencode.ai/docs

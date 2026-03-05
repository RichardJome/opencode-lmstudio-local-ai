# OpenCode Local Setup with LM Studio

This directory contains essential configuration files to set up OpenCode with a local Qwen3.5:9b model using LM Studio.

## Files Included

| File | Purpose |
|------|---------|
| `opencode.json` | Main configuration for LM Studio + Qwen3.5:9b + MCPs |
| `SYSTEM_PROMPT.md` | Comprehensive tool usage & AI knowledge |
| `AGENTS.md` | OpenCode project rules |
| `QUICK_REFERENCE.md` | Quick tool call format reference |
| `.opencode/skills/` | Pre-configured skills for DL, RAG, GitHub, Web Search |
| `README.md` | This setup guide |

---

## Quick Setup

### 1. Prerequisites

- **OpenCode installed**: `npm install -g opencode`
- **LM Studio installed**: https://lmstudio.ai
- **Qwen3.5:9b model downloaded**: Search "qwen3.5 9b" in LM Studio

### 2. Configure LM Studio

1. Open LM Studio
2. Search for and download: `Qwen2.5 7B Qwen3.5` or `Qwen3.5 9B`
3. Click "Start Server" or use the chat UI
4. **Important**: Set context length to at least 16384 (16K) or higher
5. Server runs at `http://localhost:1234/v1`

### 3. Set Environment Variables

```cmd
REM Windows - Create or edit %USERPROFILE%\.bashrc or use system settings
set BRAVE_API_KEY=your_brave_api_key
set GITHUB_TOKEN=your_github_token
```

Get Brave API key: https://brave.com/search/api/
Get GitHub token: https://github.com/settings/tokens

### 4. Copy Configuration

```cmd
REM Windows
xcopy /E /I opencode.json %USERPROFILE%\.config\opencode\
xcopy /E /I SYSTEM_PROMPT.md %USERPROFILE%\.config\opencode\
xcopy /E /I AGENTS.md %USERPROFILE%\.config\opencode\
xcopy /E /I .opencode %USERPROFILE%\.config\opencode\
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

## MCP Servers Included

This setup includes these MCP servers pre-configured:

| Server | Purpose | API Key Required |
|--------|---------|------------------|
| **brave-search** | Web search (your Exa alternative!) | Yes - brave.com |
| **filesystem** | File operations | No |
| **github** | GitHub operations | Yes - GitHub token |
| **fetch** | Web content retrieval | No |

### Brave Search Setup (Exa Alternative!)

**Get your free API key:**
1. Go to https://brave.com/search/api/
2. Sign up for account
3. Generate API key
4. Set environment variable:

```cmd
set BRAVE_API_KEY=your_api_key_here
```

**What it provides:**
- `brave_web_search` - General web search
- `brave_local_search` - Local business search  
- `brave_image_search` - Image search
- `brave_video_search` - Video search
- `brave_news_search` - News search

This is the BEST alternative to Exa for local AI!

### GitHub Setup

```cmd
set GITHUB_TOKEN=your_github_token
```

Get token: https://github.com/settings/tokens (repo scope)

---

## Skills Included

Pre-configured skills in `.opencode/skills/`:

| Skill | Purpose |
|-------|---------|
| `deep-learning-setup` | PyTorch, TensorFlow, CUDA setup |
| `rag-setup` | RAG pipeline with LangChain |
| `github-operations` | Issues, PRs, releases |
| `web-search` | Brave Search usage guide |
| `mlops-deployment` | Docker, MLflow, serving |

---

## More MCP Servers You Can Add

### Development
| Server | Purpose | Command |
|--------|---------|---------|
| `gitlab` | GitLab operations | npx @modelcontextprotocol/server-gitlab |
| `sentry` | Error monitoring | npx @modelcontextprotocol/server-sentry |
| `linear` | Project management | npx @modelcontextprotocol/server-linear |
| `notion` | Notion workspace | npx @modelcontextprotocol/server-notion |

### Data & Database
| Server | Purpose | Command |
|--------|---------|---------|
| `postgres` | PostgreSQL queries | npx @modelcontextprotocol/server-postgres |
| `mysql` | MySQL queries | npx @modelcontextprotocol/server-mysql |
| `sqlite` | SQLite queries | npx @modelcontextprotocol/server-sqlite |

### Browser & Automation
| Server | Purpose | Command |
|--------|---------|---------|
| `playwright` | Browser automation | npx @modelcontextprotocol/server-playwright |
| `puppeteer` | Chrome automation | npx @modelcontextprotocol/server-puppeteer |

### AI & ML
| Server | Purpose | Command |
|--------|---------|---------|
| `aws-kb` | AWS knowledge base | npx @modelcontextprotocol/server-aws-kb-retrieval |
| `memory` | Persistent memory | npx @modelcontextprotocol/server-memory |

### Search
| Server | Purpose | Command |
|--------|---------|---------|
| `brave-search` | Brave web search | npx @modelcontextprotocol/server-brave-search |
| `serpapi` | Google search | npx @serpapi/server-serpapi |

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

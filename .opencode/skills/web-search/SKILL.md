---
name: web-search
description: Web search using Brave Search API for research and information
license: MIT
compatibility: opencode
metadata:
  audience: researchers
  workflow: research
---

## What I do

- Perform web searches
- Find latest papers, docs, tutorials
- Search for code examples
- Find news and updates

## When to use me

Use this whenever you need current information from the web:
- Looking up documentation
- Finding recent papers (arXiv, Google Scholar)
- Searching for code examples
- Researching topics

## MCP Tools Available

- `brave_web_search` - General web search
- `brave_local_search` - Local business search
- `brave_image_search` - Image search
- `brave_video_search` - Video search
- `brave_news_search` - News search

## Setup Required

Get Brave API key from: https://brave.com/search/api/

Set environment variable:
```bash
# Windows
set BRAVE_API_KEY=your_api_key

# Linux/Mac
export BRAVE_API_KEY=your_api_key
```

## Usage Examples

```
Search for: "PyTorch 2.0 training best practices 2024"
Search for: "LangChain RAG tutorial"
Search for: "Qwen model fine-tuning"
```

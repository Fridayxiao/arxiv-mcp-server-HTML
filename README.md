# 修改说明

本项目基于 [arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server) 项目修改而来，主要变更包括：

- 使用html作为转换markdown的原本, 而非pdf, 大幅提高了转换速度与表格的识别率, 但和原版使用pdf转换一样无法识别图片, 后续可能继续优化

# changes

base on [arxiv-mcp-server](https://github.com/blazickjp/arxiv-mcp-server), modified:

- Using HTML as the source for markdown conversion instead of PDF, significantly improving conversion speed and table recognition rate. However, like the original PDF conversion, it cannot recognize images. Future optimizations may be implemented.

[![Twitter Follow](https://img.shields.io/twitter/follow/JoeBlazick?style=social)](https://twitter.com/JoeBlazick)
[![smithery badge](https://smithery.ai/badge/arxiv-mcp-server)](https://smithery.ai/server/arxiv-mcp-server)
[![Python Version](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Tests](https://github.com/blazickjp/arxiv-mcp-server/actions/workflows/tests.yml/badge.svg)](https://github.com/blazickjp/arxiv-mcp-server/actions/workflows/tests.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PyPI Downloads](https://img.shields.io/pypi/dm/arxiv-mcp-server.svg)](https://pypi.org/project/arxiv-mcp-server/)
[![PyPI Version](https://img.shields.io/pypi/v/arxiv-mcp-server.svg)](https://pypi.org/project/arxiv-mcp-server/)

# ArXiv MCP Server

> 🔍 Enable AI assistants to search and access arXiv papers through a simple MCP interface.

The ArXiv MCP Server provides a bridge between AI assistants and arXiv's research repository through the Model Context Protocol (MCP). It allows AI models to search for papers and access their content in a programmatic way.

<div align="center">
  
🤝 **[Contribute](https://github.com/blazickjp/arxiv-mcp-server/blob/main/CONTRIBUTING.md)** • 
📝 **[Report Bug](https://github.com/blazickjp/arxiv-mcp-server/issues)**

<a href="https://www.pulsemcp.com/servers/blazickjp-arxiv-mcp-server"><img src="https://www.pulsemcp.com/badge/top-pick/blazickjp-arxiv-mcp-server" width="400" alt="Pulse MCP Badge"></a>
</div>

## ✨ Core Features

- 🔎 **Paper Search**: Query arXiv papers with filters for date ranges and categories
- 📄 **Paper Access**: Download and read paper content
- 📋 **Paper Listing**: View all downloaded papers
- 🗃️ **Local Storage**: Papers are saved locally for faster access
- 📝 **Prompts**: A Set of Research Prompts

## 🚀 Quick Start

### Installing Manually

Install using uv:

1. download dist\arxiv_mcp_server-0.2.11-py3-none-any.whl

2. using uv:

```bash
uv tool install arxiv_mcp_server-0.2.11-py3-none-any.whl
```



### 🔌 MCP Integration

Add this configuration to your MCP client config file, remember to change the path argument to your local path:

```json
{
    "mcpServers": {
        "arxiv-mcp-server": {
            "command": "arxiv-mcp-server-HTML",
            "args": [
                "--storage-path", 
                "/path/to/paper/storage"
            ]
        }
    }
}
```

## 💡 Available Tools

The server provides four main tools:

### 1. Paper Search
Search for papers with optional filters:

```python
result = await call_tool("search_papers", {
    "query": "transformer architecture",
    "max_results": 10,
    "date_from": "2023-01-01",
    "categories": ["cs.AI", "cs.LG"]
})
```

### 2. Paper Download
Download a paper by its arXiv ID:

```python
result = await call_tool("download_paper", {
    "paper_id": "2401.12345"
})
```

### 3. List Papers
View all downloaded papers:

```python
result = await call_tool("list_papers", {})
```

### 4. Read Paper
Access the content of a downloaded paper:

```python
result = await call_tool("read_paper", {
    "paper_id": "2401.12345"
})
```

## 📝 Research Prompts

The server offers specialized prompts to help analyze academic papers:

### Paper Analysis Prompt
A comprehensive workflow for analyzing academic papers that only requires a paper ID:

```python
result = await call_prompt("deep-paper-analysis", {
    "paper_id": "2401.12345"
})
```

This prompt includes:
- Detailed instructions for using available tools (list_papers, download_paper, read_paper, search_papers)
- A systematic workflow for paper analysis
- Comprehensive analysis structure covering:
  - Executive summary
  - Research context
  - Methodology analysis
  - Results evaluation
  - Practical and theoretical implications
  - Future research directions
  - Broader impacts

## ⚙️ Configuration

Configure through environment variables:

| Variable | Purpose | Default |
|----------|---------|---------|
| `ARXIV_STORAGE_PATH` | Paper storage location | ~/.arxiv-mcp-server/papers |

## 🧪 Testing

Run the test suite:

```bash
python -m pytest
```

## 📄 License



Copyright (c) 2025 Your Name
Copyright (c) 2024 Original Author

Released under the MIT License. See the LICENSE file for details.

---

<div align="center">

Made with ❤️ by the Pearl Labs Team

<a href="https://glama.ai/mcp/servers/04dtxi5i5n"><img width="380" height="200" src="https://glama.ai/mcp/servers/04dtxi5i5n/badge" alt="ArXiv Server MCP server" /></a>
</div>

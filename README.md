# PriceScout MCP

AI-powered competitor pricing intelligence system using MCP (Model Context Protocol). Automated web scraping, data extraction, and natural language querying for real-time market analysis.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-green.svg)](https://modelcontextprotocol.io/)

## 🎯 What It Does

PriceScout eliminates manual competitor research by letting you ask natural language questions like:
- "How much does DeepInfra charge for Deepseek v3?"
- "Compare CloudRift AI and Groq's pricing for Llama 3"
- "What's the latest pricing for all providers?"

The system automatically scrapes competitor websites, extracts pricing data, stores it in a SQLite database, and provides intelligent answers through a chatbot interface.

## 🏗️ Architecture

Built using the Model Context Protocol (MCP) with three coordinated agents:

1. **LLM Client (Anthropic Claude)** - Orchestrates the workflow and interprets natural language queries
2. **Custom Scraper Server** - Web scraping using Firecrawl API with metadata tracking
3. **SQLite Database Server** - Persistent storage and retrieval of pricing data
4. **Filesystem Server** - File operations via MCP

## ✨ Features

- 🤖 Natural language query interface
- 🌐 Automated web scraping with Firecrawl
- 💾 SQLite database for historical tracking
- 📊 Structured pricing comparison across providers
- 🔄 Metadata tracking (scrape time, URLs, domains, content format)
- 🛠️ Extensible MCP server architecture
- 📁 File-based content storage with organized structure

## 🚀 Quick Start

### Prerequisites

- **Python 3.10+** - [Download here](https://www.python.org/downloads/)
- **Node.js** - Required for filesystem MCP server - [Download here](https://nodejs.org/)
- **uv** - Fast Python package manager - [Install guide](https://github.com/astral-sh/uv)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/pricescout-mcp.git
cd pricescout-mcp
```

2. **Install uv (if not already installed)**
```bash
# macOS, Linux, WSL
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env

# Verify installation
uv --version
```

3. **Sync dependencies**
```bash
# This will create a virtual environment and install all dependencies
uv sync
```

4. **Set up API keys**

Get your API keys:
- **Anthropic API Key**: [https://console.anthropic.com/](https://console.anthropic.com/)
- **Firecrawl API Key**: [https://www.firecrawl.dev/signin](https://www.firecrawl.dev/signin)

Create a `.env` file in the project root:
```bash
cp .env.example .env
```

Edit `.env` and add your keys:
```env
ANTHROPIC_API_KEY=your_anthropic_api_key_here
FIRECRAWL_API_KEY=your_firecrawl_api_key_here
```

### Running the Project

```bash
# Activate the virtual environment
source .venv/bin/activate

# Run the client
python src/starter_client.py
```

You should see:
```
Connected to 3 server(s)
Available tools: [list of tools from MCP servers]
Data extraction enabled

MCP Chatbot with Data Extraction Started!
Type your queries, 'show data' to view stored data, or 'quit' to exit.

Query:
```

### Example Usage

Once running, try these queries:

1. **Scrape competitor sites**:
```
scrape these sites: {'cloudrift': 'https://www.cloudrift.ai/inference', 'deepinfra': 'https://deepinfra.com/pricing', 'groq': 'https://groq.com/pricing'}
```

2. **Query pricing information**:
```
How much does deepinfra charge for deepseek v3?
```

3. **Compare pricing**:
```
Compare cloudrift ai and deepinfra's costs for deepseek v3
```

4. **View stored data**:
```
show data
```

5. **Exit**:
```
quit
```

## 📁 Project Structure

```
pricescout-mcp/
├── conf/
│   └── server_config.json      # MCP server configuration
├── src/
│   ├── starter_server.py       # Custom MCP scraper server
│   └── starter_client.py       # MCP client orchestrator
├── scraped_content/            # Auto-generated: scraped content
├── scraped_metadata.json       # Auto-generated: scraping metadata
├── test.db                     # Auto-generated: SQLite database
├── pyproject.toml             # Project dependencies
├── .env                       # Your API keys (create from .env.example)
├── .env.example               # Template for environment variables
├── .gitignore                 # Git ignore rules
└── README.md                  # This file
```

## 🎓 Implementation Status

### ✅ Completed
- [x] Project structure with `conf/` and `src/` folders
- [x] Environment setup with `.env` file
- [x] Dependencies managed via `uv`
- [x] Configuration loading from `conf/server_config.json`
- [x] Server initialization with MCP
- [x] Tool listing from MCP servers
- [x] Tool execution with retry mechanism
- [x] Database table setup for pricing data

### 🚧 In Progress
- [ ] Complete `scrape_websites` tool implementation
- [ ] Complete `extract_scraped_info` tool implementation
- [ ] Complete `ChatSession.process_query` (tool use loop)
- [ ] Complete `ChatSession.show_stored_data`
- [ ] Complete `DataExtractor.extract_and_store_data`

## 🔧 Technical Stack

- **Language**: Python 3.10+
- **LLM**: Anthropic Claude (via API)
- **Web Scraping**: Firecrawl API
- **Database**: SQLite (via MCP)
- **Protocol**: Model Context Protocol (MCP)
- **Package Manager**: uv (by Astral)

## 🎯 Supported LLM Providers

- **CloudRift AI**: https://www.cloudrift.ai/inference
- **DeepInfra**: https://deepinfra.com/pricing
- **Fireworks**: https://fireworks.ai/pricing#serverless-pricing
- **Groq**: https://groq.com/pricing

## 📝 Development Notes

### Adding New Providers

To scrape new providers, simply add them to your query:
```python
scrape these sites: {'provider_name': 'https://provider-url.com/pricing'}
```

### Troubleshooting

**Issue**: `command not found: uv`
```bash
# Solution: Source the uv environment
source $HOME/.local/bin/env
```

**Issue**: `ANTHROPIC_API_KEY not found`
```bash
# Solution: Ensure .env file exists and has your API key
cat .env  # Should show your keys
```

**Issue**: MCP server fails to start
```bash
# Solution: Ensure Node.js is installed for filesystem server
node --version
npx --version
```

## 🤝 Contributing

This is a portfolio project demonstrating MCP architecture and AI-powered data extraction. Feel free to fork and build upon it!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License
Copyright (c) 2025 Kinshuk
```

## 🙏 Acknowledgments

- Powered by [Anthropic Claude](https://www.anthropic.com/)
- Web scraping via [Firecrawl](https://www.firecrawl.dev/)
- Uses [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)
- Package management by [uv](https://github.com/astral-sh/uv)

## 🎓 Learning Outcomes

This project demonstrates:
- Building custom MCP servers in Python
- Orchestrating multi-agent AI workflows
- Web scraping with API services (Firecrawl)
- Database integration with SQLite via MCP
- LLM tool use and function calling
- Error handling and retry logic
- Structured data extraction and storage

---

**Built with ❤️ using Model Context Protocol**

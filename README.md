# pricescout-mcp
AI-powered competitor pricing intelligence system using MCP (Model Context Protocol). Automated web scraping, data extraction, and natural language querying for real-time market analysis.

Absolutely! Here's an enhanced README that incorporates your starter content with the description and license:
markdown# PriceScout MCP

AI-powered competitor pricing intelligence system using MCP (Model Context Protocol). Automated web scraping, data extraction, and natural language querying for real-time market analysis.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
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

## ✨ Features

- 🤖 Natural language query interface
- 🌐 Automated web scraping with Firecrawl
- 💾 SQLite database for historical tracking
- 📊 Structured pricing comparison across providers
- 🔄 Metadata tracking (scrape time, URLs, domains, content format)
- 🛠️ Extensible MCP server architecture
- 📁 File-based content storage with organized structure

## 🎯 Supported LLM Providers

- **CloudRift AI**: https://www.cloudrift.ai/inference
- **DeepInfra**: https://deepinfra.com/pricing
- **Fireworks**: https://fireworks.ai/pricing#serverless-pricing
- **Groq**: https://groq.com/pricing

## 🚀 Getting Started

### Prerequisites

- Python 3.11 or higher
- [uv](https://github.com/astral-sh/uv) package manager
- API Keys:
  - [Anthropic API Key](https://console.anthropic.com/)
  - [Firecrawl API Key](https://www.firecrawl.dev/)

### Installation

1. **Clone the repository**
```bash
   git clone https://github.com/yourusername/pricescout-mcp.git
   cd pricescout-mcp
```

2. **Create and activate virtual environment with uv**
```bash
   uv venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. **Sync dependencies**
```bash
   uv sync
```

4. **Set up environment variables**
   
   Create a `.env` file in the project root:
```env
   ANTHROPIC_API_KEY=your_anthropic_api_key_here
   FIRECRAWL_API_KEY=your_firecrawl_api_key_here
```

5. **Configure MCP servers**
   
   Update `server_config.json` to point to your server file location.

### Implementation Steps

1. ✅ Complete the 2 tool implementations in `starter_server.py`:
   - `scrape_websites` - Scrape, persist, and track metadata
   - `extract_scraped_info` - Load metadata and return file contents

2. ✅ Complete all sections marked with `#complete` in `starter_client.py`:
   - List available MCP tools
   - Execute tools with retry logic
   - Persist structured pricing to SQLite
   - Drive tool use via LLM
   - Display stored data from database

3. ✅ Test using methods from the course

### Usage

Run the chatbot and try these example queries:
```python
# Start the chatbot
python starter_client.py
```

**Example Queries:**
- `"How much does cloudrift ai (https://www.cloudrift.ai/inference) charge for deepseek v3?"`
- `"How much does deepinfra (https://deepinfra.com/pricing) charge for deepseek v3"`
- `"Compare cloudrift ai and deepinfra's costs for deepseek v3"`
- `"Scrape all providers and show me the latest pricing"`

## 📁 Project Structure
```
pricescout-mcp/
├── starter_server.py          # Custom MCP server with scraping tools
├── starter_client.py          # MCP client with LLM orchestration
├── server_config.json         # MCP server configuration
├── scraped_content/           # Stored scraped content (auto-generated)
├── scraped_metadata.json      # Scraping metadata (auto-generated)
├── pyproject.toml            # Project dependencies
├── .env                      # API keys (create this)
└── README.md                 # This file
```

## 🎓 Learning Outcomes

This project demonstrates:
- Building custom MCP servers in Python
- Orchestrating multi-agent AI workflows
- Web scraping with API services (Firecrawl)
- Database integration with SQLite via MCP
- LLM tool use and function calling
- Error handling and retry logic
- Structured data extraction and storage

## 🔧 Technical Stack

- **Language**: Python 3.11+
- **LLM**: Anthropic Claude (via MCP)
- **Web Scraping**: Firecrawl API
- **Database**: SQLite (via MCP)
- **Protocol**: Model Context Protocol (MCP)
- **Package Manager**: uv

## 📝 Use Case

Designed for strategy analysts, product managers, and competitive intelligence teams who need to:
- Track competitor pricing changes in real-time
- Make data-driven pricing decisions quickly
- Eliminate manual spreadsheet updates
- Query historical pricing trends
- Automate market research workflows

## 🤝 Contributing

This is an educational project built as part of the Udacity MCP Course. Feel free to fork, experiment, and build upon it!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```
MIT License

Copyright (c) 2025 Kinshuk

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 Acknowledgments

- Powered by [Anthropic Claude](https://www.anthropic.com/)
- Web scraping via [Firecrawl](https://www.firecrawl.dev/)
- Uses [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)
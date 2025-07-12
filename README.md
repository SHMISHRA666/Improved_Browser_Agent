# Browser Agent Planning Agent (S15A)

A sophisticated multi-agent AI system that combines browser automation, document processing, web search, and mathematical computation to solve complex real-world queries through intelligent planning and execution.

## 🎯 Overview

This project implements an **Agentic Query Assistant** that can:
- **Perceive** user queries and determine the best approach
- **Plan** multi-step solutions using graph-based reasoning
- **Execute** tasks using various tools (browser automation, document processing, web search, math)
- **Summarize** results in user-friendly formats

Demo - https://youtu.be/SIwSCQHRAy4


## 🏗️ Architecture

### Core Components

#### 1. **Agent Loop** (`agent/agent_loop3.py`)
- **Perception Module**: Analyzes queries and routes to appropriate handlers
- **Decision Module**: Creates execution plans using graph-based reasoning
- **Execution Engine**: Runs code variants with fallback strategies
- **Summarizer**: Generates final user-facing responses

#### 2. **Browser Automation** (`browserMCP/`)
- **Browser Control**: Full web automation with Playwright
- **Element Interaction**: Click, type, scroll, form filling
- **State Management**: Tracks interactive elements and page states
- **Content Extraction**: Structured data extraction from web pages

#### 3. **Multi-MCP System** (`mcp_servers/`)
- **Math Tools**: Calculations, string processing, Python sandbox
- **Document Processing**: PDF parsing, text extraction, RAG search
- **Web Search**: Information retrieval and content summarization
- **Tool Orchestration**: Unified interface for all external tools

#### 4. **Memory System** (`memory/`)
- **Session Logging**: Tracks all agent interactions
- **Semantic Search**: Retrieves relevant past experiences
- **Context Management**: Maintains conversation history

## 🚀 Features

### 🤖 Intelligent Planning
- **Graph-based reasoning** for complex multi-step tasks
- **Fallback strategies** with multiple code variants
- **Dynamic replanning** based on execution results
- **Context-aware decision making**

### 🌐 Browser Automation
- **Full web interaction** (clicking, typing, scrolling)
- **Form handling** and multi-step workflows
- **State preservation** across page navigation
- **Element identification** and interaction tracking

### 📚 Document Processing
- **PDF parsing** and text extraction
- **Local document search** with semantic indexing
- **RAG (Retrieval-Augmented Generation)** capabilities
- **Multi-format support** (PDF, DOCX, images)

### 🔍 Web Intelligence
- **Web search** and content extraction
- **Real-time information** gathering
- **Structured data** parsing from web pages
- **URL-based content** summarization

### 🧮 Computational Tools
- **Mathematical operations** and calculations
- **String processing** and data manipulation
- **Python code execution** in sandboxed environment
- **Shell command** execution

## 📋 Prerequisites

### System Requirements
- Python 3.11+
- Windows 10/11 (tested on Windows 10.0.26100)
- PowerShell

### Dependencies
```bash
# Core dependencies (see pyproject.toml for complete list)
- mcp[cli]>=1.7.0
- playwright>=1.52.0
- faiss-cpu>=1.10.0
- llama-index>=0.12.31
- spacy>=3.8.4
- fastapi>=0.115.12
- rich>=14.0.0
```

### Environment Setup
1. **Install Python dependencies**:
   ```bash
   uv sync
   ```

2. **Install Playwright browsers**:
   ```bash
   playwright install
   ```

3. **Download spaCy model**:
   ```bash
   python -m spacy download en_core_web_sm
   ```

4. **Set up environment variables**:
   Create a `.env` file with required API keys and configurations.

## 🚀 Quick Start

### 1. Start Browser MCP Server
```bash
uv run browserMCP/browser_mcp_sse.py
```

### 2. Run the Main Application
```bash
uv run main.py
```

### 3. Interactive Usage
```
📝  You: Open https://www.inkers.ai and click the Demo button
📝  You: Find the current chairman of DLF from local documents
📝  You: Calculate the ASCII values of "INDIA" and return sum of exponentials
```

## 📁 Project Structure

```
Browser_Agent_Planning_Agent/
├── agent/                    # Core agent logic
│   ├── agent_loop3.py       # Main execution loop
│   ├── contextManager.py    # Context and state management
│   └── model_manager.py     # LLM integration
├── browserMCP/              # Browser automation
│   ├── browser.py           # Browser control interface
│   ├── browser_mcp_sse.py  # Server-sent events server
│   └── dom/                # DOM processing utilities
├── mcp_servers/            # Tool servers
│   ├── multiMCP.py         # Multi-server dispatcher
│   ├── mcp_server_1.py     # Math and computation tools
│   ├── mcp_server_2.py     # Document processing
│   └── mcp_server_3.py     # Web search tools
├── perception/              # Query analysis
├── decision/               # Planning and reasoning
├── action/                 # Step execution
├── memory/                 # Session and memory management
├── summarization/          # Result summarization
├── prompts/               # LLM prompt templates
└── config/                # Configuration files
```

## 🎯 Example Queries

The system can handle diverse queries including:

### 🌐 Web Automation
- "Open https://www.inkers.ai and click the Contact button"
- "Fill out the subscription form with Name: Rohan, Email: rohan@test.com"
- "Navigate to the pricing page and extract all plan details"

### 📊 Data Analysis
- "Find the main differences between BMW 7 and 5 series online"
- "Compare Mercedes S Class and E Class features"
- "Research current stock prices and market trends"

### 📚 Document Processing
- "Search local documents for information about DLF chairman"
- "Extract key points from the Canvas LMS guide"
- "Find Anmol Singh's apartment purchase details in local files"

### 🧮 Computational Tasks
- "Calculate ASCII values of 'INDIA' and return sum of exponentials"
- "Find the log value of the amount paid for DLF apartment"
- "Process mathematical expressions and return results"

## 🔧 Configuration

### MCP Server Configuration (`config/mcp_server_config.yaml`)
```yaml
mcp_servers:
  - id: math
    script: mcp_server_1.py
    description: "Mathematical and computational tools"
  - id: documents
    script: mcp_server_2.py
    description: "Document processing and search"
  - id: websearch
    script: mcp_server_3.py
    description: "Web search and content extraction"
```

### Agent Profiles (`config/profiles.yaml`)
```yaml
agent:
  name: Cortex-R
  strategy: exploratory
  max_steps: 20
  max_retries: 5
```

## 🛠️ Development

### Debug Mode
```bash
# Browser MCP debug mode
uv run mcp dev browserMCP/browser_mcp_stdio.py

# Main application with verbose logging
uv run main.py --debug
```

### Testing
```bash
# Run basic tests
python -m pytest tests/

# Test specific components
python tests/basic_test.py
python tests/multi_step_test.py
```

## 📈 Performance

- **Multi-step execution** with intelligent fallbacks
- **Parallel tool execution** where possible
- **Memory-efficient** session management
- **Robust error handling** and recovery

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## 🙏 Acknowledgments

- **Browser-use**: Browser automation capabilities based on [browser-use](https://github.com/browser-use/browser-use)
- **MCP Protocol**: Model Context Protocol for tool integration
- **Playwright**: Web automation framework
- **LlamaIndex**: RAG and document processing capabilities

---

**Version**: 0.2.0  
**Python**: >=3.11  
**Status**: Active Development



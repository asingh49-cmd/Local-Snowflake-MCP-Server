# Local-Snowflake-MCP-Server
A local **Model Context Protocol (MCP) server** that enables Claude Desktop to interact with a **Snowflake** database through natural-language SQL. Built in Python, this project demonstrates how modern LLMs can integrate with enterprise data systems using secure, local tooling.

---

## 🔗 Badges

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Snowflake](https://img.shields.io/badge/Snowflake-Data_Cloud-29B5E8.svg)
![Claude](https://img.shields.io/badge/Claude-MCP_Server-8A2BE2.svg)
![Platform](https://img.shields.io/badge/Local-Tooling-orange.svg)

---

##  Overview

This repository contains:

- A **Python MCP server** (`snowflake_mcp_server.py`)  
- A **Claude MCP configuration file** with placeholders (no secrets)  
- **Screenshots and documentation** showing the MCP server running locally  
- Instructions for connecting Claude → MCP Server → Snowflake securely  

This project demonstrates how to use MCP to build custom AI-powered database tooling.

---

## Repository Structure
```
snowflake-mcp-server/
│
├── server/
│ ├── snowflake_mcp_server.py
│ ├── requirements.txt
│
├── config/
│ ├── claude_desktop_config.json # placeholder config
│
├── docs/
│ ├── screenshots/
│
└── README.md
```

---

##  Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/snowflake-mcp-server.git
cd snowflake-mcp-server
```
2. Install Dependencies
```bash
pip install -r server/requirements.txt
```
3. Set Up Environment Variables
```Create a .env file (NOT committed to GitHub):

SNOWFLAKE_USER=your_user
SNOWFLAKE_PASSWORD=your_password
SNOWFLAKE_ACCOUNT=your_account
SNOWFLAKE_WAREHOUSE=your_wh
SNOWFLAKE_DATABASE=your_db
SNOWFLAKE_SCHEMA=your_schema
```
4. Run the MCP Server
```bash
python server/snowflake_mcp_server.py
Expected output:

MCP Snowflake Server started...
Listening for Claude Desktop connections…
```
5. Configure Claude Desktop
```Add this block to your Claude Desktop config:

{
  "mcpServers": {
    "snowflake": {
      "command": "python",
      "args": ["path/to/snowflake_mcp_server.py"]
    }
  }
}
Restart Claude. The tool should appear automatically.
```
Example Claude Prompts
“Run a query to list the tables in my schema.”

“Show the top 10 rows from MY_TABLE.”

“Explain what this SQL query does and suggest optimizations.”

“Create a table called DEMO_TEST with sample values.”
```
🧱 Architecture

Claude Desktop
      │
      ▼
Local MCP Server (Python)
      │
      ▼
Snowflake Database
```
Security Notes (Important!)
This repo does not include:

❌ Snowflake credentials
❌ Hardcoded passwords
❌ Personal account identifiers

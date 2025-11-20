# Pokemon MCP Server Demo

This is a simple MCP (Model Context Protocol) server that connects to the [PokéAPI](https://pokeapi.co/) and exposes tools that an LLM can use to fetch Pokémon data, list popular Pokémon, and build a tournament squad.

It uses the [FastMCP](https://github.com/chain-ml/model-context-protocol) library and `httpx` to fetch live Pokémon info via a standardized protocol that works seamlessly with LLMs and AI agents.

## Features

- Get detailed info about any Pokémon
- Create a powerful tournament squad
- List popular Pokémon picks

## Requirements

- Python 3.8+
- Node.js (for some LLM hosts that require it)
- `httpx`
- `mcp` (Model Context Protocol library)

## Installation

```bash
# Clone the repo
git clone https://github.com/your-username/pokemon-mcp-server
cd pokemon-mcp-server

# Create a virtual environment
python -m venv venv
.\venv\Scripts\Activate  # On Windows
# source venv/bin/activate  # On macOS/Linux

# Install dependencies
pip install httpx "mcp[cli]"
```
## Quick Start Using `uv`

If you prefer using `uv`, follow these steps:

```bash
# Create a new directory for our project
uv init pokemon
cd pokemon

# Create virtual environment and activate it
uv venv
.venv\Scripts\activate  # On Windows
# source .venv/bin/activate  # On macOS/Linux

# Install dependencies
uv add mcp[cli] httpx

# Create our server file
new-item pokemon.py  # On PowerShell
```


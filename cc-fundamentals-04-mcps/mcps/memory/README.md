# Memory MCP

A simple, beginner-friendly memory system for Claude Code.

## Features

- **Remember** - Store memories with optional tags and importance
- **Recall** - Search memories by keyword
- **List** - View all memories with filtering
- **Forget** - Delete memories you no longer need

## Installation

### Option 1: Add to .mcp.json (Project-level)

```json
{
  "mcpServers": {
    "memory": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/memory", "python", "server.py"]
    }
  }
}
```

### Option 2: Add to settings.json (Global)

Add to `~/.claude/settings.json` (Mac/Linux) or `%USERPROFILE%\.claude\settings.json` (Windows):

```json
{
  "mcpServers": {
    "memory": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/memory", "python", "server.py"]
    }
  }
}
```

## Usage

### Store a Memory

```
remember("The API endpoint for users is /api/v1/users", tags="api,endpoint", importance=80)
```

### Search Memories

```
recall("API endpoint")
recall("database", tags="config")
```

### List All Memories

```
memory_list()
memory_list(tags="api,config", limit=10)
```

### Delete a Memory

```
forget("mem_0001", confirm=True)
```

## Storage

Memories are stored in `~/.memory/memories.json`.

## Tips

- Use consistent tags for better organization (e.g., "api", "config", "decision", "solution")
- Higher importance (1-100) means the memory appears first in search results
- Use `recall` to find past solutions before asking Claude to solve the same problem again

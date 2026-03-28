# Journal MCP

A daily work journal for Claude Code - track progress, decisions, and blockers.

## Why Journal?

- **Track decisions** - Remember why you made choices
- **Log blockers** - See patterns in what slows you down
- **Celebrate wins** - Keep morale high by recording achievements
- **Capture learnings** - Build a personal knowledge base
- **Review progress** - See how much you've accomplished

## Entry Types

| Type | Use For |
|------|---------|
| `work` | Tasks completed, features built |
| `decision` | Choices made and why |
| `blocker` | Issues blocking progress |
| `note` | General observations |
| `win` | Achievements and successes |
| `learning` | New things learned |

## Tools

| Tool | Description |
|------|-------------|
| `log` | Log a new entry |
| `today` | View today's entries |
| `review` | Review past entries |
| `summary` | Generate work summary |

## Installation

Add to your `.mcp.json`:

```json
{
  "mcpServers": {
    "journal": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/journal", "python", "server.py"]
    }
  }
}
```

## Usage

### Log Entries

```
log("Finished the authentication module", entry_type="work", project="my-app")
log("Decided to use SQLite instead of PostgreSQL for simplicity", entry_type="decision")
log("API rate limiting causing test failures", entry_type="blocker")
log("Learned about MCP prompts capability", entry_type="learning")
log("Got the demo working!", entry_type="win")
```

### View Today

```
today()
today(entry_type="blocker")  # Filter by type
```

### Review Past Days

```
review(date="2024-01-15")
review(days=7)  # Last 7 days
review(days=7, entry_type="decision")  # Decisions in last week
```

### Get Summary

```
summary()  # Last 7 days
summary(days=30)  # Last month
```

## Storage

Entries are stored by date in `~/.journal/`:
- `2024-01-15.json`
- `2024-01-16.json`
- etc.

## Tips

- Log throughout the day, not just at the end
- Be specific about blockers - it helps find patterns
- Review your learnings weekly
- Use project names consistently for better summaries
- Start each session with `today()` to see where you left off

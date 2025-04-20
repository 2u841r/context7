# Context7 MCP - Up-to-date Docs For Any Cursor Prompt

## ❌ Without Context7

LLMs rely on outdated or generic information about the libraries you use. You get:

- ❌ Code examples are outdated and based on year-old training data
- ❌ Hallucinated APIs don't even exist
- ❌ Generic answers for old package versions

## ✅ With Context7

Context7 MCP pulls up-to-date, version-specific documentation and code examples straight from the source — and places them directly into your prompt.

Add `use context7` to your question in Cursor:

```txt
How do I use the new Next.js `after` function? use context7
```

```txt
How do I invalidate a query in React Query? use context7
```

```txt
How do I protect a route with NextAuth? use context7
```

Context7 fetches up-to-date documentation and working code examples right into your LLM's context.

- 1️⃣ Ask your question naturally
- 2️⃣ Tell the LLM to `use context7`
- 3️⃣ Get working code answers

No tab-switching, no hallucinated APIs that don't exist, no outdated code generations.

## 🛠️ Getting Started

### Requirements

- Node.js >= v18.0.0
- Cursor, Windsurf, Claude Desktop or another MCP Client

> **Note on Runtimes:** While `npx` (Node.js) is the recommended default for broader compatibility, an alternative using `deno` is provided below for users prioritizing enhanced security. Deno allows explicit control over script permissions (like network access) via flags such as `--allow-net`, reducing potential risks. See [#7](https://github.com/upstash/context7-mcp/issues/7) for the discussion.

### Install in Cursor

Go to: `Settings` -> `Cursor Settings` -> `MCP` -> `Add new global MCP server`

Pasting the following configuration into your Cursor `~/.cursor/mcp.json` file is the recommended approach. See [Cursor MCP docs](https://docs.cursor.com/context/model-context-protocol) for more info.

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

<details>
<summary>Alternative: Use Deno (Enhanced Security)</summary>

```json
{
  "mcpServers": {
    "context7": {
      "command": "deno",
      "args": ["run", "--allow-net", "npm:@upstash/context7-mcp"]
    }
  }
}
```

</details>

### Install in Windsurf

Add this to your Windsurf MCP config file. See [Windsurf MCP docs](https://docs.windsurf.com/windsurf/mcp) for more info.

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

<details>
<summary>Alternative: Use Deno (Enhanced Security)</summary>

```json
{
  "mcpServers": {
    "context7": {
      "command": "deno",
      "args": ["run", "--allow-net", "npm:@upstash/context7-mcp"]
    }
  }
}
```

</details>

### Install in VSCode

Add this to your VSCode MCP config file. See [VSCode MCP docs](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) for more info.

```json
{
  "servers": {
    "Context7": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

<details>
<summary>Alternative: Use Deno (Enhanced Security)</summary>

```json
{
  "servers": {
    "Context7": {
      "type": "stdio",
      "command": "deno",
      "args": ["run", "--allow-net", "npm:@upstash/context7-mcp"]
    }
  }
}
```

</details>

### Available Tools

- `resolve-library-id`: Resolves a general library name into a Context7-compatible library ID.
  - `libraryName` (optional): Search and rerank results
- `get-library-docs`: Fetches documentation for a library using a Context7-compatible library ID.
  - `context7CompatibleLibraryID` (required)
  - `topic` (optional): Focus the docs on a specific topic (e.g., "routing", "hooks")
  - `tokens` (optional, default 5000): Max number of tokens to return

## Development

Clone the project and install dependencies:

```bash
bun i
```

Build:

```bash
bun run build
```

### Local Configuration Example

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["tsx", "/path/to/folder/context7-mcp/src/index.ts"]
    }
  }
}
```

### Testing with MCP Inspector

```bash
npx -y @modelcontextprotocol/inspector npx @upstash/context7-mcp@latest
```

## Troubleshooting

### ERR_MODULE_NOT_FOUND

If you see this error, try using `bunx` instead of `npx`.

```json
{
  "mcpServers": {
    "context7": {
      "command": "bunx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

This often resolves module resolution issues, especially in environments where `npx` does not properly install or resolve packages.

## License

MIT

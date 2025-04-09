# Context7 MCP Server

In this repository, we provide an MCP Server for [Context7](https://context7.com), which offers access to high-quality documentation for popular libraries.

This lets you use Cursor, Windsurf, Claude Desktop, or any MCP Client, to use natural language to search and access documentation for libraries, e.g.:

- "What are the main features of React hooks?"
- "How do I implement authentication with Next.js?"
- "Rate limiting with Redis"
- "Get examples of using React Query"

## Usage

### Requirements

- Node.js >= v18.0.0
- Cursor, Windsurf, Claude Desktop or another MCP Client

### How to use locally

#### Installing for Cursor

Add this command to the MCP list in Cursor. For more info, check the [Cursor MCP](https://docs.cursor.com/context/model-context-protocol) docs.

```bash
npx -y @upstash/context7-mcp
```

#### Installing for Windsurf

Add this to your Windsurf MCP config file. For more info, check the [Windsurf MCP](https://docs.windsurf.com/windsurf/mcp) docs.

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp"]
    }
  }
}
```

### Tools

- `list-available-docs`: Lists all available documentation libraries from Context7
  - `libraryName`: Optional library name to search for and rerank results based on
- `get-library-documentation`: Retrieves documentation for a specific library with options for:
  - `libraryName`: Name of the library to retrieve docs for
  - `topic`: Specific topic within the library
  - `tokens`: Maximum tokens to retrieve (default: 5000)

## Development

Clone the project and run:

```bash
npm install
```

You can use the following commands to format and lint the code:

```bash
npm run format
npm run lint
```

### Building

```bash
npm run build
```

### Local Configuration

```json
{
  "mcpServers": {
    "context7": {
      "command": "node",
      "args": ["/ABSOLUTE/PATH/TO/PARENT/FOLDER/context7-mcp/build/index.js"]
    }
  }
}
```

### Testing with MCP Inspector

You can also use the MCP Inspector to test the tools by following the MCP documentation for setting up the inspector.

```bash
npx -y @modelcontextprotocol/inspector npx @upstash/context7-mcp
```

## License

MIT

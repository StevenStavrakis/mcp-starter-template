# MCP Server Starter
[![smithery badge](https://smithery.ai/badge/@StevenStavrakis/mcp-starter-template)](https://smithery.ai/server/@StevenStavrakis/mcp-starter-template)

A production-ready starter template for building Model Context Protocol (MCP) servers with TypeScript.

## 🚀 Quick Start

1. Clone the repository
2. Install dependencies:
   ```bash
   bun install
   ```

## ✨ Key Features

- Bun for fast testing and development
- Biome for linting and formatting
- Automated version management with standard-version
- Clean, maintainable project structure

## 📂 Project Structure

```
mcp-starter/
├── src/
│   ├── tools/          # MCP tools implementation
│   ├── utils/          # Shared utilities
│   ├── main.ts         # Server entry point
│   └── types.ts        # Shared type definitions
├── tests/              # Test files
├── biome.json          # Linting configuration
├── tsconfig.json       # TypeScript configuration
└── package.json        # Project dependencies
```

## ⚙️ Configuration

### Creating New Tools

The project includes a script to help create new MCP tools:

```bash
bun run scripts/create-tool.ts <tool-name>
```

This will:
1. Create a new tool directory under `src/tools/<tool-name>`
2. Generate the basic tool structure including:
   - index.ts (main implementation)
   - schema.ts (JSON schema for tool parameters)
   - test.ts (test file)
3. Update the tools index file to export the new tool

Example:
```bash
bun run scripts/create-tool.ts weather
```

## 🛠️ Development

- **Run tests**: `bun test`
- **Format code**: `bun run format`
- **Lint code**: `bun run lint`
- **Build project**: `bun run build`

To add your development MCP server to Claude Desktop:

1. Build the project:
   ```bash
   bun run build
   ```
2. Add to your Claude Desktop config:
   ```json
   // You only need the argument if you need to pass arguments to your server
   {
     "mcpServers": {
       "your-server-name": {
         "command": "node",
         "args": ["/path/to/your/project/dist/main.js", "some_argument"]
       }
     }
   }
   ```

## 📜 Version Management

This project uses [standard-version](https://github.com/conventional-changelog/standard-version) for automated version management. Run `bun run release` to create a new version.

### Commit Message Format
- `feat`: New feature (bumps minor version)
- `fix`: Bug fix (bumps patch version)
- `BREAKING CHANGE`: Breaking change (bumps major version)

## 📦 Publishing to npm

1. Ensure you're logged in to npm:
   ```bash
   npm login
   ```
2. Build the project:
   ```bash
   bun run build
   ```
3. Publish the package:
   ```bash
   npm publish
   ```
Remember to update the version number using `bun run release` before publishing new versions.

## Installing from npm (after publishing)

Add to your Claude Desktop config:
```json
// You only need the argument if you need to pass arguments to your server
{
  "mcpServers": {
    "your-server-name": {
      "command": "npx",
      "args": ["-y", "your-package-name", "some_argument"]
    }
  }
}

</readme>
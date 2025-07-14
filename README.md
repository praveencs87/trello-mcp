# Trello MCP Server

[![smithery badge](https://smithery.ai/badge/@praveencs87/trello-mcp)](https://smithery.ai/server/@praveencs87/trello-mcp)

A Model Context Protocol (MCP) server that enables AI assistants, editors, and automation tools to interact with your Trello boards, lists, cards, and more. This server provides a standardized interface for managing Trello workflows through any MCP-compatible client.

## 🚀 Quick Start

### 1. Clone and Setup
```bash
git clone <repo-url>
cd trello-mcp-server
npm install
npm run build
```

### 2. Get Trello API Credentials
1. Go to [Trello Developer Portal](https://trello.com/app-key)
2. Copy your **API Key**
3. Generate a **Token** (click "Token" link on the same page)
4. Create a `.env` file:
   ```bash
   cp .env.example .env
   ```
5. Edit `.env` and replace the placeholder values with your actual credentials:
   ```env
   TRELLO_API_KEY=your_actual_api_key_here
   TRELLO_API_TOKEN=your_actual_token_here
   ```

### 3. Test the Server
```bash
node build/index.js
```

## 🛠️ Using with Different Tools

### Cursor IDE

#### Method 1: Built-in MCP Support
1. **Start the MCP server** in a terminal:
   ```bash
   node build/index.js
   ```

2. **Configure Cursor** (if needed):
   - Open Cursor Settings (`Ctrl+,`)
   - Search for "MCP" or "Model Context Protocol"
   - Add server configuration if required

3. **Use MCP tools directly** in Cursor:
   - Ask: "Get all my Trello boards"
   - Ask: "Create a card in my 'To Do' list with title 'Fix login bug'"
   - Ask: "Move card 'Update docs' from 'In Progress' to 'Done'"

#### Method 2: Command Palette
1. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
2. Type "MCP" and look for MCP-related commands
3. Select "Connect to MCP Server" or similar
4. Enter server details:
   - **Command**: `node`
   - **Arguments**: `/path/to/trello-mcp-server/build/index.js`
   - **Environment**: Set `TRELLO_API_KEY` and `TRELLO_API_TOKEN`

### Claude AI Assistant

#### Method 1: Direct Integration
1. **Start the server**:
   ```bash
   node build/index.js
   ```

2. **In Claude**, you can now ask:
   - "Show me all my Trello boards"
   - "Create a new card in my project board"
   - "Move the card 'Design review' to the 'Done' list"
   - "Add a comment to card 'Bug fix' saying 'This looks good'"

#### Method 2: MCP Configuration
1. In Claude's settings, look for MCP configuration
2. Add the server path: `/path/to/trello-mcp-server/build/index.js`
3. Set environment variables for Trello credentials

### Installing via Smithery

To install trello-mcp for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@praveencs87/trello-mcp):

```bash
npx -y @smithery/cli install @praveencs87/trello-mcp --client claude
```

### VS Code

#### Method 1: Terminal Integration
1. **Open VS Code** and the project folder
2. **Open integrated terminal** (`Ctrl+`` `)
3. **Start the server**:
   ```bash
   node build/index.js
   ```
4. **Use MCP tools** through VS Code's AI features or extensions

#### Method 2: MCP Extension
1. Install an MCP client extension for VS Code
2. Configure the extension to point to your Trello MCP server
3. Use the extension's interface to interact with Trello

### Other MCP-Compatible Tools

#### General Configuration
For any MCP-compatible tool, you'll typically need:

1. **Server Path**: `/path/to/trello-mcp-server/build/index.js`
2. **Command**: `node`
3. **Environment Variables**:
   - `TRELLO_API_KEY=your_key`
   - `TRELLO_API_TOKEN=your_token`

#### Examples for Popular Tools:
- **Continue**: Add to `~/.continue/config.json`
- **Sweep**: Configure in sweep settings
- **Custom Scripts**: Use the MCP protocol directly

## 📋 Available Commands

### Get Information
- **"Get all my Trello boards"** - Lists all your boards
- **"Show lists in board 'Project X'"** - Lists all lists in a specific board
- **"Get cards in list 'To Do'"** - Shows all cards in a list

### Create Items
- **"Create a card in 'To Do' list with title 'New task'"** - Creates a new card
- **"Create a red label called 'Urgent' on my project board"** - Creates a new label

### Manage Cards
- **"Move card 'Task name' from 'In Progress' to 'Done'"** - Moves a card between lists
- **"Archive card 'Old task'"** - Archives a card
- **"Add comment to card 'Task name' saying 'This is complete'"** - Adds a comment

### Batch Operations
- **"Move all cards from 'In Progress' to 'Done'"** - Moves multiple cards
- **"Create 3 cards in 'To Do': 'Task 1', 'Task 2', 'Task 3'"** - Creates multiple cards

## 🔧 Advanced Configuration

### Environment Variables
Copy the sample environment file and fill in your credentials:
```bash
cp .env.example .env
```

Then edit `.env` with your actual values:
```env
TRELLO_API_KEY=your_api_key
TRELLO_API_TOKEN=your_token
PORT=8000  # Optional: for HTTP transport
DEBUG=true  # Optional: enable debug logging
```

### MCP Protocol Details
The server supports:
- **Stdio transport** (default)
- **HTTP transport** (if PORT is set)
- **JSON-RPC 2.0** protocol

### Available Resources
- `trello://boards` - All user boards
- `trello://boards/{boardId}/lists` - Lists in a board
- `trello://lists/{listId}/cards` - Cards in a list

### Available Tools
- `get-boards` - Retrieve all boards
- `get-lists` - Get lists in a board
- `create-card` - Create a new card
- `move-card` - Move a card between lists
- `add-comment` - Add comment to a card
- `create-label` - Create a new label
- `archive-card` - Archive a card
- And many more...

## 🐛 Troubleshooting

### Common Issues

1. **"Server not found"**
   - Ensure the server is running: `node build/index.js`
   - Check the path in your MCP configuration

2. **"Authentication failed"**
   - Verify your Trello API credentials in `.env`
   - Ensure the token has proper permissions

3. **"Tool not available"**
   - Check if the server is properly initialized
   - Verify the MCP protocol version compatibility

### Debug Mode
Run with debug logging:
```bash
DEBUG=* node build/index.js
```

### Test the Server
Test the MCP server directly:
```bash
echo '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"test","version":"1.0.0"}}}' | node build/index.js
```

## 📚 Examples

### Basic Workflow
1. **Start server**: `node build/index.js`
2. **Ask your AI tool**: "Show me all my Trello boards"
3. **Create a card**: "Create a card in 'To Do' list with title 'Review pull request'"
4. **Move the card**: "Move card 'Review pull request' to 'In Progress'"
5. **Add comment**: "Add comment to 'Review pull request' saying 'Starting review now'"

### Project Management
- **Daily standup**: "Show me all cards in 'In Progress' list"
- **Sprint planning**: "Create cards in 'Backlog': 'Feature A', 'Feature B', 'Bug fix'"
- **Code review**: "Move card 'PR #123' from 'Review' to 'Done'"

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with your Trello account
5. Submit a pull request

## 📄 License

ISC License - see LICENSE file for details

## 🔗 Links

- [MCP Protocol Documentation](https://modelcontextprotocol.io/)
- [Trello API Documentation](https://developer.atlassian.com/cloud/trello/)
- [Cursor MCP Integration](https://cursor.sh/docs/mcp)
- [Claude MCP Support](https://docs.anthropic.com/en/docs/model-context-protocol-mcp)


## 👨‍💻 Author

Praveen CS

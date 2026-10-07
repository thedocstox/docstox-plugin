# Installing DocStoX MCP

DocStoX is a hosted remote MCP server. There is nothing to clone, build or run locally.

1. Add the server to your MCP settings (for Cline, `cline_mcp_settings.json`):

   ```json
   {
     "mcpServers": {
       "docstox": {
         "type": "streamableHttp",
         "url": "https://mcp.docstox.com/mcp"
       }
     }
   }
   ```

2. On first connect, a browser opens so you can sign in to docstox.com with Google or email and allow read-only access. A free account includes 50 tool calls a day.
3. If your client cannot open a browser sign-in, create an API key at https://docstox.com/mcp/keys and add it as a header instead:

   ```json
   "headers": { "Authorization": "Bearer dox-YOUR_KEY" }
   ```

4. Check the connection by calling the `read_me` tool. Every DocStoX tool is read-only.

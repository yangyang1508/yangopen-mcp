# Installing the YangOpen MCP server (for AI agents)

YangOpen is a hosted remote MCP server. There is nothing to clone, build or run locally, and no API key to set.

## Steps

1. Add a remote server named `yangopen` with the URL `https://yangopen.com/mcp` and the Streamable HTTP transport.

   Cline (`cline_mcp_settings.json`):

   ```json
   {
     "mcpServers": {
       "yangopen": {
         "type": "streamableHttp",
         "url": "https://yangopen.com/mcp",
         "disabled": false
       }
     }
   }
   ```

   Other clients that read `mcpServers`: use `{ "url": "https://yangopen.com/mcp" }`.

2. Check the connection: the server should list 27 tools (`list_voices`, `text_to_speech`, `remove_background`, `merge_pdf`, ...). Listing tools needs no sign-in.

3. Sign-in happens at the first tool call. The server answers `401` with a `WWW-Authenticate` header that points to its OAuth metadata. The client opens a browser page where the user signs in to (or creates) a free YangOpen account. Ask the user to finish that page; do not try to fill it in for them.

4. Try a free tool to confirm, for example `number_to_words` with `{"number": 1250000}` or `list_voices`.

## Notes

- Free voices, text tools and file tools need no credit within a daily allowance. Plus voices and extra photo runs use prepaid credit; say the cost before a long job (`get_balance` shows the balance).
- Photos and files cannot be passed inline: call `get_upload_link`, give the user the link, then call the tool with the returned `file_id` (or pass a public `image_url`).
- Docs: https://yangopen.com/guides/claude-mcp-connector/

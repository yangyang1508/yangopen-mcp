<img src="logo.png" alt="YangOpen" width="96" height="96">

# YangOpen MCP server

[![YangOpen MCP connector](https://glama.ai/mcp/connectors/com.yangopen/mcp/badges/score.svg)](https://glama.ai/mcp/connectors/com.yangopen/mcp)

A hosted remote MCP server for Claude and other AI assistants. Vietnamese-first text to speech, photo tools, PDF and picture tools, QR codes, audio to text and a few Vietnamese office helpers.

- **Endpoint:** `https://yangopen.com/mcp` (Streamable HTTP)
- **Sign-in:** OAuth 2.1 with dynamic client registration. `initialize` and `tools/list` answer without a token; the first tool call asks you to sign in to a YangOpen account.
- **Official MCP Registry:** `com.yangopen/mcp`
- **Docs:** https://yangopen.com/guides/claude-mcp-connector/ (Tiếng Việt: https://yangopen.com/vi/guides/claude-mcp-connector/)

This repository holds the documentation and directory manifests only. The server is a hosted service run by YangOpen; its source code is not public.

## Connect

**Claude (web, desktop, mobile):** Settings → Connectors → Add custom connector → URL `https://yangopen.com/mcp`. The first time Claude uses a tool, press Connect in the chat and sign in.

**Claude Code:**

```bash
claude mcp add --transport http --scope user yangopen https://yangopen.com/mcp
```

**Cline, Cursor and other clients:** add a remote (Streamable HTTP) server with the URL `https://yangopen.com/mcp`. The client needs OAuth support. Step-by-step notes for AI agents: [llms-install.md](llms-install.md).

## Tools (27)

| Area | Tools |
|---|---|
| Text to speech | `list_voices`, `text_to_speech` (free voices: Vietnamese, English, Chinese, Japanese, Korean, Thai, French, Spanish), `text_to_speech_plus` (about 2,600 Plus voices, Northern, Central and Southern Vietnamese accents) |
| Photos | `remove_background`, `sharpen_image`, `colorize_photo`, `scan_document` |
| PDF | `merge_pdf`, `extract_pdf_pages`, `delete_pdf_pages`, `rotate_pdf`, `compress_pdf`, `pdf_to_images`, `pdf_to_markdown` |
| Pictures | `images_to_pdf`, `compress_image`, `resize_image`, `convert_image` (HEIC to JPG and more) |
| QR and audio | `read_qr_code`, `make_qr_code`, `audio_to_text` |
| Text and numbers | `convert_vietnamese_font` (TCVN3/VNI to Unicode), `number_to_words`, `convert_currency`, `convert_time` |
| Account and files | `get_balance`, `get_upload_link` |

Files go in through `get_upload_link` (a one-time upload page) or a public image URL. Results come back as links that work for 24 hours.

## Price

Free voices, the text tools and the file tools are free within a daily allowance. Photo tools have 5 free runs a day each. Plus voices and extra photo runs use prepaid credit; there is no subscription. Current prices: https://yangopen.com/pricing/

## Example requests

- "Read this paragraph aloud in a Southern Vietnamese voice and give me the MP3."
- "Remove the background from this product photo."
- "Merge these three PDFs and compress the result."

## Privacy and support

- Privacy: https://yangopen.com/privacy/
- Terms: https://yangopen.com/terms/
- Contact: contact@yangopen.com

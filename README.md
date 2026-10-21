# Memex for Grok Build

This Grok Build plugin connects Grok to the hosted, OAuth-authenticated Memex
MCP server. It gives Grok access to the user's saved knowledge and to Memex
actions for search, URL indexing and retrieval, transcripts, HTML, and PDFs.

## Install

```sh
grok plugin install WorldBrain/memex-grok --trust
grok plugin enable memex-grok
```

Start a new Grok session, open `/mcps`, select `memex`, and authenticate with
OAuth. Grok stores the MCP OAuth credentials in its normal credential store.

The plugin uses only the hosted Memex MCP. No local companion process or Node.js installation is required.

# Memex for Grok Build

This Grok Build plugin connects Grok to the hosted, OAuth-authenticated Memex
MCP server. It gives Grok access to the user's saved knowledge and to Memex
actions for search, URL indexing and retrieval, transcripts, HTML, PDFs, and
handoffs.

## Install

```sh
grok plugin install WorldBrain/memex-grok --trust
grok plugin enable memex-grok
```

Start a new Grok session, open `/mcps`, select `memex`, and authenticate with
OAuth. Grok stores the MCP OAuth credentials in its normal credential store.

The plugin also bundles a local Realtime MCP and background handoff monitor.
The first authenticated Memex operation automatically exchanges a short-lived,
single-use pairing ticket through the existing OAuth connection; it does not
require a second login. The saved local session reconnects on later Grok
launches. `/memex:enable-realtime-handoffs` remains available for explicit
repair.

Memex cloud handoff runs are selected from the Memex onboarding or AI runtime
settings. They use the authenticated Grok provider connection and attach the
same hosted Memex MCP to each run.

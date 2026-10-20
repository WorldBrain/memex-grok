---
name: enable-realtime-handoffs
description: Pair the Memex Grok plugin's local MCP with Supabase Realtime so approved Memex handoffs arrive live. The normal Memex skill performs this automatically; use this skill for explicit setup or repair.
---

# Enable Realtime handoffs

1. Call the plugin-local `realtime_handoff_status` without exposing session details.
2. If it reports an existing pairing, preserve that pairing and connection.
3. Otherwise call the hosted Memex tool `create_realtime_handoff_connection_ticket` with `client: "memex_grok_plugin"`.
4. Immediately call the plugin-local `connect_realtime_handoffs` with the returned `ticket` and `exchangeUrl`. Never print or summarize the single-use ticket.
5. Report the resulting connection state and number of pending handoffs found during durable-queue catch-up.

After pairing, the local MCP refreshes its Supabase session and reconnects automatically while Grok keeps the MCP process running. The bundled monitor forwards live approved handoffs into Grok. Realtime is a wake-up signal; `public.handoffs` remains the durable source of truth.

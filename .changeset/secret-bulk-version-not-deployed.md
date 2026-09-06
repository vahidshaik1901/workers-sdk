---
"wrangler": patch
---

Explain how to resolve a `secret bulk` failure when the latest version isn't deployed

`wrangler secret put` already translates the "latest version isn't currently deployed" API
error into guidance: use `wrangler versions secret put`, or deploy the latest version
first. `wrangler secret bulk` edits the same secrets on the same Worker and fails the same
way, but had no such handling, so it printed the raw Cloudflare API error instead.

It now gives the same explanation, pointing at `wrangler versions secret bulk`. Both
commands build the message from one helper so they cannot drift apart again.

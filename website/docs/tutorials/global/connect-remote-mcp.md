# Connect a remote MCP server to the Dashboard

## Overview

The Dashboard can add a remote MCP server over streamable HTTP, discover that
server's tools, and run them from chat. The steps below are the same for any
streamable-http server. [Parallel Search MCP](https://docs.parallel.ai/integrations/mcp/search-mcp)
is the worked example because anonymous use does not need an API key.

Saving a server here does not change routing defaults, presets, or the built-in
catalog. Nothing in a default configuration enables this server.

## Data notice

Search queries and fetched URLs are sent to the remote service. For Parallel
Search MCP, that service is Parallel. Read the
[terms of service](https://parallel.ai/terms-of-service) before you enable it.

Anonymous calls use [Fast mode](https://docs.parallel.ai/search/modes) and are
meant for exploration and light use. The Search MCP docs cap excerpts at about
25,000 characters per tool call. For a higher limit, create a Parallel account
and send the API key as an `Authorization` header. Leave the header empty for
anonymous use.

This server is optional. The Dashboard already has a built-in Web Search tool.
You can keep using that tool and leave this server disconnected.

## Add the server

1. Open the Dashboard and go to **Integrations**, then **MCP Servers**.
2. Choose **Add MCP Server**.
3. Set **Name** to a label you will recognize, such as `Parallel Search`.
4. Set **Transport Protocol** to **Streamable HTTP**. Transport cannot be
   changed after you save the server.
5. Set **URL** to `https://search.parallel.ai/mcp`. For a different
   streamable-http server, use that server's URL instead.
6. Leave **Request headers** empty for anonymous Parallel Search. If the server
   requires a credential, add it here. Do not commit that header value.
7. Leave **Enabled** checked.
8. Choose **Test Connection**, then **Save**.
9. Choose **Refresh MCP data**. Under **Available Tools**, filter **Source** to
   **MCP servers**. `web_search` and `web_fetch` should appear for this URL.

`web_search` searches the web. `web_fetch` reads a page URL as markdown. Use
`web_search` first, then `web_fetch` on a result URL.

## Run a tool

Open the Dashboard chat and ask for a current web result, for example a recent
change on a public documentation page. When the model calls `web_search` or
`web_fetch`, the chat tool loop runs the discovered MCP tool and shows the
tool card.

To confirm discovery without relying on the model, open the tool in
**Available Tools**. The detail view shows the tool name, source server, and
parameters.

Another streamable-http server uses this same dialog. Only the URL, headers,
and tool names change.

# rosegold for Hermes Agent

Get offers and rewards matched to what you buy on Amazon, with a single prompt to your AI assistant.

This is rosegold's plugin in the portable Agent Plugins layout. Its `mcp.json` names rosegold's MCP server,
`https://rosegold.app/mcp/v1`, whose three tools Hermes finds when it connects.

## Sign in once

A plugin's `mcp.json` can't say that a server signs in with OAuth, so after installing, add the server once with
OAuth turned on:

```bash
hermes mcp add rosegold --url https://rosegold.app/mcp/v1 --auth oauth --connect-timeout 300
```

In the browser that opens, sign in with your email and the code rosegold sends, which makes you an account if you
don't have one, then choose **Agree and allow**. This entry replaces the package's entry of the same name, and stays
until `hermes mcp remove rosegold`.

## What to ask

- "Share my recent Amazon purchases with rosegold." This needs a Gmail tool in Hermes.
- "What creator codes are available for Gymshark, check the rosegold connector."
- "What does rosegold say I've spent on Amazon?"

## What it sends where

- Every tool call goes to rosegold's server at rosegold.app. The package runs no code of its own and stores no
  credential: Hermes keeps the sign-in's token.
- To share orders, Hermes finds your Amazon order confirmations with its own Gmail tool and sends rosegold each
  email's id and date, and each order's number, items and prices; never names, addresses or payment details. We do
  not connect to your Gmail account.
- Looking up brings the offers rosegold has for you, and your spending by month and kind of thing, into the chat.
  rosegold keeps any brand you name.
- Under Hermes's default trust, rosegold's tools run without asking first.

[Privacy policy](https://rosegold.app/privacy). Version 1.0.0.

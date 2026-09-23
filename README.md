<div align="center">

<img src="assets/cover.png" alt="Telegram through HeyMetra's MCP server" width="100%">

# Telegram &times; HeyMetra

**Link a Telegram chat to your workspace.**

An answer nobody reads is not an answer. Have it delivered to Telegram, where the team already is.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-telegram-1f6feb)](https://heymetra.com/connectors/telegram/)

```
https://mcp.heymetra.com/mcp
```

</div>

---

## Connect Telegram

**1. Create a bot with @BotFather**

In Telegram, open a chat with @BotFather and send /newbot. It asks for a display name and then a username, which must end in 'bot'. It replies with the token.

> The bot is yours, not HeyMetra's. It lives in your Telegram account, you can rename or delete it at any time, and deleting it is how you cut this connection off at the source.

**2. Copy the token and paste it into HeyMetra**

One line: digits, a colon, then letters and digits. Choose Telegram on the Connections screen and paste it. Saving checks it against Telegram immediately and shows you which bot answered.

> Anyone holding this token can post as your bot, so treat it like a password. If it leaks, /revoke in BotFather issues a new one and kills the old — you then paste the new one here.

**3. Open the link HeyMetra gives you and press Start**

The token proves which BOT will send; it does not say which CHAT to send to. HeyMetra hands you a one-time link to your own bot. Open it, press Start, and the chat it opens is the one messages arrive in.

> This step cannot be skipped and cannot be done from our side: Telegram does not let a bot message somebody who has never written to it. The link is good for fifteen minutes and can be used once.

**4. Send the test message**

From the Connections screen. It proves the whole path — token, bot, chat — rather than just the token, and it is the only step that does.

**5. Add HeyMetra to the assistant you use**

Claude, ChatGPT, Cursor or Codex. Your assistant can then send to this chat — it shows you the exact text first and nothing goes until you approve it.

Watch what you paste:

- Anything starting `@` is **that is the bot's username, not its token. The token is the long line BotFather sent you, digits then a colon then letters.** and will be refused by name.

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

### One command

```bash
npx add-mcp https://mcp.heymetra.com/mcp
```

[`add-mcp`](https://www.npmjs.com/package/add-mcp) is a third-party installer that writes the configuration for Claude Code, Codex, Cursor, Antigravity, VS Code and seventeen other agents. It infers the name from the address, so the server lands as `heymetra`. Run against this endpoint before it was written here.

### Or by hand

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans only an owner can add it, under Organization settings._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — Settings → Security and login → Developer mode, then chatgpt.com/plugins</summary>

Paste the address above into Settings → Security and login → Developer mode, then chatgpt.com/plugins.

_The endpoint has to include its /mcp path here._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_XAI calls this “bring your own MCP”._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Settings → Connectors → Custom connector → Remote</summary>

Paste the address above into Settings → Connectors → Custom connector → Remote.

_Perplexity documents it as a Pro, Max and Enterprise feature._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_Or a .mcp.json in the project root; /mcp inside a session shows what connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Under an [mcp_servers.<name>] section, then codex mcp login._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Leave the static OAuth fields empty — they exist for servers that cannot register themselves._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_The key is serverUrl, not url — the one every other JSON client spells differently._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## What it may and may not touch

Send a message to the linked Telegram chat — proposed first, with the exact text, and sent only once you approve. It cannot be recalled.

Propose a change through this account's own API, for operations HeyMetra does not cover. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.

Permissions are switched on per connection, and one you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Send messages** | Let your assistant send to this chat, with your approval each time. Turn it off and only the test button can reach it. | Yes — every change waits for your approval |
| **Direct API access** | Let your assistant use this account's own API for anything HeyMetra's other operations do not cover. It reads directly, and what comes back is the provider's own answer rather than a figure HeyMetra has checked. It can also propose changes — those are never applied until you approve them, and HeyMetra cannot undo one afterwards. | Yes — every change waits for your approval |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Send a message to the linked Telegram chat — proposed first, with the exact text, and sent only once you approve. It cannot be recalled.
- Ask this account's own API a question HeyMetra's other operations do not cover. Reads only, and the answer is the provider's own rather than a figure HeyMetra has checked.
- Propose a change through this account's own API, for operations HeyMetra does not cover. Nothing is sent until you approve it, and HeyMetra cannot undo it afterwards.
</details>

Anything that would change something comes back as a proposal you approve, inside bounds that live in code rather than in a prompt: at most 20 messages a rolling day, counted separately from account changes, and an approval that expires after 30 minutes. [How that works](https://heymetra.com/security/).

## When something goes wrong

<details>
<summary>Saving fails and says Telegram rejected the token.</summary>

**Why:** Usually the bot's username was pasted instead of its token, or the token was revoked in BotFather after being copied. Telegram answers 404 for a malformed token and 401 for a revoked one; both mean the same thing here.

**Fix:** Send /token to @BotFather and pick the bot. It shows the current token, which is the long line with a colon in it.

</details>

<details>
<summary>The token saved, but the test message never arrives and nothing says why.</summary>

**Why:** The Start step has not happened. A bot cannot open a conversation in Telegram — the person has to write to it first — so until Start arrives there is no chat to deliver to.

**Fix:** Open the link from the Connections screen again and press Start. Ask for a fresh link if more than fifteen minutes have passed.

</details>

<details>
<summary>The link opens Telegram but nothing seems to happen.</summary>

**Why:** The link carries a one-time code, and it is consumed the first time it is opened. Opening the same one twice does nothing the second time.

**Fix:** Ask for a new link on the Connections screen.

</details>

<details>
<summary>Messages arrive for one person, and a colleague wants them too.</summary>

**Why:** The link is redeemed by whoever opens it, so the chat belongs to that person. It is a private chat between them and the bot.

**Fix:** Have the colleague open their own link from their own HeyMetra account. A Telegram connection carries one chat, so a second person is a second link rather than a shared one.

</details>

## What HeyMetra reads from Telegram

Connect your own bot and press Start to link the chat, then send a test message from HeyMetra to confirm it arrives. After that, your assistant can send to that same chat — it shows you the exact text first and nothing is sent until you approve it. Whoever is in that chat sees it, and a sent message cannot be recalled. A bot token reaches Telegram's own API, so your assistant can ask it things as well as send — but a bot sees only what is addressed to it, which here is the one chat you linked.

<details>
<summary>About Telegram</summary>

Telegram is a channel you own outright. HeyMetra does not have an app you install — you create a bot in BotFather, in your own account, and hand us its token. Nothing about it belongs to us: revoke the token and the connection is over the same second, with nothing to ask us for.

What it reaches is one conversation: the chat you open with the bot by pressing Start. A Telegram bot sees only what is addressed to it, so there is no surface here that could wander into somebody else's messages. Groups and channels are a different mechanism and this connector does not do them — one bot, one chat, on purpose.
</details>

## One connection, not seven

The reason to read Telegram through HeyMetra rather than through a server that only knows Telegram is everything else it can answer in the same breath:

**Ads** — [Google Ads](https://heymetra.com/connectors/google-ads/) · [Meta](https://heymetra.com/connectors/meta-ads/)

**Analytics** — [Google Analytics 4](https://heymetra.com/connectors/google-analytics-4/) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp) · [PostHog](https://github.com/zeisoft/posthog-mcp)

**Ecommerce** — [Shopify](https://heymetra.com/connectors/shopify/) · [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://heymetra.com/connectors/stripe/) · [HubSpot](https://heymetra.com/connectors/hubspot/) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · [Zoho Marketing Automation](https://github.com/zeisoft/zoho-marketing-automation-mcp)

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://heymetra.com/connectors/revenuecat/) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Work** — [Google Calendar](https://heymetra.com/connectors/google-calendar/) · [Google Meet](https://heymetra.com/connectors/google-meet/) · [Jira](https://github.com/zeisoft/jira-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · **Telegram**

The full catalogue is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Telegram connector page](https://heymetra.com/connectors/telegram/)
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup for every assistant](https://heymetra.com/mcp/)
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/)
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>Built by <a href="https://zeisoft.com">Zeisoft</a>, who make HeyMetra. Not affiliated with Telegram. This README is generated from HeyMetra's live connector catalogue and refreshed daily; corrections are welcome as issues.</sub>

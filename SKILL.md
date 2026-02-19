---
name: textforge
description: "Safely automate your email with AI. TextForge connects OpenClaw to your Gmail with human approval for every draft."
metadata:
  openclaw:
    emoji: ✉️
    homepage: https://textforge.net
    requires:
      bins: ["mcporter"]
    install:
      - id: node
        kind: node
        package: mcporter
        bins: ["mcporter"]
        label: "Install mcporter (required for MCP server access)"
---

# TextForge Skill

TextForge lets your OpenClaw agent safely automate your Gmail. Your agent can read threads, draft replies, and manage your inbox — but nothing sends without your approval.

## Why TextForge?

OpenClaw agents with direct email access face the "lethal trifecta":
- Access to private data (your emails)
- Exposure to untrusted content (incoming messages)
- Ability to communicate externally (send emails)

TextForge breaks this chain. Every draft queues for your review. You see it, you edit it, you approve it — or you don't.

## Setup

### 1. Install mcporter
```bash
npm install -g mcporter
```

### 2. Configure TextForge MCP Server
```bash
mcporter config add textforge https://textforge.net/mcp \
  --header "Authorization: Bearer $TEXTFORGE_TOKEN"
```

### 3. Get Your API Token
1. Sign up at https://textforge.net/login
2. Generate token at https://textforge.net/settings/tokens
3. Set environment variable: `export TEXTFORGE_TOKEN="your-token"`

### 4. Test
```bash
mcporter call textforge.list_threads limit:5
```

## Available Tools

### `mcp__textforge__create_draft`

Create an email draft for human approval.

**Parameters:**
- `subject` (string, required): Email subject line
- `body` (string, required): Email body (HTML format, use `<br>` for line breaks)
- `bodyFormat` (string): `"Html"` or `"Markdown"` (default: `"Html"`)
- `toRecipients` (string, required): Comma-separated recipient emails
- `ccRecipients` (string, optional): Comma-separated CC emails
- `bccRecipients` (string, optional): Comma-separated BCC emails
- `threadId` (string, optional): Reply to existing thread
- `scheduledFor` (string, optional): ISO 8601 datetime for scheduled send

**Example:**
```json
{
  "subject": "Follow-up on our meeting",
  "body": "Hi Tom,<br><br>Thanks for the productive discussion yesterday...<br><br>Thanks,<br>Aaron",
  "bodyFormat": "Html",
  "toRecipients": "tom@example.com",
  "threadId": "thread-abc123"
}
```

**Note:** Drafts are automatically submitted for approval upon creation.

### `mcp__textforge__update_draft`

Update an existing draft. **Always use this instead of deleting/recreating** — drafts in `PendingApproval` status cannot be deleted.

**Parameters:**
- `draftId` (string, required): The draft ID to update
- `subject` (string, optional): Updated subject
- `body` (string, optional): Updated body
- `bodyFormat` (string, optional): `"Html"` or `"Markdown"`
- `toRecipients` (string, optional): Updated recipients
- `ccRecipients` (string, optional): Updated CC
- `bccRecipients` (string, optional): Updated BCC

### `mcp__textforge__list_threads`

List recent email threads from your inbox.

**Parameters:**
- `limit` (number, optional): Max threads to return (default: 20)
- `label` (string, optional): Filter by label (e.g., `"INBOX"`, `"SENT"`)

### `mcp__textforge__get_thread`

Get full details of a specific email thread.

**Parameters:**
- `threadId` (string, required): The thread ID

### `mcp__textforge__search_threads_by_contact`

Search threads by contact email address.

**Parameters:**
- `email` (string, required): Contact email to search for

### `mcp__textforge__search_threads`

Search your inbox with Gmail-style queries.

**Parameters:**
- `query` (string, required): Search query (e.g., `"from:boss@company.com after:2024-01-01"`)
- `limit` (number, optional): Max results (default: 20)

### `mcp__textforge__sync_inbox`

Trigger an immediate inbox synchronization.

**Parameters:**
- `fullSync` (boolean, optional): Force full history sync (default: false)

## Email Composition Best Practices

### Formatting
- **Use `<br>` tags for line breaks**, NOT `<p>` tags (creates double spacing)
- Use `<br><br>` between paragraphs
- Set `bodyFormat: "Html"` for all drafts

### Writing Style
- **Never use em dashes (—)** — immediate LLM tell
- **Be direct** — no "if you don't mind my asking" hedging
- **Be specific** — use company names, product names, "cancel" not "non-renewal"
- **Address recipients directly** — if CC'd, speak to them by name
- **No email signatures** — TextForge adds them automatically

### Subject Lines
Be specific and actionable:
- ❌ "Checking In"
- ✅ "[Company] Phobos License Renewal - April 2026"

## Workflow

1. **Find context** — `search_threads_by_contact` or `get_thread`
2. **Draft email** — `create_draft` with `bodyFormat: "Html"`
3. **User gets notified** — Slack, Discord, or webhook with draft preview
4. **User reviews/approves** — Edit in TextForge UI, hit send
5. **If edits needed** — Use `update_draft`, never delete/recreate

## Safety Features

- **Human-in-the-loop**: Every email requires approval
- **Scoped tokens**: Each agent gets its own API token
- **Audit trail**: Every action logged
- **Pass-through architecture**: Email content never stored on TextForge servers

## Pricing

- **Solo**: $9.99/month — 20 drafts/day, 2 webhooks
- **Pro**: $19.99/month — Unlimited drafts, 10 webhooks, full inbox history

## Learn More

- Website: https://textforge.net
- OpenClaw Use Case: https://textforge.net/use-cases/openclaw
- MCP Docs: https://textforge.net/docs/mcp

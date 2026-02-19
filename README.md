# OpenClaw TextForge Skill

Official OpenClaw skill for [TextForge](https://textforge.net) — safely automate your Gmail with AI.

---

## Use OpenClaw with Confidence

OpenClaw gives your agent incredible power — including the ability to read and send emails. But with that power comes risk: a prompt injection, a hallucination, or a misunderstood instruction could send an email you never intended.

**TextForge makes OpenClaw safer to use** by adding a human approval layer to every email. Your agent gets full email capability — reading threads, drafting replies, attaching files — but **nothing sends without your review**.

### How It Works

1. **Agent drafts** — Your OpenClaw agent reads the thread and composes a response via MCP
2. **You review** — Get notified via Slack, Discord, or webhook with the full draft preview
3. **You decide** — Edit, approve, or reject. When you approve, it sends from your Gmail with your signature
4. **Loop continues** — When they reply, your agent gets notified to draft the next response

Your agent stays productive. You stay in control.

[See the UI →](https://textforge.net/docs/ui)

### Safety by Design

- **Human-in-the-loop**: Every email requires your approval before sending — catches hallucinations, prompt injection, or just off-tone drafts
- **Scoped API tokens**: Your agent connects through TextForge's API, never touches your Gmail credentials directly. Compromised token? Revoke it without changing your Google password.
- **Full audit trail**: Every draft, edit, approval, and rejection is logged — know exactly what your agent tried to send
- **Pass-through architecture**: Email content is fetched from Gmail on-demand and never stored on TextForge servers

---

## Installation

### 1. Install mcporter
```bash
npm install -g mcporter
```

### 2. Get Your API Token
1. Sign up at [textforge.net](https://textforge.net/login)
2. Generate token at [textforge.net/tokens](https://textforge.net/tokens)
3. Set environment variable:
   ```bash
   export TEXTFORGE_TOKEN="your-token-here"
   ```

### 3. Configure TextForge MCP Server
```bash
mcporter config add textforge https://textforge.net/mcp \
  --header "Authorization: Bearer $TEXTFORGE_TOKEN"
```

### 4. Test the Connection
```bash
mcporter call textforge.list_threads limit:5
```

---

## What Can Your Agent Do?

Once configured, your OpenClaw agent can:

- **Draft emails** — with full thread context, ready for your approval
- **Search your inbox** — find relevant conversations instantly
- **Read threads** — understand the full conversation history
- **Manage follow-ups** — never drop the ball on important conversations
- **Sync inbox state** — keep everything current

Your agent gets the power. You keep the control.

---

## Real Use Cases

**Sales follow-ups** — CRM exports leads, AI drafts follow-ups, you approve the batch

**Customer support** — AI reads the thread, drafts a reply with full context

**Procurement** — W-9s, insurance certs, vendor contracts. Pulled and attached.

**Market research** — Personal outreach from your Gmail, not a bulk tool

**Relationship management** — Never forget a check-in, birthday, or quarterly touch

[See all use cases →](https://textforge.net/use-cases)

---

## Pricing

Simple, transparent pricing. No free tier. No trial. No tricks.

| Plan | Price | What's Included |
|------|-------|-----------------|
| **Solo** | $9.99/month | 20 drafts/day, 2 webhooks, 30-day inbox sync |
| **Pro** | $19.99/month | Unlimited drafts, 10 webhooks, full inbox history |

---

## Learn More

- **[TextForge](https://textforge.net)** — Home
- **[OpenClaw Use Case](https://textforge.net/use-cases/openclaw)** — Why this matters for OpenClaw users
- **[MCP Documentation](https://textforge.net/docs/mcp)** — Full API reference
- **[Agent Safety](https://textforge.net/use-cases/agentic-workflows)** — General agent safety principles

---

## Documentation

See [SKILL.md](./SKILL.md) for complete tool documentation, formatting guidelines, and best practices for email composition.

---

*Set up in 5 minutes. Use OpenClaw with confidence.*

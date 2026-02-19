# OpenClaw TextForge Skill

Official OpenClaw skill for [TextForge](https://textforge.net) — safely automate your Gmail with AI.

---

## The Risk is Real

OpenClaw went from zero to 180,000 GitHub stars in weeks. Security researchers found thousands of misconfigured instances leaking API keys, OAuth tokens, and credentials. When your OpenClaw agent has direct email access, it faces the "lethal trifecta":

- **Access to private data** — your emails
- **Exposure to untrusted content** — incoming messages with hidden instructions
- **Ability to communicate externally** — send emails that can't be unsent

Email is the most dangerous capability an AI agent can have.

---

## TextForge Breaks the Chain

TextForge sits between your OpenClaw agent and your Gmail. Your agent gets full email capability — reading threads, drafting replies, attaching files — but **nothing sends without your approval**.

Every draft queues for your review. You see it, you edit it, you approve it — or you don't.

### Safety Features

- **Human-in-the-loop**: Every email requires approval before sending
- **Scoped API tokens**: Your agent connects through TextForge's API, never touches your Gmail credentials directly
- **Full audit trail**: Every draft, edit, approval, and rejection is logged
- **Pass-through architecture**: Email content is never stored on TextForge servers

### The Workflow

1. **Agent reads context** — searches threads, gets full email history
2. **Agent drafts response** — composes a reply with proper context
3. **You get notified** — Slack, Discord, or webhook with draft preview
4. **You review and approve** — catch hallucinations, prompt injection, or just fix tone
5. **Email sends** — from your Gmail, with your signature
6. **Reply triggers agent** — when they respond, your agent gets notified to draft the next message

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

*Take back your inbox. Set up in 5 minutes.*

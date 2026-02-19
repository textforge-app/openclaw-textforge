# OpenClaw TextForge Skill

Official OpenClaw skill for [TextForge](https://textforge.net) - safely automate your Gmail with AI.

## What is TextForge?

TextForge sits between your OpenClaw agent and your Gmail. Your agent gets full email capability — reading threads, drafting replies, attaching files — but **nothing sends without your approval**.

## Installation

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
1. Sign up at [textforge.net](https://textforge.net/login)
2. Generate token at [textforge.net/settings/tokens](https://textforge.net/settings/tokens)
3. Set environment variable: `export TEXTFORGE_TOKEN="your-token"`

### 4. Test
```bash
mcporter call textforge.list_threads limit:5
```

## Usage

Once configured, your OpenClaw agent can use TextForge to:
- Draft emails for your approval
- Search and read email threads
- Manage follow-ups
- Sync inbox state

See [SKILL.md](./SKILL.md) for full documentation.

## Pricing

- **Solo**: $9.99/month — 20 drafts/day
- **Pro**: $19.99/month — Unlimited drafts

## Learn More

- [TextForge](https://textforge.net)
- [OpenClaw Use Case](https://textforge.net/use-cases/openclaw)
- [MCP Documentation](https://textforge.net/docs/mcp)

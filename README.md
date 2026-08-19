<p align="center"><img src="logo.png" width="84" alt="OntoRamp"></p>

# OntoRamp Graph Query — MCP Server

> The MCP server that answers "what does governance say about this?" — evidence-grounded answers from a curated architecture and governance knowledge base, not a document dump.

**Problem:** AI agents act blindly against organizational architecture. They don't know what the org has already decided, what constraints apply, or what the existing structure says about a proposed action.

**Solution:** Query a curated architecture and governance knowledge base directly from any AI agent or LLM workflow. Returns evidence-grounded answers with citation chains — not document similarity. Works from day one, and grows as your organization seeds its own knowledge.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.ontoramp%2Fgraph--query-blue)](https://registry.modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-live-brightgreen)](https://ontoramp-graph-query.fly.dev/health)

---

## Tools

| Tool | Description | Tier |
|------|-------------|------|
| `query_architecture` | Query organizational architecture for answers grounded in documented structure | Free |
| `get_constraint_signals` | Surface governance constraints relevant to a proposed action or decision | Free |
| `find_dependencies` | Trace dependencies between systems and components in your architecture | Developer+ |
| `get_evidence_for_claim` | Return evidence chains supporting or contradicting an architectural claim | Developer+ |
| `request_assessment` | Submit an Agentic Readiness Assessment request | All tiers, rate-limit exempt |

## Tiers

| Tier | Price | Limits | Features |
|------|-------|--------|----------|
| **Free** | — (no credit card) | 10 queries/day | `query_architecture` + `get_constraint_signals` |
| **Developer** | $0.015/call | Unlimited | All tools · Evidence provenance · Query history |
| **Org** | $249/mo flat | Unlimited | Aggregate architecture health · Cross-agent pooling · ARA pre-population |

`request_assessment` is exempt from rate limits on every tier.

## Install

OntoRamp Graph Query is a **hosted, remote** MCP server (Streamable HTTP) — nothing to install, build, or run locally. See [`llms-install.md`](llms-install.md) for an agent-followable walkthrough.

**1. Get a free API key** at [ontoramp.com/mcp](https://ontoramp.com/mcp) (no credit card). It arrives by email as `or_free_…`.

**2. Add to Cline** — edit `~/.cline/mcp.json` (or use the Cline UI → MCP Servers → Configure):

```json
{
  "mcpServers": {
    "ontoramp-graph-query": {
      "url": "https://ontoramp-graph-query.fly.dev/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

**Other MCP clients** (Claude Desktop, etc.) use the same `mcpServers` shape (`url` + `headers`). Transport is Streamable HTTP.

**3. Verify** — `curl https://ontoramp-graph-query.fly.dev/health` → `{"status":"ok","version":"1.0.0","server":"ontoramp-graph-query"}`.

See [`examples/usage.md`](examples/usage.md) for example calls.

## ARA Trigger

When `get_evidence_for_claim` surfaces evidence coverage gaps, the server prompts:

> Your architecture coverage has gaps that a manual review won't surface. An Agentic Readiness Assessment will diagnose your current state and build a prioritized remediation plan. [Schedule at ontoramp.com/assess](https://ontoramp.com/assess).

## Security

- All responses are audited for public release — no scoring-formula internals, no substrate architecture details
- Your data is scoped to your tenant namespace and never shared across organizations
- Free-tier keys are read-scoped; Developer/Org keys require account authentication
- `GET /health` returns live status

## Support

- Docs: [ontoramp.com/mcp](https://ontoramp.com/mcp)
- Issues: [github.com/ontoramp/ontoramp-graph-query/issues](https://github.com/ontoramp/ontoramp-graph-query/issues)
- Contact: m@ontoramp.com

---

*Governed by OntoRamp Governance Physics. OntoRamp LLC · [ontoramp.com](https://ontoramp.com)*

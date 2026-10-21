# MOSN — Solana token safety, fresh alpha & safe swaps for AI agents

**MOSN** is an autonomous Solana agent that screens every brand-new token in real time (PumpSwap + Raydium CPMM pool creations, seconds after launch) and sells what it learns — pay-per-call, no API key, no signup.

- 🛡️ **Rug / safety checks** — mint & freeze authority, dangerous Token-2022 settings, real-wallet holder concentration (pools excluded), live sell-route round-trip test
- 🆕 **Real-time new pools** — straight from on-chain pool-creation logs
- ⚡ **Fresh Solana alpha** — new tokens that *passed* MOSN's screens, with its AI verdict + live market data
- 📊 **Labeled memecoin dataset** — features + what the price did 5/10/15 min later
- 🔁 **Safe Swap** — refuses buys into DANGER tokens, returns an unsigned Jupiter swap for *your* wallet

Base URL: **https://mosn-api.mosn-3r41y.workers.dev**

## 🤖 For people: Telegram bot
**[@MOSNSafeSwapBot](https://t.me/MOSNSafeSwapBot)** — send any Solana token address or pump.fun / DexScreener link and get a rug-check verdict in seconds plus one-tap Buy / Sell buttons. You sign in your **own** Phantom or Solflare wallet; MOSN never holds keys or funds. 0.5% fee (half of most Telegram trading bots). Refuses to route buys into DANGER tokens.

📣 **Free alerts channel: [@MOSNAlpha](https://t.me/MOSNAlpha)** — new Solana tokens that passed MOSN's rug checks, posted in real time.

## Use it from Claude / Cursor / any MCP client (remote MCP)

```json
{
  "mcpServers": {
    "mosn": { "type": "http", "url": "https://mosn-api.mosn-3r41y.workers.dev/mcp" }
  }
}
```

Tools:
| Tool | What it does | Cost |
|---|---|---|
| `mosn_token_check` | SAFE / CAUTION / DANGER verdict with reasons | 5 free/day, then x402 |
| `mosn_safe_swap` | Safety-checked Jupiter swap tx for your wallet | free (0.3% platform fee) |
| `mosn_paid_endpoints` | Lists the paid data endpoints | free |

## Pay-per-call HTTP API (x402 — USDC on Solana or Base)

| Endpoint | Price |
|---|---|
| `GET /token-check?mint=<mint>` | $0.005 |
| `GET /holders?mint=<mint>` | $0.002 |
| `GET /new-pools?minutes=15` | $0.01 |
| `GET /alpha?minutes=30` | $0.05 |
| `GET /dataset?hours=24` | $0.25 |
| `GET /safe-swap?mint=&side=buy&amountSol=0.1&wallet=<pubkey>` | free + 0.3% fee |

Any x402 client works, e.g. `@x402/fetch`:
```js
import { wrapFetchWithPayment, x402Client } from '@x402/fetch';
// register your Solana (or Base) signer with x402Client, then:
const res = await payFetch('https://mosn-api.mosn-3r41y.workers.dev/token-check?mint=JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN');
```

Machine-readable: [`/openapi.json`](https://mosn-api.mosn-3r41y.workers.dev/openapi.json) · [`/.well-known/x402`](https://mosn-api.mosn-3r41y.workers.dev/.well-known/x402) · [`/.well-known/agent.json`](https://mosn-api.mosn-3r41y.workers.dev/.well-known/agent.json) · [`/llms.txt`](https://mosn-api.mosn-3r41y.workers.dev/llms.txt)

Also on **Virtuals ACP** (search "MOSN"): token checks, holder checks, new-pool snapshots, fresh alpha, labeled dataset, crypto research briefs.

## Honest numbers
New Solana tokens are extremely risky. In MOSN's own tracking, roughly 1 in 4 brand-new tokens that passed basic scam checks still crashed 50%+ within 15 minutes. MOSN's checks reduce risk; they don't remove it. **Not financial advice.**

## Daily public reports
MOSN publishes a free daily "Solana new-token report" from its own data — see the links in [REPORTS.md](REPORTS.md).

---
Built and operated autonomously by MOSN · X: [@MOSNagent](https://x.com/MOSNagent) · Alerts: [@MOSNAlpha](https://t.me/MOSNAlpha)

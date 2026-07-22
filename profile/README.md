<p align="center">
  <img src="./assets/logo.png" alt="YummyBait" width="200">
</p>

<h1 align="center">YummyBait</h1>

<p align="center">
  DeFi analytics and autonomous tooling for Uniswap liquidity providers.<br>
  <a href="https://yummybait.finance?utm_source=gh">yummybait.finance</a> ·
  <a href="https://docs.yummybait.finance/">docs</a>
</p>

---

LP positions drift out of range and bleed impermanent loss while nobody's watching. YummyBait
tracks them in real time, scores the risk, and gives you — or an agent acting on your behalf —
the tools to act on it.

## What we build

- **[YummyBait](https://yummybait.finance?utm_source=gh)** — real-time indexing, position
  tracking, and risk scoring for Uniswap V3 and V4, with a signals API and a
  [Telegram bot](https://t.me/Yummybait_bot) on top.
- **[`uniswap-tx-builder-mcp`](https://github.com/Yummybait-fin/uniswap-tx-builder-mcp)** — a
  keyless [MCP](https://modelcontextprotocol.io) server that builds unsigned Uniswap LP
  transactions (collect, close, mint, increase, wrap, swap) and simulates them via `eth_call`.
  It never holds keys and never signs. Published on
  [npm](https://www.npmjs.com/package/@yummybait/uniswap-tx-builder-mcp).
- **[`cdp-wallet-agent-example`](https://github.com/Yummybait-fin/cdp-wallet-agent-example)** —
  a playbook, not a program: your local Claude Code becomes an LP agent that polls YummyBait's
  signals and acts on your positions, guarded by a Coinbase CDP Wallet Policy so only Uniswap
  position-manager calls can ever get signed.

## How it fits together

```
YummyBait signals  →  your agent (Claude Code + strategy in plain English)
                   →  uniswap-tx-builder-mcp (unsigned calldata)
                   →  your wallet (CDP, viem, ...) signs & broadcasts
```

Nothing in this chain custodies funds or holds signing keys except your own wallet.

## Principles

- **Non-custodial, always.** Your keys, your wallet, your signature.
- **Keyless by design.** The tx builder only builds and simulates — it never signs.
- **Guardrails enforced server-side.** Wallet policy checks happen at the signer, not in a prompt.
- **Observe before act.** Agent tooling defaults to telling you what it would do; you opt in to
  acting.
- **Open source.** Read what runs before you trust it.

## Links

- Product — https://yummybait.finance
- Docs — https://docs.yummybait.finance
- Telegram bot — https://t.me/Yummybait_bot
- npm — https://www.npmjs.com/package/@yummybait/uniswap-tx-builder-mcp

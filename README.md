# Awesome On-Chain Prediction Markets [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**A curated list of on-chain prediction-market protocols, apps, resolution oracles and developer tooling — 2026.**

> A prediction market lets people trade shares in the outcome of a future event; the price of a "yes" share tracks the crowd's implied probability. On-chain prediction markets settle these trades with smart contracts and resolve them with oracles, so positions and payouts are publicly verifiable. This list tracks the apps people trade on, the protocols and liquidity layers underneath them, the oracles that resolve markets, and the tooling for building your own.

> PRs welcome — see [Contributing](#-contributing). Neutral, no referral spam.

---

## Contents

- [What Are On-Chain Prediction Markets?](#-what-are-on-chain-prediction-markets)
- [Prediction Market Apps](#-prediction-market-apps)
- [Protocols & Liquidity Layers](#-protocols--liquidity-layers)
- [Resolution & Oracles](#-resolution--oracles)
- [Developer Tooling & SDKs](#-developer-tooling--sdks)
- [Data & Analytics](#-data--analytics)
- [Docs & Reading](#-docs--reading)
- [Contributing](#-contributing)
- [License](#-license)

> **Legend** — 🟢 Live · 🟡 Beta/Regional · 🔴 Inactive · 🔓 Self-custodial · 🧱 Protocol/infra · 📖 Open source

---

## 📖 What Are On-Chain Prediction Markets?

Two mechanics recur across the space:

- **Outcome tokens.** A market mints a token per outcome (e.g. "Yes" / "No"). Each resolves to $1 if its outcome occurs and $0 otherwise; the live price sits between and reads as a probability. The [Gnosis Conditional Tokens Framework](https://docs.gnosis.io/conditionaltokens/) is the most widely reused implementation.
- **Resolution via oracle.** When the event settles, an oracle reports the result on-chain. Common designs are optimistic oracles ([UMA](https://docs.uma.xyz/)) and escalation-game oracles ([reality.eth](https://reality.eth.limo/)).

Markets differ by **order model** (central-limit order book vs. AMM/liquidity pool), **chain**, **collateral** (usually USDC), and **who can create or resolve markets**.

> ⚠️ Availability and legality vary by jurisdiction; several venues geo-restrict. This list is informational and is not financial, legal or betting advice.

---

## 🎯 Prediction Market Apps

Consumer-facing venues where you can trade outcomes directly.

| Project | Model | Chain | Notable | Status | Link |
| --- | --- | --- | --- | --- | --- |
| **Polymarket** 🔓 | Order book (CLOB) | Polygon | Largest on-chain prediction market by volume; USDC-settled; Gnosis CTF + UMA resolution | 🟢 Live | [polymarket.com](https://polymarket.com/) |
| **Limitless** 🔓 | Order book + AMM | Base | Crypto, sports, finance and politics markets, incl. short-duration (5-min/hourly) price markets | 🟢 Live | [limitless.exchange](https://limitless.exchange/) |
| **Myriad** 🔓 | AMM | Abstract, Linea, BNB | Prediction app by DASTAN (Decrypt / Rug Radio); crypto, sports, politics and culture markets | 🟢 Live | [myriad.markets](https://myriad.markets/) |
| **Drift BET** 🔓 | On-chain | Solana | Prediction markets from the Drift perps protocol; multi-collateral | 🟢 Live | [app.drift.trade/bet](https://app.drift.trade/bet) |
| **Overtime** 🔓 | AMM (Thales) | Optimism, Arbitrum, Base | On-chain sports markets built on the Thales protocol | 🟢 Live | [overtimemarkets.xyz](https://overtimemarkets.xyz/) |
| **bookmaker.XYZ** 🔓 | Azuro liquidity | Multi-chain | Consumer sports app powered by Azuro's permissionless markets | 🟢 Live | [bookmakerxyz.app](https://bookmakerxyz.app/) |
| **Sapience (Foil)** 🔓 | AMM | Base, Ethereum | Markets on on-chain "resources" such as gas and blobspace; UMA-resolved | 🟢 Live | [foil.xyz](https://foil.xyz/) |

> Building an on-chain prediction-market app? Open a PR — neutral, accurate descriptions only.

---

## 🧱 Protocols & Liquidity Layers

Infrastructure other apps build on, rather than consumer venues themselves.

| Project | Role | Notable | Status | Link |
| --- | --- | --- | --- | --- |
| **Azuro** 🧱 | Prediction/betting liquidity layer | B2B protocol; multiple front-ends (bookmaker.XYZ, DexWin, PinWin, Giraft) build on its pools | 🟢 Live | [azuro.org](https://azuro.org/) |
| **Thales** 🧱 | Parimutuel/AMM markets protocol | Powers Overtime and other market front-ends | 🟢 Live | [thalesmarket.io](https://thalesmarket.io/) |
| **Hyperliquid outcome markets** 🧱 | On-chain binary outcome markets | Native `outcomeMeta` / `settledOutcome` markets on the Hyperliquid L1 (e.g. recurring price-binary markets) | 🟢 Live | [Hyperliquid API docs](https://hyperliquid.gitbook.io/hyperliquid-docs/for-developers/api/info-endpoint/spot) |

---

## 🔮 Resolution & Oracles

How markets get settled on-chain.

- [**UMA Optimistic Oracle**](https://docs.uma.xyz/) 🧱📖 — Optimistic oracle used by Polymarket and others; outcomes are asserted with a bond and can be disputed. [Contracts](https://github.com/UMAprotocol/protocol).
- [**reality.eth**](https://reality.eth.limo/) 🧱📖 — Crowd-sourced escalation-game oracle for verifying real-world outcomes; pluggable arbitrators. [Monorepo](https://github.com/RealityETH/monorepo).
- [**Gnosis Conditional Tokens Framework**](https://docs.gnosis.io/conditionaltokens/) 🧱📖 — ERC-1155-based framework for representing and settling outcome tokens; widely forked. [Contracts](https://github.com/gnosis/conditional-tokens-contracts).

---

## 🛠️ Developer Tooling & SDKs

Build, integrate or query prediction markets.

- [**UMA dev-quickstart-oov3**](https://github.com/UMAprotocol/dev-quickstart-oov3) 📖 — Reference `PredictionMarket.sol` and quick-start for building an optimistic-oracle-resolved binary market.
- [**Polymarket API & docs**](https://docs.polymarket.com/) 📖 — REST/CLOB and Gamma market APIs for reading markets and placing orders.
- [**Azuro Protocol (GitHub)**](https://github.com/Azuro-protocol) 📖 — SDK, subgraphs and contracts for building on the Azuro liquidity layer.
- [**Gnosis conditional-tokens-contracts**](https://github.com/gnosis/conditional-tokens-contracts) 📖 — Solidity contracts for splitting, merging and redeeming outcome tokens.

---

## 📊 Data & Analytics

- [**DefiLlama — Prediction Markets**](https://defillama.com/) — Category TVL/volume tracking across prediction-market protocols.
- [**Dune**](https://dune.com/) — Community dashboards for Polymarket and other on-chain markets.
- [**Polymarket Leaderboard**](https://polymarket.com/leaderboard) — Public trader rankings and volumes.

---

## 📚 Docs & Reading

- [**UMA — Prediction Market tutorial**](https://docs.uma.xyz/developers/optimistic-oracle-v3/prediction-market) — How an optimistic-oracle-resolved market works end to end.
- [**Gnosis Conditional Tokens docs**](https://docs.gnosis.io/conditionaltokens/) — Outcome-token mechanics and motivation.
- [**Polymarket — Learn**](https://docs.polymarket.com/concepts) — How prediction markets and resolution work.

---

## 🤝 Contributing

PRs welcome — the space moves fast.

1. **Fork** and create a feature branch (e.g. `feature/add-foo`).
2. **Match the column structure** of the section you're editing.
3. **Quality bar:** live (or clearly-marked beta), working link, genuinely an on-chain prediction market, protocol, oracle or tool.
4. **One row/bullet per project.** Use the legend consistently.
5. **No referral spam.** Neutral, accurate descriptions; disclose affiliations.

For corrections (broken links, inactive projects), open an issue or a small PR.

---

## 📄 License

[CC0](https://creativecommons.org/publicdomain/zero/1.0/) — public domain. Made for the on-chain prediction-market community.

---

> **Maintainer note:** This list is maintained by the team behind [Dexly](https://dexly.trade/) (Hyper Lion LTD), a self-custodial mobile app that includes prediction-market trading. The goal is a neutral, useful directory of the whole category, and competing projects are welcome via PR. **Not affiliated with Hyperliquid.**

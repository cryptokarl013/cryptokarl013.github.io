---
title: "Report #0134.4 — undeads.com Routed ~$1M Through OFAC-Sanctioned Cryptex.net While Its Investors Received Funds from the Same Platform"
description: "On-chain tracing of ~540 ETH (~$970K spring-2023) flowing from undeads.com wallets through intermediaries to OFAC-sanctioned Cryptex.net hot wallets, with funds also flowing back to the investor cluster and onward to Binance."
permalink: /reports/0134/4-cryptex-routing/
canonical_url: https://cryptokarl013.xyz/reports/0134/4-cryptex-routing/
image: https://cryptokarl013.xyz/assets/reports/0134/report_0134.4_cover.png
author: cryptokarl013
date: 2026-04-07
last_modified_at: 2026-04-24
redirect_from:
  - /report-0134-stolen-ETHs-Leads-to-NFT-Whales-n0b0dy-indifferent-and-investments-into-a-real-company-undeadscom/report-0134.4-undeads-routed-1M-through-OFAC-sanctioned-cryptex-net/
---

# Report #0134.4 — undeads.com Routed ~$1M Through OFAC-Sanctioned Cryptex.net While Its Investors Received Funds from the Same Platform

> This report is part of the larger investigation [#0134 — Stolen ETH traced to NFT whales and an investment into undeads.com](/reports/0134/).

> **Update 2026-04-14:** a new address [`0xc5fb927cb25ffec6360db345e0deb1de12e307b4`](https://intel.arkm.com/explorer/address/0xc5fb927cb25ffec6360db345e0deb1de12e307b4) connects cryptnex.com (~1.5M USDT transferred), `n0b0dy.eth` (210 ETH), `indifferent.eth` (34.7 ETH), and a Binance deposit wallet (~300K USDT).

## Abstract

- Between **February and May 2023**, on-chain evidence shows a bidirectional flow of funds involving:
  - Two **Cryptex.net** hot wallets.
  - Wallets associated with **`n0b0dy.eth`** and **`indifferent.eth`**.
  - An **undeads.com** wallet (`UndeadsMysteryBox`) and a second undeads.com operating wallet.
  - A **Binance** deposit wallet.
- In total, the undeads.com operating wallet transferred approximately **540 ETH (~$970K at spring-2023 prices)** to intermediary wallets, which forwarded **409,245 USDT** and **138,083 USDT** to a Cryptex hot wallet and ~306,946 USDT to a Binance deposit wallet.
- On the reverse flow, Cryptex hot wallets sent approximately **100 ETH** to `n0b0dy.eth` and **60,222 USDT** to `indifferent.eth`.
- On **26 September 2024**, **Cryptex.net** was designated by the U.S. Treasury's Office of Foreign Assets Control (OFAC) under Executive Orders 13694 and 14024. The Cryptex.net infrastructure was subsequently seized in a U.S. / Netherlands joint action (Operation Endgame).

The funds at issue predate the OFAC designation. The report does **not** claim that use of Cryptex.net at the time was unlawful. The report's finding is that the combination of (i) an undeads.com wallet as a *source* of funds flowing through Cryptex.net infrastructure and (ii) the same Cryptex infrastructure delivering funds back to wallets that subsequently invested into undeads.com is a pattern **consistent with** a closed-loop obfuscation cycle — which is material information for anyone evaluating the provenance of the project's capital.

## Material of investigation

- **U.S. Treasury OFAC** — [September 26, 2024 press release designating Cryptex.net and associated parties](https://ofac.treasury.gov/recent-actions/20240926)
- **Etherscan** — transaction-level data for all cited hashes
- **Arkham Intelligence** — address labels used in the wallet-identity table below
- **Breadcrumbs.app** — [shared fund-flow report](https://www.breadcrumbs.app/reports/39217?share=18e383c8-dbe7-4c72-8084-e2ec3c962d6e)

## What Cryptex.net was

Cryptex.net was a cryptocurrency exchange that the **U.S. Treasury Department (OFAC)** [designated on September 26, 2024](https://ofac.treasury.gov/recent-actions/20240926) as a major money-laundering platform. Key facts from the official OFAC designation and the U.S. Secret Service public statement:

- Processed over **$5.88 billion** in cryptocurrency transactions over its lifetime.
- Received more than **$51.2 million** in funds derived from ransomware attacks.
- Associated with over **$720 million** in transactions connected to Russia-based ransomware actors, fraud shops, mixing services, and darknet markets.
- Designated under Executive Orders 13694 and 14024.
- Cryptex's payment processor "**CryptexPay**" generated new wallet addresses for each transaction and mixed deposits — behaviour described by OFAC as designed to obstruct tracing.
- Netherlands authorities (FIOD, NHCTU), the U.S. Secret Service, and the German Federal Criminal Police (BKA) — under Operation Endgame — seized Cryptex's infrastructure and recovered approximately **€7M** in cryptocurrency from seized servers.

![Cryptex.net seizure notice from the U.S. Secret Service / U.S. Attorney's Office for the District of Maryland / Operation Endgame](/assets/reports/0134/cryptex.net.png)

Archived state: <https://web.archive.org/web/20251031223642/https://cryptex.net/>

For detail about specific individuals designated alongside Cryptex, readers are directed to the [official OFAC press release](https://ofac.treasury.gov/recent-actions/20240926).

## Wallets referenced in this report

| Address | Label |
|---|---|
| [`0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206`](https://etherscan.io/address/0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206) | `n0b0dy.eth` |
| [`0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3`](https://etherscan.io/address/0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3) | `indifferent.eth` |
| [`0xa9615dfa74c79b38ee144169b5e87dfba43ed066`](https://intel.arkm.com/explorer/address/0xa9615dfa74c79b38ee144169b5e87dfba43ed066) | Cryptex.net hot wallet #1 |
| [`0x01baea860c7661561c31b1f765cfe8e064ff6de6`](https://intel.arkm.com/explorer/address/0x01baea860c7661561c31b1f765cfe8e064ff6de6) | Cryptex.net hot wallet #2 |
| [`0xbc75da5ad73edf07b1dd38c4b158f45318f30339`](https://intel.arkm.com/explorer/address/0xbc75da5ad73edf07b1dd38c4b158f45318f30339) | `UndeadsMysteryBox (UNMB)` — undeads.com wallet |
| [`0xe2fc8fcae91f0bb046367d198861731a068a9204`](https://intel.arkm.com/explorer/address/0xe2fc8fcae91f0bb046367d198861731a068a9204) | undeads.com operating wallet |
| [`0xc1cd80849b138909c5599096c0cab36c229ed3cf`](https://intel.arkm.com/explorer/address/0xc1cd80849b138909c5599096c0cab36c229ed3cf) | undeads.com TransparentUpgradeableProxy |
| [`0x9664465588585758823b4b49079cc668097f66eb`](https://intel.arkm.com/explorer/address/0x9664465588585758823b4b49079cc668097f66eb) | Binance deposit wallet |
| [`0x5ed706e051605df8b58844572fa3cf16d2eda5ea`](https://etherscan.io/address/0x5ed706e051605df8b58844572fa3cf16d2eda5ea) | Intermediary wallet |
| [`0x7b03a5d14332b4111ee839f8956f7efe31b69d7a`](https://etherscan.io/address/0x7b03a5d14332b4111ee839f8956f7efe31b69d7a) | Intermediary wallet |
| [`0xc622a675cf2bccc88162e777a1f3e0a275f96f8f`](https://etherscan.io/address/0xc622a675cf2bccc88162e777a1f3e0a275f96f8f) | Intermediary wallet |
| [`0xc5fb927cb25ffec6360db345e0deb1de12e307b4`](https://intel.arkm.com/explorer/address/0xc5fb927cb25ffec6360db345e0deb1de12e307b4) | New (2026-04-14) — connects cryptnex.com, `n0b0dy.eth`, `indifferent.eth`, Binance |

> **Note:** By May 2023, `n0b0dy.eth` and `indifferent.eth` had received approximately **~23,000 USDT (to `indifferent.eth`)** and **~90,000 USDT (to `n0b0dy.eth`)** from Cryptex hot wallets. See the shared [Breadcrumbs report](https://www.breadcrumbs.app/reports/39217?share=18e383c8-dbe7-4c72-8084-e2ec3c962d6e) for detail.

![Breadcrumbs flow graph showing funds between undeads.com wallets, Cryptex hot wallets, n0b0dy.eth, indifferent.eth, and a Binance deposit wallet during February–May 2023](/assets/reports/0134/breadcrumbs_report_134.4.png)

## Transaction sequence

### Step 1 — Investor wallets fund the UndeadsMysteryBox (23 February 2023)

- `n0b0dy.eth` → `UndeadsMysteryBox`: **20 ETH** — [tx `0x64fbef3a…7e38c`](https://etherscan.io/tx/0x64fbef3a556c176d5b3c947b080e4dcec619a4ca00510f64fa7ce3f6f897e38c)
- `indifferent.eth` → `UndeadsMysteryBox`: **0.06 ETH** — [tx `0xb5d198c…4efe`](https://etherscan.io/tx/0xb5d198c43334b88ce314207bee190fa244166208850eff23f67d2b64798d4efe)

Both transfers to the **same** project wallet on the **same day** are consistent with the pair acting in coordination.

### Step 2 — undeads.com operating wallet → intermediary → Cryptex (27 March 2023)

- undeads.com (`0xe2fc…9204`) → intermediary `0x5ed7…5ea`: **240 ETH** — [tx](https://etherscan.io/tx/0x9e513fe4346bbcb657e3a020300ec2a52728b48fe77701569f64bf3f2a3aa27e)
- Intermediary `0x5ed7…5ea` → Cryptex hot wallet #2: **409,245 USDT** — [tx](https://etherscan.io/tx/0xd4a5f00b5f0432beff0c44a882e499ee4cb24cba99e9162e0e9739702e2e675e)

### Step 3 — Cryptex → investor wallets (4–5 April 2023)

- Cryptex hot wallet #2 → `n0b0dy.eth`: **100 ETH** — [tx](https://etherscan.io/tx/0xe82d496d785c6dbb8ef5c106a9b2a0b47c2a9be25ba61d944a438def999f0543)
- Cryptex hot wallet #2 → `indifferent.eth`: **60,222 USDT** — [tx](https://etherscan.io/tx/0x4f047877cc2fc94d4dd55ed9f12ebcc2e6b00c7c81f1345c2e09494f2a04eee7)

### Step 4 — undeads.com → intermediary → Cryptex → Binance (13–21 April 2023)

- undeads.com → intermediary `0x7b03…d7a`: **159 ETH** — [tx](https://etherscan.io/tx/0xb830a4895a6b8ea5ec1173e8c6ac4f08d6e81b3459b6b49f0dbe50f346ab2984)
- Intermediary `0x7b03…d7a` → Cryptex hot wallet #2: **138,083 USDT** — [tx](https://etherscan.io/tx/0x41921fd3317b179971f11e0594f1b1c4e54af0a71ed980bef454abb2108b8eb1)
- Cryptex hot wallet #2 → Binance deposit: **50,000 USDT** — [tx](https://etherscan.io/tx/0x7027aebe6fa1cbc848716f71fe321d8ef511e30fb245379e68d02bd82daf7e86)

### Step 5 — undeads.com → intermediary → Binance (1 May 2023)

- undeads.com → intermediary `0xc622…f8f`: **141 ETH** — [tx](https://etherscan.io/tx/0x3527e4ad4acfcf53524cc7df9d2a1f994598662352833ab78703425be9a18a40)
- Intermediary `0xc622…f8f` → Binance: **5 transactions totalling 256,946 USDT** — [tx1](https://etherscan.io/tx/0x244a1c2fc7676f90f234fa34fe14d645329a42c53d95c44276e12b749a36b48a), [tx2](https://etherscan.io/tx/0xdce5c1e7baa0ac6fd3b86e98fb957578f428cc378f56e64cc559ab01badac924), [tx3](https://etherscan.io/tx/0xdeea8734261daca94a09bfabc5967482db4674fa3dd465dfa40ca554295baf2a), [tx4](https://etherscan.io/tx/0xdd83693327730f9537cd1fd2a1ed44069485bec997ea8e48190a5f2da2f94f30), [tx5](https://etherscan.io/tx/0x88251c4d7ca1fd3b85fd157a9e916ac0bb8751580124dfda2f3ccb34523ed0fe)

### Summary of quantitative flows

- undeads.com operating wallet → intermediaries: **540 ETH (~$970K spring-2023)** aggregate.
- Intermediaries → Cryptex: **409,245 + 138,083 = 547,328 USDT**.
- Cryptex → Binance: **50,000 USDT** (observed).
- Intermediary → Binance: **~256,946 USDT** across 5 transactions.
- Reverse flow: Cryptex → `n0b0dy.eth` ~100 ETH; Cryptex → `indifferent.eth` 60,222 USDT in spring 2023; totals through May 2023 reach ~23K USDT (`indifferent.eth`) and ~90K USDT (`n0b0dy.eth`).

## Flow pattern

```
  ┌──────────────────────────────────────────────────────────┐
  │                                                          │
  ▼                                                          │
Cryptex.net ──► n0b0dy.eth / indifferent.eth ──► undeads.com ┘
  │                                              (UndeadsMysteryBox)
  │
  └──► Intermediaries ──► Binance
```

The cycle is **consistent with** closed-loop obfuscation: funds move between the investor cluster, the project wallets, a platform that OFAC subsequently designated for money-laundering, and a major centralized exchange. The report does not claim that the flow was in violation of law *at the time it occurred* (the OFAC designation post-dates the transfers) — but the pattern is material for anyone evaluating the provenance of the project's capital and the propriety of the investor cluster's fund sources.

## Alternative explanations considered

- **Ordinary over-the-counter activity.** Possible in theory. Ruled inconsistent because the observed flow is bidirectional within a small fixed set of wallets and does not show the breadth of counterparties typical of an OTC market maker.
- **A third-party settlement layer.** Possible in theory. Ruled inconsistent because the intermediary wallets have no other observable counterparties during the relevant window.
- **Simple custody-rotation.** Ruled inconsistent because the flow includes a sanctioned-exchange hop and ends at a centralized-exchange deposit wallet, which is not typical of custody rotation.

## Findings

At the evidence thresholds in [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold):

- **Verifiable:** `n0b0dy.eth` and `indifferent.eth` received funds from Cryptex hot wallets; undeads.com operating wallet sent 540 ETH through intermediaries that forwarded USDT to a Cryptex hot wallet and to a Binance deposit wallet; both investor wallets sent funds to the same `UndeadsMysteryBox` project wallet on the same day.
- **Attributed:** Cryptex.net was a money-laundering platform — source: the September 26, 2024 OFAC designation.
- **Inferred:** The observed bidirectional flow is consistent with closed-loop obfuscation; the undeads.com operating wallet was a **source** of funds flowing through Cryptex infrastructure, not merely a passive recipient of investor funds.

## Related wallets

```
0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206
0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3
0xa9615dfa74c79b38ee144169b5e87dfba43ed066
0x01baea860c7661561c31b1f765cfe8e064ff6de6
0xbc75da5ad73edf07b1dd38c4b158f45318f30339
0x9664465588585758823b4b49079cc668097f66eb
0xe2fc8fcae91f0bb046367d198861731a068a9204
0xc1cd80849b138909c5599096c0cab36c229ed3cf
0x5ed706e051605df8b58844572fa3cf16d2eda5ea
0x7b03a5d14332b4111ee839f8956f7efe31b69d7a
0xc622a675cf2bccc88162e777a1f3e0a275f96f8f
0xc5fb927cb25ffec6360db345e0deb1de12e307b4
```

## Right of reply

undeads.com and any individual associated with the wallets above may submit a response via [Corrections](/corrections/). Any response received will be published at the end of this report in full.

> This report is based on verifiable public blockchain data and the official U.S. Treasury OFAC designation of Cryptex.net (2024-09-26). It is not a criminal allegation against any natural person. See the [Disclaimer](/disclaimer/).

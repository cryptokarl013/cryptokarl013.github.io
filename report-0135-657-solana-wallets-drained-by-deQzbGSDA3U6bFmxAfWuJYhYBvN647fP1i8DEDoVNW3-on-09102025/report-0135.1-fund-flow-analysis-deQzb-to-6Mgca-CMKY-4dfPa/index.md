---
title: Attacker deQzb Follow-up — Laundering into Coinbase and Ongoing SPL Token Seizures. Report 0135.1
description: Crypto Report 0135.1. Follow-up investigation of attacker wallet deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3 from Report #0135. Reveals (1) a laundering path through 6Mgca to a Coinbase Personal Deposit Wallet 4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr, and (2) ongoing SPL token seizures via SetAuthority that expose three more attacker-controlled wallets.
keywords: solana fund flow, stolen SOL tracing, Coinbase deposit wallet, SPL SetAuthority, deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3, 6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb, CMKY625CeWehSuqxSrZJiNibKP13FLmcovPorqxkdcxj, 4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr, 3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad, HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ, Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu, pump.fun
image: https://cryptokarl013.xyz/report-0135-657-solana-wallets-drained-by-deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3-on-09102025/report-0135.1-fund-flow-analysis-deQzb-to-6Mgca-CMKY-4dfPa/report_0135.1_cover.png
date: 2026-04-15
last_modified_at: 2026-04-24
author: cryptokarl013
---
# Report #0135.1 Attacker deQzb Follow-up: Laundering into Coinbase and Ongoing SPL Token Seizures

> [!IMPORTANT]
> This report is part of a larger investigation [Crypto Report #0135 Solana Wallets Drained: Over 650 Accounts Hit in Single-Day Attack on October 9, 2025](https://cryptokarl013.xyz/report-0135-657-solana-wallets-drained-by-deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3-on-09102025/).

## Keywords
crypto theft, stolen SOL tracing, fund flow analysis, Coinbase deposit wallet, SPL SetAuthority, pump.fun, BigQuery, Arkham Intelligence, `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`

## Abstract

A follow-up on-chain investigation of the attacker wallet `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3` (identified in [Report #0135](https://cryptokarl013.xyz/report-0135-657-solana-wallets-drained-by-deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3-on-09102025/) as draining 657 Solana wallets in October 2025) produces two linked findings:

1. **A likely off-ramp into a specific Coinbase account has been identified, although the stolen-SOL batch has not yet been observed traversing it on-chain.** In March 2026, `deQzb` forwarded funds to two intermediaries — `CMKY` and `6Mgca` (Mar 20). Independently, `6Mgca` is observed depositing SOL into `4dfPa`, which [Arkham Intelligence](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) labels as a **Coinbase Personal Deposit Wallet** — an account-specific deposit address belonging to a single Coinbase user. Importantly, the two `6Mgca → 4dfPa` deposits seen in the data (Mar 9 and Mar 17) **predate** the `deQzb → 6Mgca` transfer (Mar 20), so those specific deposits could not have carried the October 2025 stolen SOL. What the data does establish is that `6Mgca` — a wallet that subsequently received stolen funds from `deQzb` — maintains an active deposit channel into this one Coinbase user's account, making it the most plausible exit route for the funds.
2. **The attacker is still active and controls a broader wallet cluster.** In the 6 days to 2026-04-24 the attacker executed 5 transactions that seized SPL token balances via the Solana SPL Token program's `SetAuthority` instruction, with a net USD retention of **+$8,530**. Applying the `SetAuthority` signing rule proves that three additional wallets (`3ScNEE`, `HW66xmb`, `Futbm`) are under the same attacker's control. Combined with the March laundering path, **six attacker-controlled wallets** are now catalogued, plus one identified off-ramp (Coinbase).

## The material of investigation

* Google BigQuery public dataset: `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers` (used for the laundering-path analysis)
* Arkham export of full transfer history for `deQzb`: 676 transactions from 2025-10-09 to 2026-04-24 (used for the ongoing-activity analysis)
* [Solana explorer](https://solscan.io/) — transaction verification
* [Arkham Intelligence](https://intel.arkm.com/) — address labeling (identified `4dfPa` as a Coinbase Personal Deposit Wallet)
* [Solana SPL Token program source](https://github.com/solana-program/token/blob/main/program/src/processor.rs) — authority-change instruction semantics

## Attacker-controlled wallet cluster

| Short Name | Address | Role in this investigation |
|---|---|---|
| **deQzb** | [`deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`](https://intel.arkm.com/explorer/address/deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3) | Primary drainer wallet (Report #0135) |
| **CMKY** | [`CMKY625CeWehSuqxSrZJiNibKP13FLmcovPorqxkdcxj`](https://intel.arkm.com/explorer/address/CMKY625CeWehSuqxSrZJiNibKP13FLmcovPorqxkdcxj) | Intermediary — received from `deQzb` (Mar 2026) |
| **6Mgca** | [`6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb`](https://intel.arkm.com/explorer/address/6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb) | Intermediary — received from `deQzb`, forwarded to Coinbase |
| **3ScNE** | [`3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad`](https://intel.arkm.com/explorer/address/3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad) | Attacker-controlled — signed `SetAuthority` to `deQzb` (Apr 2026) |
| **HW66x** | [`HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ`](https://intel.arkm.com/explorer/address/HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ) | Attacker-controlled — signed `SetAuthority` to `deQzb` (Apr 2026) |
| **Futbm** | [`Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu`](https://intel.arkm.com/explorer/address/Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu) | Attacker-controlled — signed `SetAuthority` to `deQzb` (Apr 2026) |

## Identified off-ramp

| Short Name | Address | Role |
|---|---|---|
| **4dfPa** | [`4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr`](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) | **Coinbase Personal Deposit Wallet** — final on-chain destination of laundered funds |

---

## Part 1 — Laundering path: `deQzb → 6Mgca → 4dfPa [Coinbase]`

### Fund flow overview (chronological)

```
6Mgca ──→ 4dfPa [Coinbase Personal Deposit Wallet]  (Mar  9, 2026 19:51 UTC)  ← predates the attacker distribution
6Mgca ──→ 4dfPa [Coinbase Personal Deposit Wallet]  (Mar 17, 2026 20:14 UTC)  ← predates the attacker distribution
deQzb (attacker) ──→ CMKY                           (Mar 20, 2026 05:39 UTC)
deQzb (attacker) ──→ 6Mgca                          (Mar 20, 2026 05:50 UTC)
```

> [!NOTE]
> The two `6Mgca → 4dfPa` deposits happened *before* `6Mgca` received the stolen SOL from `deQzb` on March 20. They establish `6Mgca`'s Coinbase deposit channel but do not themselves carry the October 2025 stolen funds. A post-March-20 `6Mgca → 4dfPa` transfer — not yet observed in the available data — would be required to prove the specific stolen batch reached Coinbase.

### 1.1 Attacker wallet distributes stolen funds (March 20, 2026)

The attacker wallet `deQzb` made 2 outgoing transfers on the same day, 11 minutes apart — a coordinated distribution:

| # | Timestamp (UTC) | From | To | Tx Signature |
|---|---|---|---|---|
| 1 | 2026-03-20 05:39:29 | deQzb | CMKY | [4HLVP9P8fsiN...](https://solscan.io/tx/4HLVP9P8fsiNzcHf4kHPEZGsgriKDk9mAnUzdP2ZzfvPjUPNKGYsS5ouA7EoXugLVauzivEFLRSvmo6oRFh9m39P) |
| 2 | 2026-03-20 05:50:30 | deQzb | 6Mgca | [3userKsPrSisR5f...](https://solscan.io/tx/3rKsPrSisR5fkJzkp1WciZdcTLQprRfoXmQvR19T2Qy8TUQehfXwdfCgcCrEvsZBLVCKQEEpWuV97Frp6rXvAz8u) |

```sql
-- BigQuery: outgoing transfers from the attacker wallet
SELECT source, destination, block_timestamp, tx_signature
FROM `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers`
WHERE source = 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3'
AND block_timestamp >= TIMESTAMP('2023-01-01')
ORDER BY block_timestamp ASC
```

### 1.2 Intermediary `6Mgca` forwards to Coinbase deposit wallet `4dfPa`

`6Mgca` sent 2 transfers to `4dfPa` (Coinbase Personal Deposit Wallet) on March 9 and March 17, 2026 — **before** receiving its own transfer from `deQzb` on March 20. This ordering indicates `6Mgca` was already an operating intermediary, not a freshly spun-up burn wallet:

| # | Timestamp (UTC) | From | To | Tx Signature |
|---|---|---|---|---|
| 1 | 2026-03-09 19:51:10 | 6Mgca | 4dfPa | [4tAq2uLGqx7R...](https://solscan.io/tx/4tAq2uLGqx7RYzDshoC42tQbRWNJHJ7ETqmdfTrM1r4DYYdBsvxups5Noyo5i84Y8EesF2baQRcxW1KKeuFCBfhU) |
| 2 | 2026-03-17 20:14:10 | 6Mgca | 4dfPa | [4C3YgKKsq5mj...](https://solscan.io/tx/4C3YgKKsq5mjWbYmNhXwVSp4k991gDcqPJQM8uhBy5PJ2BW2DfRvygh2z6EDM12YG8MYCdK77Sc5gRsSUKfhNDye) |

```sql
-- BigQuery: transfers from 6Mgca to 4dfPa
SELECT source, destination, block_timestamp, tx_signature
FROM `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers`
WHERE source = '6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb'
AND destination = '4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr'
AND block_timestamp >= TIMESTAMP('2023-01-01')
ORDER BY block_timestamp ASC
```

### 1.3 `4dfPa` identified as a Coinbase Personal Deposit Wallet

The address [`4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr`](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) is labeled by **Arkham Intelligence** as a **Coinbase Personal Deposit Wallet**. Personal deposit wallets on Coinbase are assigned to a single account holder — so the two March 2026 deposits from `6Mgca` to `4dfPa` (Mar 9 and Mar 17) were credited to one specific Coinbase user.

#### Chronology caveat — what is and isn't proven

Because the `6Mgca → 4dfPa` deposits (Mar 9 and Mar 17) **predate** the `deQzb → 6Mgca` transfer (Mar 20), those two deposits **cannot have carried the SOL drained on October 9, 2025**. The available data therefore does not show stolen SOL physically arriving at Coinbase. What it does show is:

1. `6Mgca` maintains a recurring deposit channel into this one specific Coinbase user's account.
2. `6Mgca` subsequently received stolen SOL from the attacker wallet `deQzb` on March 20.
3. The two facts together make this the single most plausible off-ramp for the stolen funds, but a post-March-20 `6Mgca → 4dfPa` transfer — not yet observed in the available data — would be needed to close the chain.

Once funds reach a Coinbase Personal Deposit Wallet, on-chain tracing stops being meaningful: any subsequent movements belong to Coinbase's internal consolidation infrastructure rather than attacker-controlled addresses. Further identification of the account holder would require a subpoena or legal request to Coinbase.

BigQuery confirms that **no reverse transfers** from `6Mgca`, `CMKY`, or `4dfPa` ever returned to `deQzb` — the observed flow is strictly one-directional.

---

## Part 2 — Ongoing SPL token seizures via `SetAuthority` (April 2026)

The full Arkham export of `deQzb` transfer history (676 transactions from 2025-10-09 to 2026-04-24) shows the attacker is still active. Unlike the October 2025 attack — which only drained native SOL — the April 2026 activity involves **SPL tokens** and a different on-chain primitive: **`SetAuthority`**.

### 2.1 Activity in the last 6 days (2026-04-18 to 2026-04-24)

| Metric | Value |
|---|---|
| Total transactions | 5 |
| `SET OWNER AUTHORITY` events (inbound) | 3 |
| `TRANSFER` events (outbound) | 2 |
| Total USD inflow value | **$19,389.42** |
| Total USD outflow value | **$10,859.11** |
| **Net USD value retained** | **+$8,530.31** |
| Distinct SPL token mints involved | 3 |
| Distinct counterparty addresses | 3 |

### 2.2 Transaction detail (chronological)

| # | Timestamp (UTC) | Action | Flow | Counterparty | Amount | Token Mint | USD Value | Tx |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-04-19 02:00:23 | SET OWNER AUTHORITY | in | `3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad` | 17,094.41 | `3k5z8WWX...afN` | $5,964.46 | [64e1pf9wew2o...](https://solscan.io/tx/64e1pf9wew2ocgL6MSPFvvpMArYaDDBFpkbUHnkrcdoSdeZS2MtdVJH4JSFBB96fckR2LmbP5KAny8dR2wK6V7Kk) |
| 2 | 2026-04-20 18:33:07 | TRANSFER | out | `3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad` | 17,094.41 | `3k5z8WWX...afN` | $5,975.66 | [5uUty1AnuJ7B...](https://solscan.io/tx/5uUty1AnuJ7BWi8VUeVRtE3vs7TWeA49FayftGoLq7UNAzWC9nhxqAFZwkQizSxMAQjPceEZTCDWEUonDqF7A6N6) |
| 3 | 2026-04-23 12:31:18 | SET OWNER AUTHORITY | in | `HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ` | 29,570.00 | `GM9WxQp...d5DD` | $4,875.90 | [2io9VbDHyty4...](https://solscan.io/tx/2io9VbDHyty4jCs9A6R3WYsYK33zSHJybQSqAjQqZVKKF3A5WUmAHtQRqPNGrCnbYpv2mY1VRtg1AHQXqcHRc2UD) |
| 4 | 2026-04-24 00:43:43 | TRANSFER | out | `HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ` | 29,570.00 | `GM9WxQp...d5DD` | $4,883.45 | [vNyhzwSeLb8r...](https://solscan.io/tx/vNyhzwSeLb8rjRPj3VpWYVErZ6omMRbRvmK6Wiw6L7XHm1sNebFMvavMxV4uCkHCYBcYkCmQ4YRNfUH6dzRCHBt) |
| 5 | 2026-04-24 08:06:03 | SET OWNER AUTHORITY | in | `Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu` | 506,617.00 | `3tWGSt...BY2V` | $8,549.06 | [2XSz5Y7uWeEu...](https://solscan.io/tx/2XSz5Y7uWeEurNrMPMYUbAUJWxiLMmrTMakuHM473CVXhrFDJvXWyoxMv6cntqPVRuuzQnD4C2H315JVGmUNLcsc) |

### 2.3 Observations

* **New attack primitive: `SetAuthority`.** The original October 2025 attack drained SOL via direct transfers and `closeAccount`. The April 2026 activity uses `SetAuthority` to seize the `AccountOwner` authority of SPL token accounts — a different technique that specifically targets token holdings rather than SOL balances.
* **Target shift from SOL to SPL tokens (likely memecoins).** Each inbound event brings a different SPL token (`3k5z8WWX...`, `GM9WxQp...`, `3tWGSt...`), all with 6 decimals and small unit prices (~$0.017–$0.35), consistent with Solana memecoins (pump.fun / Raydium-listed). This aligns with Report #0135's finding that 96% of victim wallets had pump.fun activity — the attacker appears to be returning to liquidate token holdings that were left behind in the October 2025 SOL-only sweep.
* **Repeated authority-take → transfer cycle.** Each `SET OWNER AUTHORITY` inbound is followed ~1.5 days later by an outbound `TRANSFER` of the exact same amount of the same token, back to the same counterparty address. For `3ScNEE` and `HW66xmb` the cycle is complete; for `Futbm` the outbound had not yet occurred at export time.
* **Ongoing, not dormant.** Six months after being publicly identified as a drainer in Report #0135, `deQzb` continues to receive and move tokens worth thousands of USD per week. No exchange or authority has frozen this wallet.

### 2.4 Attribution: `3ScNEE`, `HW66xmb`, `Futbm` are attacker-controlled

The SPL Token program's `SetAuthority` instruction has a strict authorization rule: **only the current authority of a token account can sign a transaction that changes the authority**. The instruction is defined in the [Solana SPL Token program](https://github.com/solana-program/token/blob/main/program/src/processor.rs) and requires a signed instruction from the existing authority — the new authority does *not* need to sign or approve.

**What this means for each `SET OWNER AUTHORITY` event:**

| Event | Previous authority | New authority | Who had to sign |
|---|---|---|---|
| 2026-04-19 | `3ScNEE3m4bKy...` | `deQzb...` | **`3ScNEE3m4bKy...` had to sign** |
| 2026-04-23 | `HW66xmbLcqDy...` | `deQzb...` | **`HW66xmbLcqDy...` had to sign** |
| 2026-04-24 | `Futbm4v55YL4...` | `deQzb...` | **`Futbm4v55YL4...` had to sign** |

For each of the three transactions to land on-chain, the private key of `3ScNEE`, `HW66xmb`, and `Futbm` respectively had to sign. Therefore one of the following is true for each counterparty:

1. **The attacker controls the private key of that address** (either directly or via key compromise). In either case the address is now under attacker control.
2. **The address's owner voluntarily handed over authority to a publicly-known drainer wallet.** This is implausible — `deQzb` has been publicly flagged as a SOL drainer since October 2025 and is easily searchable on Solscan and Arkham. No rational legitimate counterparty would knowingly transfer token ownership to it.

**Supporting evidence for the attacker-controlled interpretation:**

* **Pattern repetition.** The identical "authority-take → delayed transfer back" sequence occurred three times in six days with three different counterparties. A repeatable process this consistent points to a single actor running a script.
* **Economic irrationality of the alternative.** If `3ScNEE`, `HW66xmb`, `Futbm` were independent parties, they would be gifting ~$19K of tokens to a known drainer. No inbound payment or service explains this.
* **Fast automated round-trip.** The ~1.5-day cycle between authority change and transfer is consistent with an automated or semi-automated workflow (token-account consolidation, splitting, on-DEX sale preparation) rather than interactions with distinct counterparties.
* **No reciprocal flow.** `deQzb` does not compensate these wallets. A legitimate service relationship would show a two-way flow.

**Conclusion:** `3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad`, `HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ`, and `Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu` are, with high confidence, either additional wallets operated by the same attacker or wallets whose private keys the attacker has compromised. Operationally the distinction does not matter — the attacker signs for all of them.

### 2.5 SPL token mints seen in this window

| Token Mint Address | Total Flow (USD) |
|---|---|
| [`3k5z8WWX6TkpgvDwwr2jDEAaMMwxX56Kj2Xs6HFRjafN`](https://solscan.io/token/3k5z8WWX6TkpgvDwwr2jDEAaMMwxX56Kj2Xs6HFRjafN) | $11,940.12 |
| [`GM9WxQpAi1SwPnc8YGyojZCFHxoCjp4AAzSQEQfQd5DD`](https://solscan.io/token/GM9WxQpAi1SwPnc8YGyojZCFHxoCjp4AAzSQEQfQd5DD) | $9,759.35 |
| [`3tWGStNsYF2VihjBPBv4BpZufoY7iJKbCejnPUatBY2V`](https://solscan.io/token/3tWGStNsYF2VihjBPBv4BpZufoY7iJKbCejnPUatBY2V) | $8,549.06 (inbound only so far) |

---

## Conclusions

**Laundering path (Part 1):**

* The attacker wallet `deQzb` distributed stolen SOL to exactly 2 addresses on March 20, 2026: `CMKY` and `6Mgca`, 11 minutes apart.
* `6Mgca` is observed maintaining an active deposit channel to `4dfPa`, which **Arkham Intelligence identifies as a Coinbase Personal Deposit Wallet** (belonging to a single Coinbase user).
* **Chronology caveat:** the two `6Mgca → 4dfPa` deposits (Mar 9 and Mar 17) **predate** the `deQzb → 6Mgca` transfer (Mar 20), so they could not themselves have carried the October 2025 stolen SOL. The data therefore identifies a *likely* off-ramp but does not yet prove the stolen funds have physically reached Coinbase — that would require a post-March-20 `6Mgca → 4dfPa` transfer not yet visible in the available data.
* The fact that `6Mgca` was already operating as a Coinbase-deposit wallet *before* receiving from `deQzb` indicates it was a pre-existing intermediary, not a freshly-funded burn wallet.
* The observed flow is strictly one-directional — no reverse transfers to `deQzb`.
* Further identification of the Coinbase account holder would require a subpoena or legal request to Coinbase.

**Ongoing activity and wallet cluster (Part 2):**

* `deQzb` remains active six months after publication of Report #0135. In the 6 days to 2026-04-24, `deQzb` executed 5 transactions with a **net retained USD value of +$8,530**.
* The technique has evolved — from SOL drains to SPL token-account seizures via `SetAuthority` — suggesting the attacker is liquidating memecoin holdings left behind in the October 2025 SOL-only sweep.
* **Three additional attacker-controlled wallets** identified via the SPL `SetAuthority` signing requirement: `3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad`, `HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ`, and `Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu`.

**Combined attacker cluster now catalogued:** six wallets (`deQzb`, `CMKY`, `6Mgca`, `3ScNE`, `HW66x`, `Futbm`) plus one identified off-ramp (`4dfPa` → Coinbase).

*This investigation is ongoing...*

*If you have additional information or insights, please reach out at [https://x.com/cryptokarl013](https://x.com/cryptokarl013)*

> [Other investigations by @cryptokarl013](https://cryptokarl013.xyz)

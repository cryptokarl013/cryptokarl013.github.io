---
title: "Report #0135.1 — Attacker deQzb Follow-up: Laundering Path to Coinbase and Ongoing SPL Token Seizures"
description: "Follow-up to Report #0135. Identifies a probable Coinbase off-ramp via the 4dfPa deposit wallet, catalogues three additional attacker-controlled wallets via SPL SetAuthority signer analysis, and records ongoing April 2026 activity."
permalink: /reports/0135/1-fund-flow/
canonical_url: https://cryptokarl013.xyz/reports/0135/1-fund-flow/
image: https://cryptokarl013.xyz/assets/reports/0135/report_0135_cover.png
author: cryptokarl013
date: 2026-04-15
last_modified_at: 2026-04-24
redirect_from:
  - /report-0135-657-solana-wallets-drained-by-deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3-on-09102025/report-0135.1-fund-flow-analysis-deQzb-to-6Mgca-CMKY-4dfPa/
---

# Report #0135.1 — Attacker `deQzb` Follow-up: Laundering Path to Coinbase and Ongoing SPL Token Seizures

> This report is a follow-up to [Report #0135](/reports/0135/).

## Abstract

A follow-up on-chain investigation of the attacker wallet `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3` (the drainer from [Report #0135](/reports/0135/)) produces two linked findings:

1. **A probable off-ramp into a specific Coinbase account has been identified**, although the October 2025 stolen SOL batch has not yet been observed traversing it on-chain. In March 2026, `deQzb` forwarded funds to two intermediaries — `CMKY` and `6Mgca` (March 20). `6Mgca` independently deposits SOL into `4dfPa`, which **[Arkham Intelligence](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) labels as a Coinbase Personal Deposit Wallet** — an account-specific deposit address belonging to a single Coinbase user. The two observed `6Mgca → 4dfPa` deposits (Mar 9 and Mar 17) **predate** the `deQzb → 6Mgca` transfer (Mar 20), so those specific deposits could not have carried the October 2025 stolen SOL. What the data does establish is that `6Mgca` — a wallet that subsequently received stolen funds from `deQzb` — maintains an active deposit channel into this Coinbase user's account. That makes this the single most plausible off-ramp for the stolen funds, pending observation of a post-March-20 `6Mgca → 4dfPa` transfer.
2. **The attacker is still active and controls a broader wallet cluster.** In the 6 days to 2026-04-24, `deQzb` executed 5 transactions that seized SPL token balances via the Solana SPL Token program's `SetAuthority` instruction, with a **net retained USD value of +$8,530**. Applying the `SetAuthority` signing rule proves that three additional wallets — `3ScNEE`, `HW66xmb`, and `Futbm` — are under the attacker's control. Combined with the March laundering path, **six attacker-controlled wallets** are now catalogued, plus one identified off-ramp (Coinbase).

## Material of investigation

- **Google BigQuery public dataset** — `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers` (used for the March 2026 laundering-path analysis).
- **Arkham Intelligence export** — full transfer history for `deQzb`, 676 transactions from 2025-10-09 to 2026-04-24 (used for the ongoing-activity analysis).
- **Solscan** — transaction verification.
- **Arkham Intelligence labels** — quoted verbatim; `4dfPa` identified as a Coinbase Personal Deposit Wallet.
- **Solana SPL Token program source** — [authority-change instruction semantics](https://github.com/solana-program/token/blob/main/program/src/processor.rs).

## Attacker-controlled wallet cluster

| Short name | Address | Role |
|---|---|---|
| **deQzb**  | [`deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`](https://intel.arkm.com/explorer/address/deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3) | Primary drainer (Report #0135) |
| **CMKY**   | [`CMKY625CeWehSuqxSrZJiNibKP13FLmcovPorqxkdcxj`](https://intel.arkm.com/explorer/address/CMKY625CeWehSuqxSrZJiNibKP13FLmcovPorqxkdcxj) | Intermediary — received from `deQzb` Mar 2026 |
| **6Mgca**  | [`6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb`](https://intel.arkm.com/explorer/address/6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb) | Intermediary — received from `deQzb`; forwards to Coinbase |
| **3ScNE**  | [`3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad`](https://intel.arkm.com/explorer/address/3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad) | Signed `SetAuthority` to `deQzb` (Apr 2026) |
| **HW66x**  | [`HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ`](https://intel.arkm.com/explorer/address/HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ) | Signed `SetAuthority` to `deQzb` (Apr 2026) |
| **Futbm**  | [`Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu`](https://intel.arkm.com/explorer/address/Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu) | Signed `SetAuthority` to `deQzb` (Apr 2026) |

## Identified off-ramp

| Short name | Address | Role |
|---|---|---|
| **4dfPa** | [`4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr`](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) | Coinbase Personal Deposit Wallet (Arkham label) — probable off-ramp |

---

## Part 1 — Laundering path: `deQzb → 6Mgca → 4dfPa [Coinbase]`

### Fund-flow timeline

```
6Mgca ──→ 4dfPa [Coinbase Personal Deposit Wallet]  (Mar  9, 2026 19:51 UTC)  ← predates the attacker distribution
6Mgca ──→ 4dfPa [Coinbase Personal Deposit Wallet]  (Mar 17, 2026 20:14 UTC)  ← predates the attacker distribution
deQzb (attacker) ──→ CMKY                           (Mar 20, 2026 05:39 UTC)
deQzb (attacker) ──→ 6Mgca                          (Mar 20, 2026 05:50 UTC)
```

> The two `6Mgca → 4dfPa` deposits occur *before* `6Mgca` receives from `deQzb` on March 20. They establish `6Mgca`'s Coinbase deposit channel but cannot themselves carry the October 2025 stolen SOL. A post-March-20 `6Mgca → 4dfPa` transfer — not yet observed in the available data — is required to prove the specific stolen batch reached Coinbase.

### 1.1 Attacker wallet distributes stolen funds (March 20, 2026)

The attacker wallet `deQzb` made 2 outgoing transfers on the same day, 11 minutes apart — a coordinated distribution:

| № | Timestamp (UTC) | From | To | Tx signature |
|---|---|---|---|---|
| 1 | 2026-03-20 05:39:29 | deQzb | CMKY | [4HLVP9P8fsiN…](https://solscan.io/tx/4HLVP9P8fsiNzcHf4kHPEZGsgriKDk9mAnUzdP2ZzfvPjUPNKGYsS5ouA7EoXugLVauzivEFLRSvmo6oRFh9m39P) |
| 2 | 2026-03-20 05:50:30 | deQzb | 6Mgca | [3rKsPrSisR5f…](https://solscan.io/tx/3rKsPrSisR5fkJzkp1WciZdcTLQprRfoXmQvR19T2Qy8TUQehfXwdfCgcCrEvsZBLVCKQEEpWuV97Frp6rXvAz8u) |

```sql
-- BigQuery: outgoing transfers from the attacker wallet
SELECT source, destination, block_timestamp, tx_signature
FROM `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers`
WHERE source = 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3'
  AND block_timestamp >= TIMESTAMP('2023-01-01')
ORDER BY block_timestamp ASC;
```

### 1.2 `6Mgca` forwards to the Coinbase deposit wallet `4dfPa`

`6Mgca` sent two transfers to `4dfPa` on March 9 and March 17, 2026 — **before** receiving its own transfer from `deQzb` on March 20. The ordering means `6Mgca` was already operating as an intermediary with an established deposit channel, not a freshly spun-up burn wallet.

| № | Timestamp (UTC) | From | To | Tx signature |
|---|---|---|---|---|
| 1 | 2026-03-09 19:51:10 | 6Mgca | 4dfPa | [4tAq2uLGqx7R…](https://solscan.io/tx/4tAq2uLGqx7RYzDshoC42tQbRWNJHJ7ETqmdfTrM1r4DYYdBsvxups5Noyo5i84Y8EesF2baQRcxW1KKeuFCBfhU) |
| 2 | 2026-03-17 20:14:10 | 6Mgca | 4dfPa | [4C3YgKKsq5mj…](https://solscan.io/tx/4C3YgKKsq5mjWbYmNhXwVSp4k991gDcqPJQM8uhBy5PJ2BW2DfRvygh2z6EDM12YG8MYCdK77Sc5gRsSUKfhNDye) |

```sql
-- BigQuery: transfers from 6Mgca to 4dfPa
SELECT source, destination, block_timestamp, tx_signature
FROM `bigquery-public-data.crypto_solana_mainnet_us.Token Transfers`
WHERE source = '6MgcaeMYVfecgMe87UqY8PvtyHQ5FhjeC2XpuoPgyvPb'
  AND destination = '4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr'
  AND block_timestamp >= TIMESTAMP('2023-01-01')
ORDER BY block_timestamp ASC;
```

### 1.3 `4dfPa` is labelled a Coinbase Personal Deposit Wallet

The address [`4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr`](https://intel.arkm.com/explorer/address/4dfPaYTyCyuKKqMyp9Riy84oJmbykceUFBAvRn9d9XSr) is labelled by **Arkham Intelligence** as a **Coinbase Personal Deposit Wallet**. Personal deposit wallets on Coinbase are assigned to a single account holder, so the two March 2026 deposits from `6Mgca` were credited to one specific Coinbase user.

#### What is and isn't proven

- The two `6Mgca → 4dfPa` deposits (Mar 9 and Mar 17) predate `deQzb → 6Mgca` (Mar 20) and therefore **cannot have carried** the SOL drained on October 9, 2025.
- Available data **does show** that `6Mgca` maintains a recurring deposit channel into this one specific Coinbase user's account, and that `6Mgca` subsequently received stolen SOL from the attacker wallet `deQzb` on March 20.
- A post-March-20 `6Mgca → 4dfPa` transfer — not yet observed in the available data — would be required to close the chain.

Once funds reach a Coinbase Personal Deposit Wallet, on-chain tracing stops being meaningful: any subsequent movements belong to Coinbase's internal consolidation infrastructure. Further identification of the account holder would require legal process to Coinbase.

BigQuery confirms that **no reverse transfers** from `6Mgca`, `CMKY`, or `4dfPa` ever returned to `deQzb` — the observed flow is strictly one-directional.

---

## Part 2 — Ongoing SPL token seizures via `SetAuthority` (April 2026)

Unlike the October 2025 attack — which drained only native SOL — the April 2026 activity uses a different on-chain primitive: **`SetAuthority`** to seize the owner authority of SPL token accounts.

### 2.1 Activity in the 6 days to 2026-04-24

| Metric | Value |
|---|---|
| Total transactions | 5 |
| `SET OWNER AUTHORITY` events (inbound) | 3 |
| `TRANSFER` events (outbound) | 2 |
| Total USD inflow value | **$19,389.42** |
| Total USD outflow value | **$10,859.11** |
| **Net USD retained** | **+$8,530.31** |
| Distinct SPL token mints involved | 3 |
| Distinct counterparty addresses | 3 |

### 2.2 Transaction detail

| № | Timestamp (UTC) | Action | Flow | Counterparty | Amount | Token mint | USD value | Tx |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-04-19 02:00:23 | SET OWNER AUTHORITY | in  | `3ScNEE3m4bKy…` | 17,094.41 | `3k5z8WWX…afN` | $5,964.46 | [64e1pf9wew2o…](https://solscan.io/tx/64e1pf9wew2ocgL6MSPFvvpMArYaDDBFpkbUHnkrcdoSdeZS2MtdVJH4JSFBB96fckR2LmbP5KAny8dR2wK6V7Kk) |
| 2 | 2026-04-20 18:33:07 | TRANSFER            | out | `3ScNEE3m4bKy…` | 17,094.41 | `3k5z8WWX…afN` | $5,975.66 | [5uUty1AnuJ7B…](https://solscan.io/tx/5uUty1AnuJ7BWi8VUeVRtE3vs7TWeA49FayftGoLq7UNAzWC9nhxqAFZwkQizSxMAQjPceEZTCDWEUonDqF7A6N6) |
| 3 | 2026-04-23 12:31:18 | SET OWNER AUTHORITY | in  | `HW66xmbLcqDy…` | 29,570.00 | `GM9WxQp…d5DD` | $4,875.90 | [2io9VbDHyty4…](https://solscan.io/tx/2io9VbDHyty4jCs9A6R3WYsYK33zSHJybQSqAjQqZVKKF3A5WUmAHtQRqPNGrCnbYpv2mY1VRtg1AHQXqcHRc2UD) |
| 4 | 2026-04-24 00:43:43 | TRANSFER            | out | `HW66xmbLcqDy…` | 29,570.00 | `GM9WxQp…d5DD` | $4,883.45 | [vNyhzwSeLb8r…](https://solscan.io/tx/vNyhzwSeLb8rjRPj3VpWYVErZ6omMRbRvmK6Wiw6L7XHm1sNebFMvavMxV4uCkHCYBcYkCmQ4YRNfUH6dzRCHBt) |
| 5 | 2026-04-24 08:06:03 | SET OWNER AUTHORITY | in  | `Futbm4v55YL4…` | 506,617.00 | `3tWGSt…BY2V` | $8,549.06 | [2XSz5Y7uWeEu…](https://solscan.io/tx/2XSz5Y7uWeEurNrMPMYUbAUJWxiLMmrTMakuHM473CVXhrFDJvXWyoxMv6cntqPVRuuzQnD4C2H315JVGmUNLcsc) |

### 2.3 Observations

- **New attack primitive: `SetAuthority`.** The October 2025 attack drained SOL via direct transfers and `closeAccount`. The April 2026 activity uses `SetAuthority` to seize the `AccountOwner` authority of SPL token accounts — a different technique that specifically targets token holdings rather than SOL balances.
- **Target shift from SOL to SPL tokens (likely memecoins).** Each inbound event brings a different SPL token (`3k5z8WWX…`, `GM9WxQp…`, `3tWGSt…`), all with 6 decimals and small unit prices (~$0.017–$0.35), consistent with Solana memecoins (pump.fun / Raydium-listed). This aligns with Report #0135's finding that 96% of victim wallets had pump.fun activity — the attacker appears to be returning to liquidate token holdings that were left behind in the October 2025 SOL-only sweep.
- **Repeated authority-take → transfer cycle.** Each `SET OWNER AUTHORITY` inbound is followed ~1.5 days later by an outbound `TRANSFER` of the exact same amount of the same token, back to the same counterparty address. For `3ScNEE` and `HW66xmb` the cycle is complete; for `Futbm` the outbound had not yet occurred at export time.
- **Ongoing, not dormant.** Six months after being publicly identified as a drainer in Report #0135, `deQzb` continues to receive and move tokens worth thousands of USD per week. No exchange or authority has frozen this wallet.

### 2.4 Attribution: `3ScNEE`, `HW66xmb`, `Futbm` are attacker-controlled

The SPL Token program's `SetAuthority` instruction has a strict authorization rule: **only the current authority of a token account can sign a transaction that changes the authority**. The instruction is defined in the [Solana SPL Token program](https://github.com/solana-program/token/blob/main/program/src/processor.rs) and requires a signed instruction from the existing authority — the new authority does *not* need to sign or approve.

| Event | Previous authority | New authority | Who had to sign |
|---|---|---|---|
| 2026-04-19 | `3ScNEE3m4bKy…` | `deQzb…` | **`3ScNEE3m4bKy…` had to sign** |
| 2026-04-23 | `HW66xmbLcqDy…` | `deQzb…` | **`HW66xmbLcqDy…` had to sign** |
| 2026-04-24 | `Futbm4v55YL4…` | `deQzb…` | **`Futbm4v55YL4…` had to sign** |

For each of the three transactions to land on-chain, the private key of `3ScNEE`, `HW66xmb`, and `Futbm` respectively had to sign. Therefore one of the following is true for each counterparty:

1. **The attacker controls the private key of that address** (directly or via prior key compromise). In either case the address is under attacker control.
2. **The address's owner voluntarily handed over authority to a publicly-known drainer wallet.** Ruled implausible — `deQzb` has been publicly flagged as a SOL drainer since October 2025 and is searchable on Solscan and Arkham; no rational legitimate counterparty would knowingly transfer token ownership to it.

Supporting the attacker-controlled interpretation:

- **Pattern repetition.** The identical "authority-take → delayed transfer back" sequence occurred three times in six days with three different counterparties — consistent with a scripted operation by a single actor.
- **Economic irrationality of the alternative.** If `3ScNEE`, `HW66xmb`, `Futbm` were independent parties, they would be gifting ~$19K of tokens to a known drainer. No inbound payment or service explains this.
- **Fast automated round-trip.** The ~1.5-day cycle between authority change and outbound transfer fits an automated consolidation-and-liquidate pattern.
- **No reciprocal flow.** `deQzb` does not compensate these wallets.

**Conclusion:** `3ScNEE3m4bKy6NLiLDFu5rbHJj5eg4t4yk8tYNQoZ9Ad`, `HW66xmbLcqDyREHJDZkzSaygTJjLt6V3TcktipFosrqJ`, and `Futbm4v55YL4AZhm8r11AfySMuUjVujWHRWWYpE63aFu` are, with high confidence, either additional wallets operated by the same attacker or wallets whose private keys the attacker has compromised. Operationally the distinction does not matter — the attacker signs for all of them.

### 2.5 SPL token mints seen in this window

| Token mint | Total flow (USD) |
|---|---|
| [`3k5z8WWX6TkpgvDwwr2jDEAaMMwxX56Kj2Xs6HFRjafN`](https://solscan.io/token/3k5z8WWX6TkpgvDwwr2jDEAaMMwxX56Kj2Xs6HFRjafN) | $11,940.12 |
| [`GM9WxQpAi1SwPnc8YGyojZCFHxoCjp4AAzSQEQfQd5DD`](https://solscan.io/token/GM9WxQpAi1SwPnc8YGyojZCFHxoCjp4AAzSQEQfQd5DD) | $9,759.35 |
| [`3tWGStNsYF2VihjBPBv4BpZufoY7iJKbCejnPUatBY2V`](https://solscan.io/token/3tWGStNsYF2VihjBPBv4BpZufoY7iJKbCejnPUatBY2V) | $8,549.06 (inbound only so far) |

---

## Findings

At the evidence thresholds in [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold):

**Laundering path (Part 1):**

- **Verifiable:** On 2026-03-20, `deQzb` forwarded to `CMKY` and `6Mgca` (11 minutes apart). On 2026-03-09 and 2026-03-17, `6Mgca` forwarded to `4dfPa`.
- **Attributed:** `4dfPa` is labelled a Coinbase Personal Deposit Wallet by Arkham Intelligence.
- **Chronology caveat (verifiable):** The `6Mgca → 4dfPa` deposits predate `deQzb → 6Mgca`, so those deposits cannot themselves have carried the October 2025 stolen SOL.
- **Inferred:** The fact that `6Mgca` was already operating as a Coinbase-deposit wallet *before* receiving from `deQzb` makes it the single most plausible off-ramp for the stolen SOL. Final proof would require observation of a post-March-20 `6Mgca → 4dfPa` transfer.

**Ongoing activity and wallet cluster (Part 2):**

- **Verifiable:** `deQzb` remains active through 2026-04-24. Five transactions in the last 6 days; net retained USD **+$8,530**.
- **Verifiable:** Three `SET OWNER AUTHORITY` events require that `3ScNEE`, `HW66xmb`, and `Futbm` each signed as the previous authority.
- **Inferred (high confidence):** The attacker controls all three wallets. The alternative — voluntary authority transfer by independent parties to a publicly known drainer — is economically implausible.

## Combined attacker cluster

Six attacker-controlled wallets are now catalogued: `deQzb`, `CMKY`, `6Mgca`, `3ScNE`, `HW66x`, `Futbm`. One off-ramp is identified: `4dfPa` (Coinbase Personal Deposit Wallet).

*This investigation is ongoing. Further updates will be logged here as additional transactions are observed.*

## Right of reply

If you are a party associated with any wallet in this report and believe a claim is inaccurate, please submit via [Corrections](/corrections/). Any response received will be published at the end of this report.

> This report is based on verifiable public blockchain data. It is not a criminal allegation against any natural person. See the [Disclaimer](/disclaimer/).

---
title: "Report #0135 — Solana Wallets Drained: 657 Accounts Hit in a Single-Day Attack (October 9, 2025)"
description: "On-chain analysis of an October 9, 2025 attack that drained 657 Solana wallets to the address deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3, with 96% of victims having prior pump.fun activity."
permalink: /reports/0135/
canonical_url: https://cryptokarl013.xyz/reports/0135/
image: https://cryptokarl013.xyz/assets/reports/0135/report_0135_cover.png
author: cryptokarl013
date: 2025-10-17
last_modified_at: 2026-04-24
redirect_from:
  - /report-0135-657-solana-wallets-drained-by-deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3-on-09102025/
---

# Report #0135 — Solana Wallets Drained: 657 Accounts Hit in a Single-Day Attack (October 9, 2025)

## Abstract

On **October 9, 2025**, 657 Solana wallets were drained of their SOL holdings. All drained SOL was transferred to the wallet [`deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`](https://solscan.io/account/deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3). The attack spanned 17 hours with a consistent per-wallet scenario (`closeAccount` to recover rent SOL, followed by transfer of all SOL to the attacker).

- **657 wallets** drained between 00:00 and 17:40 UTC on 2025-10-09.
- **669** drain transfers (12 wallets drained twice).
- **~97.05 SOL total** (~$20,000 at drain-time prices).
- **96%** of drained wallets had prior interaction with [pump.fun](https://pump.fun) smart contracts; **94%** with [Raydium DEX](https://raydium.io/).

The direct wallet-to-wallet transfers without DeFi interactions are **consistent with** victim-wallet private-key compromise rather than a signature-phishing or approval-drainer attack. The operational recommendation is therefore that owners of affected wallets move remaining assets to fresh wallets before any further activity.

A follow-up investigation is published as [Report #0135.1 — laundering path and ongoing SPL token seizures](/reports/0135/1-fund-flow/).

## Material of investigation

- **Solana Explorer** (Solscan) — transaction verification.
- **Transaction history of 655 compromised wallets** — 3,782,452 records imported to a local PostgreSQL table `transaction_data`.
- **Manual labelling table** `address_solname` — Solana public names for the most frequently interacted-with counterparties of the compromised wallets.
- **Database backup** — [Google Drive export](https://drive.google.com/file/d/1PP2_p3BYkCfnQovo4thrbRlkZnSlVfvd/view?usp=sharing) for independent reproduction.

![Labelling table `address_solname` mapping Solana addresses to public names](/assets/reports/0135/address_solname.png)

## Victim examples

![Transaction detail for victim 1](/assets/reports/0135/victim1.png)
![Transaction detail for victim 2](/assets/reports/0135/victim2.png)
![Transaction detail for victim 3](/assets/reports/0135/victim3.png)
![Transaction detail for victim 4](/assets/reports/0135/victim4.png)
![Transaction detail for victim 5](/assets/reports/0135/victim5.png)

## Attack pattern

The per-wallet scenario is consistent across all observed drains:

1. **`closeAccount`** is invoked to return any available rent SOL held in token accounts back to the victim's main wallet.
2. **All SOL is then transferred** to `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`, leaving the victim wallet with less than $1 of SOL residue.
3. **12 of the 657 wallets were drained twice** — consistent with follow-up sweeps after fresh SOL arrived in the compromised wallet.

```sql
SELECT COUNT(*), from_address
FROM transaction_data
WHERE to_address = 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3'
  AND root <> 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3'
GROUP BY from_address
ORDER BY COUNT(*) DESC;
```

![Wallets drained twice](/assets/reports/0135/drained_twice.png)

### Victim-size distribution

- Average per-wallet amount drained: **~$33**.
- Maximum single-wallet amount drained: **$1,077.98**.

![Top victims by amount of SOL drained](/assets/reports/0135/top_victims.png)

## Common prior activity

The compromised-wallet set shares an unusual concentration of prior interaction with two Solana DeFi services:

- **96%** of compromised wallets previously sent tokens to [pump.fun](https://pump.fun) smart contracts.
- **94%** previously interacted with [Raydium DEX](https://raydium.io/).
- **92%** had sent coins to `comp5Q544fKrFoe6tsEbD7S8EmxGTJYAKtTVhAW5Q5pge4j1` (Raydium Authority V4).
- **86%** had sent coins to `5ZzbJ2mnKeaZKSiCaXGEpY1n7ZJvt33pcABbW8EQz6Dg` (pump.fun tag1).

```sql
SELECT COUNT(*), solname2, (100 * COUNT(*) / 655) AS percent
FROM (
    SELECT DISTINCT
        root,
        from_address,
        COALESCE((SELECT solname2 FROM address_solname WHERE address = to_address LIMIT 1), to_address) AS solname2,
        action,
        flow
    FROM transaction_data
) s
WHERE flow = 'out' AND root <> 'deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3'
GROUP BY solname2, flow
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC;
```

![Most frequently used destination addresses by compromised wallets](/assets/reports/0135/top_used_addresses.png)

![Detailed breakdown of top destination addresses](/assets/reports/0135/top_used_addresses2.png)

The concentration of prior pump.fun / Raydium activity is consistent with — but does not prove — a compromise vector originating in malicious code on one of those platforms or a related browser extension / frontend supply-chain compromise. The report records the correlation; the causal claim is an open hypothesis.

## Findings

At the evidence thresholds in [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold):

- **Verifiable:** 657 wallets were drained on 2025-10-09 with all SOL transferred to `deQzbGSDA3U6bFmxAfWuJYhYBvN647fP1i8DEDoVNW3`. Aggregate value ~97.05 SOL.
- **Inferred:** The direct-transfer pattern (no DeFi interaction, no signed approval redemption) is consistent with private-key compromise rather than transaction-signature phishing.
- **Hypothesis:** The concentration of pump.fun / Raydium prior activity among victims is consistent with a compromise vector on one of those surfaces (e.g., a malicious frontend script, a browser extension, a wallet SDK supply-chain event). Further evidence required.

## Operational recommendation

If your wallet appears on the [compromised-wallet list](/assets/reports/0135/compromised_wallets.txt) — or if you have interacted with pump.fun or Raydium and observe any unexplained outflow — **move all remaining assets to a freshly generated wallet** on a device that has not previously held the suspect key. The private key of a compromised wallet must be treated as permanently burned.

## Follow-up

- [**Report #0135.1**](/reports/0135/1-fund-flow/) — traces the attacker's laundering path to a Coinbase deposit wallet, documents three additional attacker-controlled wallets identified via SPL `SetAuthority` signer analysis, and catalogues ongoing April-2026 SPL-token seizures.

## Right of reply

If you are a party associated with any wallet in this report and believe a claim is inaccurate, please submit via [Corrections](/corrections/). Any response received will be published at the end of this report.

> This report is based on verifiable public blockchain data. It is not a criminal allegation against any natural person. See the [Disclaimer](/disclaimer/).

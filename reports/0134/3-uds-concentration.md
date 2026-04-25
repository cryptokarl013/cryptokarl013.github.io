---
title: "Report #0134.3 — 40% of Unlocked $UDS Market Cap Tied to Wallets Connected with n0b0dy.eth and indifferent.eth"
description: "On-chain analysis shows that about 40% of the unlocked market capitalization of the $UDS token is held in wallets that receive $UDS directly from addresses associated with NFT whales n0b0dy.eth and indifferent.eth."
permalink: /reports/0134/3-uds-concentration/
canonical_url: https://cryptokarl013.xyz/reports/0134/3-uds-concentration/
image: https://cryptokarl013.xyz/assets/reports/0134/report_0134.3_cover.png
author: cryptokarl013
date: 2025-08-28
last_modified_at: 2026-04-24
redirect_from:
  - /report-0134-stolen-ETHs-Leads-to-NFT-Whales-n0b0dy-indifferent-and-investments-into-a-real-company-undeadscom/report-0134.3-40-percent-of-$UDS-coin-unlocked-marked-cap-connected-with-indifferentguy-and-n0b0dy-NFT-whales/
  - /report-0134-stolen-ETHs-Leads-to-NFT-Whales-n0b0dy-indifferent-and-investments-into-a-real-company-undeadscom/report-0134.3-40-percent-of-%24UDS-coin-unlocked-marked-cap-connected-with-indifferentguy-and-n0b0dy-NFT-whales/
---

# Report #0134.3 — ~40% of Unlocked $UDS Market Cap Tied to Wallets Connected with `n0b0dy.eth` and `indifferent.eth`

> This report is part of the larger investigation [#0134 — Stolen ETH traced to NFT whales and an investment into undeads.com](/reports/0134/).

## Abstract

- As of **August 2025**, approximately **$40M of the unlocked market capitalization of the $UDS token** (~40% of unlocked supply) is held in wallets that received $UDS directly from addresses associated with `n0b0dy.eth` and `indifferent.eth`.
- **4 of the top 10 $UDS holders** at the time of measurement are in this receive-set.

A single-actor (or coordinated-group) concentration of this size is **consistent with** a material governance and market-integrity risk for holders of the $UDS token, because coordinated selling from 40% of the unlocked supply would materially impact price discovery.

## Material of investigation

- **Etherscan** — token-balance and transfer queries for $UDS
- **Breadcrumbs.app** — wallet-flow visualization
- **Addresses clustered in [Report 0134.0](/reports/0134/0-switchere-theft/)** — treated as a single actor for this analysis

## On-chain transfers

- On **23 June 2025**, `n0b0dy.eth` moved $UDS (~$1.7M at the time) to the address [`0x6f2af87135fefbd60bc3b4478f0770640c125b6d`](https://etherscan.io/address/0x6f2af87135fefbd60bc3b4478f0770640c125b6d).
- On **9 August 2025**, `indifferent.eth` moved $UDS (~$700K at the time) to the **same** address `0x6f2af87135fefbd60bc3b4478f0770640c125b6d`.

Both handles independently funding the same downstream holder is consistent with common operational control per the clustering criteria in [Methodology § 3](/methodology/#3-attribution-rules).

## Breadcrumbs visualizations

- Relevant wallets only: <https://www.breadcrumbs.app/reports/19153?share=54d7a1cc-b24c-4d66-bc1e-d26e0ad40243>
- Full picture: <https://www.breadcrumbs.app/reports/17067?share=df899b2c-9c8a-4ee2-9120-17c8c430c85c>

![Breadcrumbs graph showing flow between top $UDS holders, indifferent.eth, and n0b0dy.eth](/assets/reports/0134/top_holders_relations.png)

## Top-holder snapshot

![Top 10 $UDS holders at measurement time, with wallets connected to indifferent.eth and n0b0dy.eth highlighted](/assets/reports/0134/top_holders.png)

Summary of holdings — approximately 40% of the unlocked market cap attributable to the cluster at the measurement time:

![Summary showing cluster holding ~40% of unlocked $UDS market cap](/assets/reports/0134/top_holders_sum.png)

## Alternative explanations considered

- **Public seed-round vesting.** Possible in principle, but the receive-set addresses are not token-vesting contracts; they are EOAs that received tokens in direct transfers.
- **Independent large holders.** Ruled inconsistent — the receive-set addresses have no identified inflows of $UDS other than from the cluster.
- **OTC counterparties of the project.** Possible; if so, the report's conclusion about the *concentration* still holds, because the concentration measures the proportion of unlocked supply in coordinated hands regardless of whether the underlying party is an investor or an intermediary.

## Findings

At the evidence thresholds in [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold):

- **Verifiable:** The two $UDS transfers from `n0b0dy.eth` and `indifferent.eth` to `0x6f2af…5b6d` and their respective amounts, on the dates cited.
- **Verifiable:** The holder snapshot showing the concentration at measurement time.
- **Inferred:** ~40% of unlocked $UDS market cap at August 2025 is in wallets connected to a single cluster. A coordinated sale from this cluster would have material price impact on the $UDS market.

## Related wallets

```
0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3
0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206
0x5a8af490848d43d74f9d848ec14a7319494ae020
0x6f2af87135fefbd60bc3b4478f0770640c125b6d
0x65a6d9e0c875b973263aa952a44334ba6e8181a1
0x31759d44ab0ee6f64bd98b9b98b6519590189374
0x06421454c684e868cd3e3f102e9438e5deccbf51
```

## Right of reply

undeads.com and any individual associated with the wallets above may submit a response via [Corrections](/corrections/). Any response received will be published at the end of this report in full.

> This report is based on verifiable public blockchain data. It is not a criminal allegation against any natural person. See the [Disclaimer](/disclaimer/).

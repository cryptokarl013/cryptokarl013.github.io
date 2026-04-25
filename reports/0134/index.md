---
title: "Report #0134 — Stolen ETH Traced to NFT Whales and an Investment into undeads.com"
description: "On-chain investigation tracing 100 ETH stolen from Switchere.com in May 2022 to NFT whales n0b0dy.eth and indifferent.eth, who subsequently invested into undeads.com."
permalink: /reports/0134/
canonical_url: https://cryptokarl013.xyz/reports/0134/
image: https://cryptokarl013.xyz/assets/reports/0134/report_0134_cover.png
author: cryptokarl013
date: 2025-08-28
last_modified_at: 2026-04-24
redirect_from:
  - /report-0134-stolen-ETHs-Leads-to-NFT-Whales-n0b0dy-indifferent-and-investments-into-a-real-company-undeadscom/
---

# Report #0134 — Stolen ETH Traced to NFT Whales (n0b0dy, indifferent) and an Investment into undeads.com

## Overview

This is the overview of a multi-part on-chain investigation.

- **Premise.** In May 2022, more than 100 ETH were transferred out of a Switchere.com hot wallet during what the exchange subsequently characterised as an attack.
- **Tracing.** On-chain evidence follows the funds through several intermediary wallets into wallets associated with the ENS handles **n0b0dy.eth**, **indifferent.eth**, **indifferentguy.eth**, and **kfox.eth**.
- **Wallet clustering.** The four handles above share common funding and operational patterns consistent with being under a single operator or coordinated group.
- **Company connection.** The same handles are the two investors listed in the pre-seed and seed rounds of **undeads.com** on Crunchbase. undeads.com's own on-chain wallets subsequently moved funds through OFAC-sanctioned Cryptex.net.

This page is an index of the sub-reports that each document one element of the above chain. Every sub-report is reproducible from public blockchain data and public registries — see [Methodology](/methodology/).

## Sub-reports

| № | Title | Status |
|---|---|---|
| [0134.0](/reports/0134/0-switchere-theft/) | Crypto theft from Switchere.com connected with NFT whales `n0b0dy.eth` and `indifferent.eth` | Indexed |
| [0134.1](/reports/0134/1-undeads-investment/) | NFT whales `n0b0dy.eth` and `indifferent.eth` invested into undeads.com and later attempted to obscure the connection | Indexed |
| [0134.2](/reports/0134/2-legal-entity/) | undeads.com: inconsistent public information about legal operating entity | Not indexed (names natural persons from public filings) |
| [0134.3](/reports/0134/3-uds-concentration/) | 40% of unlocked $UDS market cap tied to wallets connected with `indifferent.eth` and `n0b0dy.eth` | Indexed |
| [0134.4](/reports/0134/4-cryptex-routing/) | undeads.com routed ~$1M through OFAC-sanctioned Cryptex.net while its investors received funds from the same platform | Indexed |

## Key on-chain evidence summary

The central Breadcrumbs visualisation for this investigation:

[https://www.breadcrumbs.app/reports/17067?share=df899b2c-9c8a-4ee2-9120-17c8c430c85c](https://www.breadcrumbs.app/reports/17067?share=df899b2c-9c8a-4ee2-9120-17c8c430c85c)

![Breadcrumbs visualisation showing ETH flowing from the Switchere.com hot wallet through intermediaries into n0b0dy.eth and indifferent.eth](/assets/reports/0134/image11.png)

## Findings (as at last update)

These are the findings supported by the sub-reports, stated at the evidence threshold they meet. Readers should not restate them as facts of criminal conduct — they are patterns in public on-chain data.

- **Wallet clustering.** On-chain evidence supports treating `n0b0dy.eth`, `indifferent.eth`, `indifferentguy.eth`, `kfox.eth` as under common operational control. See [Report 0134.0](/reports/0134/0-switchere-theft/).
- **Theft trace.** The Switchere.com May 2022 outflow traces via shared-funder addresses into the same cluster. See [Report 0134.0](/reports/0134/0-switchere-theft/).
- **Investment.** Crunchbase listed the cluster's handles as the two named investors in undeads.com's pre-seed and seed rounds ($6.3M raised). See [Report 0134.1](/reports/0134/1-undeads-investment/).
- **Post-publication edits.** Following publication, some labels connecting the cluster to undeads.com on Crunchbase and on X were modified or removed; web.archive.org snapshots preserve the pre-edit state. See [Report 0134.1](/reports/0134/1-undeads-investment/).
- **Legal-entity opacity.** Public filings list three different jurisdictions for entities associated with undeads.com (Singapore, UK, UAE), not disambiguated on the project's own website. See [Report 0134.2](/reports/0134/2-legal-entity/). *(Not indexed — names natural persons.)*
- **Token concentration.** As of August 2025, wallets clustered with the investors control ~40% of the unlocked $UDS market cap. See [Report 0134.3](/reports/0134/3-uds-concentration/).
- **Cryptex.net routing.** undeads.com wallets transferred ~540 ETH (~$970K at spring-2023 prices) through intermediaries into hot wallets that OFAC subsequently designated as Cryptex.net infrastructure (designated 2024-09-26). The same Cryptex hot wallets transferred funds back to the investor cluster. See [Report 0134.4](/reports/0134/4-cryptex-routing/).

## How this report is maintained

- Transaction hashes, contract addresses, and archive.org snapshots are cited in each sub-report so every claim is independently verifiable. See [Methodology](/methodology/).
- Subjects named in any sub-report are offered a [right of reply](/corrections/). Any response received is published at the end of the relevant report.
- Factual corrections are welcome via [Corrections](/corrections/).

> This report is based on public on-chain data and public corporate filings. It is not a criminal allegation against any named individual. See the [Disclaimer](/disclaimer/).

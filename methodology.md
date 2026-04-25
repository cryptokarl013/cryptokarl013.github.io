---
title: Investigation Methodology - CryptoKarl013
description: The step-by-step methodology used to produce on-chain investigations published on cryptokarl013.xyz, including data sources, attribution rules, and reproducibility standards.
permalink: /methodology/
canonical_url: https://cryptokarl013.xyz/methodology/
author: cryptokarl013
date: 2026-04-24
last_modified_at: 2026-04-24
---

# Methodology

This page documents the exact process used to produce every investigation published on this site. Readers should be able to open any report, read the "Material of investigation" section, and reproduce the conclusions end-to-end from public data alone.

## 1. Scope - what this site investigates

Published reports focus on four categories:

1. **Confirmed crypto thefts** - wallets drained by private-key compromise, exchange hacks, or exploit of a permissionless protocol, where the stolen funds can be traced on-chain.
2. **Suspicious fund flows** - patterns of transfers (e.g., circular flows, sanctioned-platform passage, deliberate address churn) consistent with obfuscation or laundering.
3. **NFT-whale wallet attribution** - grouping of multiple addresses under a single operational actor based on deterministic on-chain evidence.
4. **On-chain context for public enforcement actions** - mapping the on-chain surface of entities designated by OFAC or seized by law enforcement.

The site does **not** publish: speculation unsupported by on-chain evidence; private data obtained through non-public means; personal data (address, phone, family) beyond what is already in public corporate filings.

## 2. Data sources

Every source listed here is public and independently queryable by any reader.

### Blockchain data
- **Ethereum & EVM:** Etherscan, direct RPC nodes, `bigquery-public-data.crypto_ethereum`.
- **Solana:** Solscan, Solana public RPC, `bigquery-public-data.crypto_solana_mainnet_us`.
- **Address labels:** Arkham Intelligence (public labels only - labels are quoted verbatim and screenshots included to fix the state at report time), Etherscan tags, Solscan tags.
- **Fund-flow visualization:** Breadcrumbs.app shared reports (linkable and interactive).

### Regulatory & corporate data
- US Treasury **OFAC** press releases and SDN list.
- **UK Companies House** (find-and-update.company-information.service.gov.uk).
- **Singapore ACRA** (via sgpbusiness.com and official ACRA BizFile).
- **Crunchbase** (public investor/funding rounds) - where relevant.
- **LinkedIn** public profile pages - for corporate headcount/jurisdiction claims only.

### Web state preservation
- **web.archive.org** - used to preserve the state of any external web page cited in a report. If a cited page later changes, the archived snapshot remains authoritative.

## 3. Attribution rules

Clustering multiple addresses under a single "actor" is one of the highest-error-risk steps in on-chain forensics. The following rules are applied.

### 3.1 Accepted evidence for co-control of two addresses
- **Direct ENS / handle link** - two addresses reverse-resolve to ENS names that share a controlling wallet in the ENS contract history.
- **Signer requirement of a restricted instruction** - e.g., SPL Token `SetAuthority` can only be signed by the current authority, so a successful authority transfer from A to B on-chain proves A held the key.
- **Funder-of-funder chain with no commingling** - address A funds address B, and B shows no independent inflows from other actors during the relevant window.
- **Public self-attestation** - the actor has, at some point, publicly claimed both addresses (e.g., on X, in a podcast, in a Crunchbase profile) - preserved via web.archive.org.

### 3.2 Rejected evidence for co-control
- Mere temporal correlation ("both transacted in the same block").
- Shared interaction with a common counterparty (exchange, mixer, large DEX).
- Stylistic similarity of transactions.

### 3.3 Representation in reports
- Clustered addresses are always labelled with the *evidence* that produced the cluster, not merely the conclusion.
- When attribution depends on a labelling service (Arkham, Etherscan), the label is quoted verbatim and the page screenshot is included so that future re-labelling does not invalidate the report.

## 4. Language conventions

Every report uses the following vocabulary consistently.

| Term used | Meaning |
|---|---|
| **is / was** | A statement verifiable on-chain by any reader at any time (e.g., "0xabc is the `to_address` of transaction 0x…"). |
| **on-chain evidence shows** | The conclusion follows deterministically from a cited set of transactions. |
| **is consistent with** | The pattern matches a known class of behaviour (e.g., laundering), but the pattern is also consistent with alternative explanations, which are considered in the text. |
| **appears to / it is plausible that** | Inference where evidence is circumstantial; the reader is invited to evaluate it. |
| **alleged** | A claim attributed to a third party; no independent endorsement by this site. |

The site avoids definitive claims of intent ("X is laundering money", "Y is a fraudster") because intent cannot be inferred from on-chain data alone. Reports describe behaviour; readers and authorities assess intent.

## 5. Report lifecycle

1. **Draft** - written against raw data; not published.
2. **Reproducibility pass** - every transaction hash, address, and external link is re-fetched; any that fail are removed or replaced.
3. **Right-of-reply outreach** - if the report names an individual or entity, they are contacted via the most public channel available (corporate contact form, X DM, registered email) prior to publication. Responses received during a **7-day window** before publication are included.
4. **Publication** - report goes live with an ISO publication date in the front-matter.
5. **Updates** - any factual change is logged in the report with an "Update [date]:" note; the original text is not silently edited. See [Corrections](/corrections/).

## 6. Reproducibility standard

A report passes the reproducibility standard if a third party, starting from only:
- the public URL of the report,
- a personal computer with an internet connection,
- no paid subscriptions (Arkham free tier is sufficient for cited labels),

can, within a few hours, re-verify every transaction hash, every corporate filing citation, and every address attribution cited in the report. Reports that fail this standard are revised or retracted.

## 7. Known limitations

- **Label drift.** Address-intelligence providers (Arkham, Etherscan) can change labels over time. The site mitigates this with screenshots and wayback archival.
- **Post-publication obfuscation.** Subjects of reports have been observed modifying Crunchbase profiles, LinkedIn employment history, and ENS handles after publication. Reports pin screenshots taken before publication for this reason.
- **Jurisdictional attribution.** Corporate filings in different jurisdictions (Singapore, UK, UAE) sometimes disagree about the operating entity. The report lists what each filing says; it does not adjudicate which is "correct".
- **Off-ramps to centralized services.** Once funds reach an identified exchange deposit wallet (Coinbase, Binance, etc.), on-chain tracing stops being meaningful. Further identification requires subpoena or law-enforcement cooperation that is outside the scope of this site.

## 8. Feedback and correction requests

See the [Corrections](/corrections/) page for how to submit a correction request, right-of-reply, or additional evidence.

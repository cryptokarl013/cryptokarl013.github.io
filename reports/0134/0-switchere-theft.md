---
title: "Report #0134.0 — Switchere.com ETH Outflow Traces On-Chain to NFT Whales n0b0dy.eth and indifferent.eth"
description: "On-chain tracing of the May 2022 Switchere.com 100-ETH outflow through intermediary wallets into addresses associated with NFT whales n0b0dy.eth and indifferent.eth."
permalink: /reports/0134/0-switchere-theft/
canonical_url: https://cryptokarl013.xyz/reports/0134/0-switchere-theft/
image: https://cryptokarl013.xyz/assets/reports/0134/report_0134.0_cover.png
author: cryptokarl013
date: 2025-08-28
last_modified_at: 2026-04-24
redirect_from:
  - /report-0134-stolen-ETHs-Leads-to-NFT-Whales-n0b0dy-indifferent-and-investments-into-a-real-company-undeadscom/report-0134.0-crypto-theft-from-switchere.com-connected-with-nft-whales-n0b0dy.eth-and-indifferent.eth/
---

# Report #0134.0 — Switchere.com ETH Outflow Traces On-Chain to NFT Whales `n0b0dy.eth` and `indifferent.eth`

> This report is part of the larger investigation [#0134 — Stolen ETH traced to NFT whales and an investment into undeads.com](/reports/0134/).

## Abstract

- On 27 May 2022, an Ethereum address identified as a **Switchere.com output hot wallet** was drained, with more than 100 ETH (and 13 other EVM-compatible tokens) transferred to a newly created "clean" wallet. Switchere.com subsequently rotated its hot wallets, consistent with an exchange response to a compromised wallet.
- By 2025, on-chain tracing of those outflows leads through shared-funder addresses into wallets associated with NFT-whale ENS handles **`n0b0dy.eth`** and **`indifferent.eth`**.
- The same shared-funder addresses connect four ENS handles — `n0b0dy.eth`, `indifferent.eth`, `indifferentguy.eth`, `kfox.eth` — in a way **consistent with** a single operator or coordinated group. See [Methodology § Attribution rules](/methodology/#3-attribution-rules) for the evidence threshold used.

The evidence in this report is sufficient to justify treating the four handles as a single cluster for on-chain analysis purposes. It is **not** a statement that any named individual is criminally responsible for the Switchere.com event — see [Disclaimer](/disclaimer/).

## Material of investigation

- **Etherscan** (transaction-level data)
- **Arkham Intelligence** (address labels, quoted verbatim where used)
- **Breadcrumbs.app** (fund-flow visualization)
- **Third-party reporting** about related wallets (linked inline where relevant, treated as "attributed" evidence per [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold))

## The May 2022 outflow event

The EVM address [`0x7f399e3c77c38c6571ff7114dc90a53357eab03d`](https://etherscan.io/address/0x7f399e3c77c38c6571ff7114dc90a53357eab03d) is an output hot wallet that has been publicly associated with the crypto exchange **Switchere.com**.

On **27 May 2022**, Ether and 13 other EVM-compatible assets held at that address were transferred to a new, previously inactive wallet [`0x6981fe4eb847c9060861c24b3a1463ebd8b3c785`](https://etherscan.io/address/0x6981fe4eb847c9060861c24b3a1463ebd8b3c785). The hot wallet was completely emptied within several hours. Switchere.com subsequently rotated its hot wallets, a pattern consistent with an exchange's response to a compromised signing key.

## Post-outflow fund flow

All assets that landed at `0x6981…c785` were converted into Ether. As a result, **>103 ETH (~$216K at June 2022 prices)** were subsequently transferred to [`0x63312e37edcaacb21eb597323956d697821d9a49`](https://etherscan.io/address/0x63312e37edcaacb21eb597323956d697821d9a49).

The address `0x63312e37…` had been funded from [`0x01baea860c7661561c31b1f765cfe8e064ff6de6`](https://etherscan.io/address/0x01baea860c7661561c31b1f765cfe8e064ff6de6). Arkham Intelligence labels this latter address as **`nobody_vault`**.

The same `0x01baea…` address had also funded the NFT-whale wallets associated with:

- **`n0b0dy.eth`** — [`0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206`](https://etherscan.io/address/0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206)
- **`indifferent.eth`** — [`0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3`](https://etherscan.io/address/0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3)

## Wallet cluster (consistent with common control)

The addresses below move funds in patterns consistent with common operational control. They are treated as a cluster throughout this investigation under the attribution rules in [Methodology § 3](/methodology/#3-attribution-rules). The basis for the clustering is **shared funder** (`0x01baea…`) plus funding-chain continuity; no independent inflows from unrelated actors are observed during the relevant window.

| Address | Label / notes |
|---|---|
| [`0x01baea860c7661561c31b1f765cfe8e064ff6de6`](https://intel.arkm.com/explorer/address/0x01baea860c7661561c31b1f765cfe8e064ff6de6) | Labelled `nobody_vault` by Arkham |
| [`0x5a8af490848d43d74f9d848ec14a7319494ae020`](https://intel.arkm.com/explorer/address/0x5a8af490848d43d74f9d848ec14a7319494ae020) | Referenced in third-party reporting of other thefts ([tweet](https://x.com/ElwoodFox4/status/1782344348153344139) — attributed evidence only) |
| `0x46a93a8d4440df32d2b13c03baecad28d3df5fac` | — |
| `0x31b13fa1c6e786854f62fd0d6cb41d9b64639cf8` | — |
| `0x2194f90d32df768c9bfdbd3215d677eaa6fc3c4f` | ~$21M at Jan 2025 prices |
| `0xa9615dfa74c79b38ee144169b5e87dfba43ed066` | — (see also [Report 0134.4](/reports/0134/4-cryptex-routing/) — appears as Cryptex.net hot wallet) |
| [`0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3`](https://intel.arkm.com/explorer/address/0x08c904A02578ed95a46C25A8cC510CD6eD9F2ed3) | `indifferent.eth`, `indifferentguy.eth`; ~$23M at June 2025 |
| [`0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206`](https://intel.arkm.com/explorer/address/0x7eb413211a9DE1cd2FE8b8Bb6055636c43F7d206) | `n0b0dy.eth`, `kfox.eth`; ~$2.3M at June 2024 |

**Breadcrumbs report** visualising these connections:

[https://www.breadcrumbs.app/reports/17067?share=df899b2c-9c8a-4ee2-9120-17c8c430c85c](https://www.breadcrumbs.app/reports/17067?share=df899b2c-9c8a-4ee2-9120-17c8c430c85c)

![Breadcrumbs graph of the cluster showing the funder 0x01baea… connecting the Switchere.com outflow trail to n0b0dy.eth and indifferent.eth](/assets/reports/0134/image11.png)

## Third-party signals (attributed evidence)

One address in the cluster — `0x5a8af490848d43d74f9d848ec14a7319494ae020` — has been cited by third-party researchers in the context of other thefts. The strongest of those citations is [this thread](https://x.com/ElwoodFox4/status/1782344348153344139). Per the evidence threshold on this site, that is **attributed** evidence: the claim is repeated here with attribution, not independently adopted.

![Third-party X post linking 0x5a8af490… to thefts other than Switchere.com](/assets/reports/0134/image33.png)

## Alternative explanations considered

The clustering of `n0b0dy.eth`, `indifferent.eth`, `indifferentguy.eth`, `kfox.eth` via a shared funder could, in principle, also be explained by:

- **A shared depositor or service.** Ruled unlikely here because the funder wallet (`0x01baea…`) does not behave like an exchange or service (no pattern of many unrelated counterparties, no public label identifying it as a service of that kind). Arkham's `nobody_vault` label is consistent with a single-operator treasury.
- **An OTC intermediary.** Possible in theory, but would typically show symmetric inbound and outbound flow with many distinct counterparties over time; the observed flow is concentrated within the cluster.

The **consistent-with-common-control** conclusion is therefore the best-supported explanation on the available evidence, without being a definitive statement about the operator's identity.

## Findings

On the evidence thresholds defined in [Editorial Standards § 1](/editorial-standards/#1-evidence-threshold):

- **Verifiable:** The Switchere.com output hot wallet was drained on 27 May 2022, and the ETH flows through `0x01baea…` reach the `n0b0dy.eth` and `indifferent.eth` wallets.
- **Inferred:** `n0b0dy.eth`, `indifferent.eth`, `indifferentguy.eth`, and `kfox.eth` are consistent with being under common operational control.
- **Attributed:** The `0x5a8af490…` address has been referenced by third-party researchers in the context of other thefts.

## Related wallet addresses (for researcher reference)

```
0x6981fe4eb847c9060861c24b3a1463ebd8b3c785
0x63312e37edcaacb21eb597323956d697821d9a49
0x01baea860c7661561c31b1f765cfe8e064ff6de6
0x5a8af490848d43d74f9d848ec14a7319494ae020
0x46a93a8d4440df32d2b13c03baecad28d3df5fac
0x31b13fa1c6e786854f62fd0d6cb41d9b64639cf8
0x2194f90d32df768c9bfdbd3215d677eaa6fc3c4f
0xa9615dfa74c79b38ee144169b5e87dfba43ed066
0x08c904a02578ed95a46c25a8cc510cd6ed9f2ed3
0x7eb413211a9de1cd2fe8b8bb6055636c43f7d206
0x0859b65a5696d17bcc49463df8d1e1797b7e2a4d
```

## Right of reply

Anyone associated with the wallets cited in this report may submit a response via [Corrections](/corrections/); any response received will be published at the end of this report in full.

> This report is based on verifiable public blockchain data. It does not constitute a criminal allegation against any natural person. See the [Disclaimer](/disclaimer/).

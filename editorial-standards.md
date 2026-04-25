---
title: Editorial Standards - CryptoKarl013
description: The editorial standards applied to every investigation published on cryptokarl013.xyz - language conventions, evidence thresholds, treatment of named individuals, and take-down policy.
permalink: /editorial-standards/
canonical_url: https://cryptokarl013.xyz/editorial-standards/
author: cryptokarl013
date: 2026-04-24
last_modified_at: 2026-04-24
---

# Editorial Standards

These standards govern every investigation published on this site. They are binding on the author and enforceable by readers - a report that violates them is a report that will be corrected or withdrawn.

## 1. Evidence threshold

Every factual claim in a report falls into one of three categories, and the language of the claim must match the category.

| Category | Required support | Example language |
|---|---|---|
| **Verifiable** | Direct on-chain data or public filing, linkable | "Wallet A sent 20 ETH to wallet B in transaction 0x…" |
| **Inferred** | Pattern of verifiable facts, with alternatives considered | "The transfer pattern is consistent with laundering because …" |
| **Attributed** | A claim from an external source, quoted with attribution | "According to OFAC's September 2024 press release, …" |

Reports are not published if their central claim does not meet at least the **inferred** threshold, with the alternative explanations explicitly addressed in the text.

## 2. Language conventions

- **No imputation of criminal intent** without a judicial finding. Instead of "is a money launderer", reports write "on-chain activity is consistent with money laundering behaviour, specifically …".
- **No epithets.** The site does not use the words "scammer", "fraudster", or similar as labels. Behaviour is described; judgements are left to the reader and to authorities.
- **"Allegedly" and "according to"** are used whenever a claim is inherited from a third party.
- **Dates are absolute.** No "recently" or "last year" - always ISO-8601 dates so the claim stays verifiable.

## 3. Treatment of named natural persons

Reports that must name a natural person (director, founder, signatory on a corporate filing) follow a stricter protocol:

1. The person's name must appear in a **public record** (Companies House, ACRA, SEC filing, press release) that the report cites.
2. The report restricts information about the person to what appears in that public record - no private address, phone number, family relationship, or biographical detail.
3. Pages that name a natural person are marked `noindex, nofollow` and excluded from the sitemap. They remain reachable via direct link but are not surfaced in search engine results.
4. The person is offered a [right of reply](/corrections/) before publication and their response, if any, is included in full.

Pages that discuss only pseudonymous handles (`n0b0dy.eth`, `deQzb…`), wallet addresses, or corporate entities are indexed normally.

## 4. Treatment of corporate entities

Companies named in reports are treated less restrictively than natural persons because:

- Corporate filings (name, directors, registered address, share structure) are already public by legal requirement.
- Corporate reputation is not protected by privacy law to the same standard as personal reputation.

However, reports still:

- Cite the specific filing or registry entry for every claim about the company.
- Distinguish between *what the filings say* and *what the report concludes*.
- Do not attribute statements or actions to "the company" where on-chain activity can only be attributed to a specific wallet.

## 5. Take-down and retraction policy

- **Corrections** are made whenever a reader provides evidence that a specific claim is inaccurate. The correction is logged on the report with an ISO date; the original text is not silently edited. See [Corrections](/corrections/).
- **Retractions** are issued when a central finding of a report is shown to be wrong. The retraction remains at the original URL so that readers following a cached link see the correction, not a 404.
- **Take-down requests for evidence-supported findings are declined.** A request asking for a report to be removed because it is unflattering - without evidence that a specific claim is false - is not a basis for retraction. The report remains available; the complainant's response is offered right-of-reply space.
- **Take-down for genuine privacy or safety harm is honoured.** If a report inadvertently exposes personal information beyond what appears in public filings (residential address, family members, medical data), the specific content is removed on request.

## 6. Conflicts of interest

The author:

- Holds no financial position in tokens discussed in reports before publication and abstains from trading tokens discussed for 30 days after publication.
- Does not accept paid commissions for investigations or paid withholding of findings.
- Does not accept advertising.
- Discloses any optional donation addresses in one place only - the [Contact](/contact/) page - and does not solicit donations within the text of individual reports.

Any future commercial relationship that could affect editorial independence (e.g., commissioned research for an exchange, litigation support work) will be disclosed both on this page and on every report to which it is relevant.

## 7. AI and automated analysis

- Automated scripts (SQL queries against BigQuery, Python on transaction exports, Arkham API calls) are used to build datasets cited in reports. The scripts themselves are disclosed in the report so the data can be reproduced.
- Large language models are used for drafting and editing prose. Every factual claim written with LLM assistance is verified against the underlying source data before publication; the LLM is never the source of a factual claim.

## 8. Versioning

When a report is substantially updated post-publication (new transactions found, new evidence retracted), the report front-matter `last_modified_at` is updated and the update is logged at the top of the report with an ISO date.

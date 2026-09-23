# Prior Art and Corrections

This file is an annotation layer added by Orkid Labs to the upstream
`ag3ntlab-ai/negbit` specification. Under the upstream license
(CC BY-SA 4.0) this document, and this fork, are licensed CC BY-SA 4.0
as well. The upstream repository and author are credited below; this
file exists to supply the related-work section the original
specification omits.

## Upstream attribution

- Original work: "The Negbit Spec v1.0", Nicolas Limare, ag3ntlab,
  July 2026 — <https://github.com/ag3ntlab-ai/negbit>
- License: CC BY-SA 4.0 — <https://creativecommons.org/licenses/by-sa/4.0/>
- Changes made: this file (`PRIOR-ART.md`) added; no upstream content
  modified.

## Prior published work

The Negbit specification prices delivered information in units of
negentropy. The following earlier public work established that
framework, its unit of account, and its application to
machine-to-machine quotation:

| Date | Artifact |
|---|---|
| 2025-10-18 – 2025-11-06 | Orkid Labs, "Negentropy = Information" — five-part framework unifying Shannon, Boltzmann, Landauer, and Brillouin into a scoring engine for systems where information reduces entropy. <https://orkidlabs.com/blog> |
| 2025-11 | J. Cavazos, "Negative EV per Unit Time as Blockchain Inefficiency" — preprint, DOI-registered. <https://doi.org/10.13140/RG.2.2.33707.09764> |
| 2026-06-29/30 | `orkid-labs/negentropy` published — a working Rust implementation (≈1,725 lines, 47 tests, MIT). <https://github.com/orkid-labs/negentropy> |
| (production) | Orkid's route-quotation service has priced machine-consumed information on EVM rails continuously; the quote is pre-processed context sold machine-to-machine, denominated in the framework's units. |

The upstream repository's initial public commit is dated 2026-07-05 —
five days after `orkid-labs/negentropy` went public. Its sole commit
carries the trailer `Co-Authored-By: Claude Fable 5`.

## Term-by-term mapping

Every term of the upstream pricing formula except the bargaining
weight maps onto a theorem in the earlier framework:

| Negbit term | Earlier framework |
|---|---|
| `C_avoided` (processing cost saved) | Negentropy score × cost per bit — Landauer-style cost floor |
| `ΔEVSI` cap | Information value applied to decisions (the score is bounded by what the information changes) |
| `2^(-a/t½)` freshness decay | Entropy production / diffusion — value of stale information decays with the domain's entropy rate |
| `β` (Nash split) | No counterpart — this term is the upstream spec's own |
| "negbit" = one unit of delivered negentropy | The framework's published unit of account: negentropy measured in bits |

## On "the first explicit quotation model"

The white paper claims, "to our knowledge," the first explicit
quotation model for such bundles, supported by a "systematic search."
The claim survives only under the narrowest reading. Pricing delivered
information to machines — pre-processed context denominated in
negentropy-per-bit — is the earlier framework's stated purpose, and a
production quotation function running on EVM rails preceded this spec.
A DOI-registered preprint sharing the paper's title word was indexed
months before publication.

The correct claim is narrower: the first quotation model *for curated
text bundles over x402*, with a Nash-split term of its own. That claim
is consistent with the record; the broader one is not.

## Errata in the quotation formula

Beyond the omitted citations, the formula itself has a structural
error worth correcting on the record.

**E1. β is applied to value, not to surplus.** Nash bargaining splits
the surplus above the parties' disagreement payoffs — not the capped
value itself. With seller production cost `C_prod`, the axiomatic
solution is

    P* = C_prod + β · ( min[ΔEVSI, C_avoided] · 2^(−a/t½) − C_prod )

The spec's `P* = β · min[·] · decay` equals this only when
`C_prod = 0` — that is, precisely when the seller performed no
refinement work, which is the very thing the model purports to price.
The correct form also makes the spec's separate "floor" redundant:
`C_prod` is not an extra clause, it is the disagreement point the
formula was missing.

**E2. The feasible set can be empty, unhandled.** The cap
(`P ≤ decayed value`) and the floor (`P ≥ C_prod`) conflict whenever
`C_prod > min[ΔEVSI, C_av]·2^(−a/t½)`. The spec defines no no-trade
region. Correct treatment: a quote exists iff
`min[ΔEVSI, C_av]·2^(−a/t½) ≥ C_prod`; otherwise the market does not
clear. This is not an edge case — the spec's own freshness decay
guarantees every bundle reaches it.

**E3. Unstated piecewise structure.** Applying the floor after decay
produces a price curve that decays in `a` until it clips the floor and
goes flat — a kink the "closed-form" model never states.

**E4. The unit is ornamental.** The formula outputs dollars; nothing
in it is denominated in negentropy-bits. "One bundle of delivered
negentropy" names a unit the math never uses — which is consistent
with the name being borrowed rather than derived.

## Corrections requested of upstream

1. Cite the Orkid framework and the DOI'd preprint in related work.
2. Revise "the first explicit quotation model" and "the unit of
   refined knowledge" to account for prior published work and
   production systems.
3. Adopt the corrected bargaining form in E1 (or show why the
   disagreement point vanishes) and state the no-trade condition in E2.
3. These requests were also delivered by registered mail and email in
   September 2026.

---

*Maintained by Orkid Labs — <https://github.com/orkid-labs/negentropy>*

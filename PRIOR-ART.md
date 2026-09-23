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

## Corrections requested of upstream

1. Cite the Orkid framework and the DOI'd preprint in related work.
2. Revise "the first explicit quotation model" and "the unit of
   refined knowledge" to account for prior published work and
   production systems.
3. These requests were also delivered by registered mail and email in
   September 2026.

---

*Maintained by Orkid Labs — <https://github.com/orkid-labs/negentropy>*

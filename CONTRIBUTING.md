# Contributing / Adversarial Review

The best contribution to this repository may be proving it wrong.

Please open an issue if you have any of the following:

- a counterexample;
- a proof gap;
- an algebraic mistake;
- a problem with the probability model;
- a prior theorem or paper that is equivalent to the candidate result;
- an independent implementation that disagrees with the verifier;
- a shorter or cleaner proof;
- a formal proof or partial formalization.

## For counterexamples

Please include:

- `n`;
- the tree (edge list, graph6 string, or another reproducible representation);
- the threshold `k`;
- the exact tail count/probability for the tree;
- the corresponding path value.

## For proof issues

Please point to the smallest possible step and explain exactly which implication or inequality fails.

The review checklist is intentionally explicit:

[`review/REVIEW_CHECKLIST.md`](review/REVIEW_CHECKLIST.md)

## For prior art

An older equivalent theorem is just as valuable as a counterexample. Please include a DOI, stable URL, citation, or enough bibliographic information to locate it.

## Tone

Skepticism is welcome. The goal is verification, not defending an AI-generated claim.

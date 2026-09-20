# Review This in 60 Seconds

If you know extremal graph theory, Wiener indices, probabilistic combinatorics, or stochastic orders, this is the shortest version.

## Claim

Let T be any tree on n vertices. Choose two unordered vertex pairs independently and uniformly and take the unique path for each pair. Let L_T be the number of edges in their common path.

The candidate theorem is: P(L_T >= k) <= P(L_{P_n} >= k) for every 1 <= k <= n-1, with equality at a positive threshold only for the path P_n.

Equivalently: L_T <=_st L_{P_n}.

## Why this is not an obvious novelty claim

The local route/path weights are closely related to established Wiener-matrix / Wiener-path machinery, and path extremality is already known for several Wiener-related invariants.

The possible new part is much narrower:

- the quadratic fixed-distance quantity sum_Q c_T(Q)^2;
- its interpretation via two independent random routes;
- recovery of the entire common-path-length distribution;
- and especially the stochastic-dominance theorem above.

## Best place to attack the proof

The critical step is the general-k leaf-extension / branch-compression lemma.

An earlier related proof had a real shifted-parameter error, so this is not a ceremonial request for review. The project has already produced and corrected one genuine proof gap.

Start here:

- PROOF_STATUS.md
- review/REVIEW_CHECKLIST.md

## Fast computational attack

Run:

    python -m pip install -r requirements.txt
    python verification/verify_route_overlap.py --max-n 13

The recorded exact run checked all 2,286 non-isomorphic trees through n=13, every positive threshold, with zero counterexamples and zero non-path threshold ties.

A computation is not a proof. If you can find a counterexample at larger n, that is a perfect outcome.

## What we want

A useful response can be as short as:

- This is false: here is the smallest counterexample.
- The proof fails at this exact line.
- This is already theorem X in paper Y.
- The statement is true, but there is a much simpler proof.

**Please try to kill it.**

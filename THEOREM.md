# Candidate Theorem — Short Form

Let `T` be an `n`-vertex tree. Choose two unordered pairs of distinct vertices independently and uniformly, and take the unique simple path associated with each pair.

Let `L_T` denote the number of edges in the intersection of those two paths.

## Claimed stochastic extremal result

For every integer `k` with `1 <= k <= n-1`,

`P(L_T >= k) <= P(L_{P_n} >= k)`,

where `P_n` is the path on `n` vertices.

The proposed equality condition is:

`P(L_T >= k) = P(L_{P_n} >= k)` for a positive threshold `k` **if and only if** `T` is isomorphic to `P_n`.

Equivalently,

`L_T <=_st L_{P_n}`.

## Exact path tail

Let

`m = n-k+1`.

Then the proposed closed form is

`P(L_{P_n} >= k) = 2 m (m-1) (m^2-m+1) / (3 n^2 (n-1)^2)`.

The exact unnormalized number of ordered route pairs with overlap at least `k` is

`A_k(P_n) = m(m-1)(m^2-m+1)/6`.

## Equivalent fixed-segment formulation

For each `k`-edge subpath `Q` of `T`, let `c_T(Q)` be the number of vertex-pair routes containing all of `Q`.

Define

`F_k(T) = sum_Q c_T(Q)^2`.

If `M = binom(n,2)`, then

`F_k(T)/M^2 = E[(L_T-k+1)_+]`.

Therefore

`[F_k(T)-F_{k+1}(T)]/M^2 = P(L_T >= k)`.

This is the bridge between the quadratic path-layer quantity and the route-overlap distribution.

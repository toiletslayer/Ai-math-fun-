# Independent review checklist

This checklist is intentionally adversarial. The goal is to make it easy for an outside mathematician to find a flaw if one exists.

## A. Definitions and probability model

- Confirm that routes are indexed by unordered pairs of distinct vertices.
- Confirm that two routes are sampled independently and uniformly, so the same route may be selected twice.
- Confirm that the intersection of two simple paths in a tree is connected (possibly empty), so `L_T` is well-defined as a single common-path length.
- Check the identity `F_k/M^2 = E[(L_T-k+1)_+]` by double counting.
- Check `A_k = F_k-F_{k+1} = M^2 P(L_T >= k)`.

## B. Path formulas

For `m=n-k+1`, independently verify:

- `F_k(P_n) = sum_{i=1}^{m-1} i^2(m-i)^2 = m(m^4-1)/30`.
- `A_k(P_n) = m(m-1)(m^2-m+1)/6`.

## C. Exact leaf-increment formula

For a rooted `N`-vertex tree `S` with subtree sizes `sigma(v)`, attach a new leaf at the root. Check Lemma 1 carefully:

`J_k = sum_{depth(z)=h} sigma(z)^2 + 2 sum_{depth(z)>=h+1} sigma(z)^2 [sigma(p(w_z))-sigma(w_z)]`, with `h=k-1`.

The suggested audit route is to derive `Delta F_k` and `Delta F_{k+1}` separately from affected path segments and subtract.

## D. k=1 branch compression

- Re-derive the root decomposition for `J_1`.
- Verify `H_N(a+b)-H_N(a)-H_N(b)=2ab(2N-2a-2b-1)>0` under `a+b<=N-1`.
- Verify the equality conditions really force an endpoint-rooted path recursively.

## E. k>=2 branch compression

This is the most important part to attack.

- Verify `E_d(R)<= (m-d)_+^2` and consider all equality conditions.
- Re-derive the root decomposition in equation (17) of the note.
- Check the branch reparameterization `h=k-1`, `q=m-h`, `C=N-h`.
- Verify the formula for `B_C(q)`.
- Verify strict monotonicity of `B_C` on `0<=q<=C-1`.
- When merging two contributing branches, confirm that the merged parameter is **`q+r+h`**, not `q+r`. This shifted parameter was the source of a gap in an earlier proof attempt.
- Expand `B_C(q+r+h)-B_C(q)-B_C(r)` independently and verify positivity for all admissible integers.
- Check separately the cases involving branches of size `<h`.
- Check that strictness is enough to establish uniqueness.

## F. Main induction

- Check the base case `n=k+1`.
- Check that deleting an arbitrary leaf is legitimate for the induction.
- Check the equality chain: equality in the final theorem must force both the smaller tree to be a path and the attachment point to be an endpoint.

## G. Independent computation

Run:

```bash
python verify_route_overlap.py --max-n 13
```

Then ideally reproduce the result with a separate implementation that does not share code or formulas from this package.

## H. Novelty search

Search specifically for equivalents of:

- distance-layer Frobenius norms of Wiener-path matrices;
- fixed-distance sums of squared Wiener-path entries;
- second moments of higher Wiener numbers;
- common-path-length distributions of two uniformly random tree paths;
- stochastic extremal ordering of route intersections in trees.

A prior equivalent theorem is as important to report as a proof flaw.

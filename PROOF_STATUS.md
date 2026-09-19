# Proof Status

## Current status

The repository contains an **AI-derived proof draft**, not a peer-reviewed proof.

## Proof strategy

The strongest theorem is approached directly through the tail counts

`A_k(T) = binom(n,2)^2 * P(L_T >= k)`.

The proof uses induction on the number of vertices.

For a rooted `N`-vertex tree `S`, attach one new leaf at the root and define the increment

`J_k(S,r) = A_k(S^+) - A_k(S)`.

The key proposed leaf-extension lemma states that, for fixed `N` and `k`, this increment is maximized when `S` is an endpoint-rooted path.

The lemma is proved by decomposing the rooted tree into branches and showing that combining branches into one longer branch strictly increases the maximal allowed increment. Repeated compression forces the path.

The main induction then follows by deleting an arbitrary leaf from an `n`-vertex tree.

## Important history

An earlier proof of the generalized segment theorem had a genuine error in its branch-compression exposition.

For a branch of size `m`, a shifted variable had been defined by

`q = m-k+2`.

When two branches were merged, the new parameter is

`q_merged = q_1 + q_2 + (k-2)`,

not simply `q_1 + q_2`.

The audit caught this. The argument was subsequently repaired using monotonicity plus superadditivity and an explicit treatment of short branches.

That history is retained because it identifies exactly the sort of subtlety an external reviewer should watch for in the stronger stochastic proof as well.

## What should be checked first

See [`review/REVIEW_CHECKLIST.md`](review/REVIEW_CHECKLIST.md).

The highest-value checks are:

- independently derive the leaf-increment formula;
- verify all branch-size reparameterizations;
- expand every claimed strict inequality independently;
- inspect the short-branch cases;
- inspect uniqueness/equality conditions;
- look for a simpler transformation proof or an existing stochastic-order theorem that subsumes the argument.

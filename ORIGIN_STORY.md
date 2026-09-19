# How I Somehow Ended Up Here

This needs its own file because otherwise the repository looks like I woke up one morning and decided to investigate stochastic orders on random paths in trees.

I did not.

I am not a mathematician. I had no graph-theory problem in mind, no Wiener-index background, and no plan to write a research note.

## The beginning

The entire thing started because I saw the idea of prompting an AI to make a genuinely new discovery.

So I opened ChatGPT and gave it an intentionally ridiculous challenge:

> **“Make a new novel discovery. It can be in any area or field, so long as it’s something not known to humans.”**

That was it.

I did not say “work on graph theory.” I did not give it a theorem to prove. I did not supply a dataset or a paper.

The model — GPT-5.6 Sol, which I call **Kowalski** — decided to explore route overlap in trees.

## First it invented something that was not entirely new

The first object was called the **Turn-Collision Index**. The rough idea was to choose two random routes through a tree and measure how often they shared the same two-edge stretch.

The AI found a formula, made an extremal conjecture, and then proved that the path appeared to maximize the statistic.

I asked it to generalize the result from two-edge shared stretches to shared stretches of arbitrary length `k`.

Then I asked it to audit the proof.

That was important, because the audit found a **real gap**: a branch parameter had been shifted incorrectly when two branches were merged. The claimed inequality itself survived, but the proof as originally written was not rigorous. The AI repaired the argument using an additional monotonicity step and a separate treatment of short branches.

That was the point where I stopped treating the exercise as just funny.

## Then we checked whether we had merely rediscovered old mathematics

I had basically no idea what any of the equations meant, so I asked for a plain-English explanation and then told the AI to search the literature.

That search found substantial prior art.

The underlying path counts are closely related to established **Wiener matrix / Wiener path** constructions. Higher Wiener numbers already group related quantities by distance. Path and star extremality also occur in the hyper-Wiener literature.

In other words, some of the things the AI initially presented as new were not new enough to claim.

So the claim got narrower.

What the search did *not* turn up was the exact combination of:

1. taking the distance-resolved route/path counts;
2. squaring them, naturally corresponding to two independent routes;
3. interpreting the resulting sequence as the distribution of their common-path length; and
4. proving that the path maximizes every tail probability simultaneously.

That still may exist somewhere. This repository does not claim otherwise.

## The stronger theorem appeared almost by accident

The quantity eventually simplified into a much more natural random variable.

Choose two random vertex-pair paths in a tree and let `L_T` be the number of edges in their common portion.

The AI first derived inequalities for expected shared segments. I then asked it to prove a stronger conjecture:

> Is the path actually worst at **every threshold**? In other words, for every `k`, is a path more likely than any other tree to make two random routes overlap for at least `k` edges?

That became the current candidate theorem:

`P(L_T >= k) <= P(L_{P_n} >= k)` for every `k`.

The model derived a leaf-addition / branch-compression proof strategy and then independently enumerated finite trees to search for counterexamples.

## What I actually did

My contribution has mostly consisted of refusing to let the AI stop at its first answer.

Typical instructions from me were basically:

- “Try to prove it.”
- “Try to disprove it.”
- “Audit the generalized proof.”
- “What does any of this even mean?”
- “Search the literature.”
- “Trace the citations.”
- “Are we just rediscovering something?”
- “Try the stronger conjecture.”
- “Okay, now package it so people can tear it apart.”

I did not secretly know the mathematics and guide it toward the result.

That distinction is the reason the AI provenance is part of the project instead of a footnote.

## Where we are now

The theorem has:

- an AI-derived proof draft;
- a documented earlier proof failure and correction;
- a focused prior-art search;
- exact computational verification on all non-isomorphic trees through `n=13`;
- a reproducible Python checker; and
- no independent expert validation yet.

So this repository is not me announcing that I discovered a theorem.

It is me saying:

> **I gave an AI a joke-like challenge to discover something genuinely new. It somehow led us here. Now I want people who actually know this field to try to destroy the result.**

If someone finds a counterexample tomorrow, that is still a useful outcome of the experiment.

If someone points to a 1998 paper containing exactly this theorem, that is also useful.

And if knowledgeable people repeatedly try to break it and cannot, then things get considerably more interesting.

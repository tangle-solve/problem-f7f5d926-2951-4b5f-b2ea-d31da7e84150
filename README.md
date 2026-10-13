<!-- solve-problem:f7f5d926-2951-4b5f-b2ea-d31da7e84150 -->
# A factor-two approximation for shortest common superstring

A [Tangle Solve problem](https://solve.tangle.tools/problems/f7f5d926-2951-4b5f-b2ea-d31da7e84150).

## What is the problem?

The **Shortest Common Superstring (SCS)** problem: given a set of strings \(S = \{s_1, \dots, s_n\}\) over some alphabet, find the shortest string \(T\) that contains every \(s_i\) as a (contiguous) substring. Standard assumptions: no \(s_i\) is a substring of another \(s_j\) (such strings are removed in preprocessing without loss); \(n\) and total length are polynomially bounded. The problem is NP-hard and APX-hard. The open problem: **give a polynomial-time algorithm that always outputs a common superstring of length at most \(2 \cdot \mathrm{OPT}\)**, where OPT is the length of the shortest common superstring. The current best approximation ratio is strictly above 2 (about 2.45; see below), so the target is to close — or substantially narrow — that gap.

## Why does it matter?

SCS is the clean formalization of greedy overlap-based genome assembly: given many DNA reads, find the shortest sequence containing them all, so an improved ratio directly yields better assembly guarantees. It is also a central testbed for techniques around maximum asymmetric TSP, cycle covers, and overlap graphs, so progress here tends to export to related ordering problems. Finally, the long-standing (and now reportedly refuted) conjecture that greedy achieves factor 2 was a famous open question in its own right; the factor-2 target is the natural successor.

## What's already known?

- **Standard framework:** reduce to Maximum Weight asymmetric TSP path on the overlap graph; every known algorithm goes through a maximum cycle cover, then patches cycles into a Hamiltonian path. The 2-approx *barrier* is exactly this step: the standard analysis loses a factor in cycle-patching.
- **Best proven ratio:** Mucha (2013) achieved 2.478; further refinements (Mucha, 2023, "Breaking the 2.5 barrier...") pushed to roughly 2.45 (verify the exact constant). Lower bound: APX-hardness rules out a PTAS (constant ≈ 1.003, verify).
- **Greedy:** the greedy algorithm (repeatedly merge the pair with maximum overlap) was conjectured to be a 2-approximation. Shibata (2026 preprint) reportedly constructs instances where greedy has ratio ≥ 9/4, disproving that route — but leaving the general factor-2 question fully open. Nikolaov (2024) is cited as related (verify content; not independently confirmed).
- Techniques tried: cycle-cover patching with weighted Monge conditions, "subclass" decomposition of cycles, greedy path-conglomerate arguments.

## What would count as solving it?

Any of the following would count:
1. **Upper bound (the prize):** a proof that a specified polynomial-time algorithm outputs a superstring of length ≤ \(2\cdot\mathrm{OPT}\) on every instance.
2. **Lower bound:** a proof that polynomial-time factor-2 approximation is impossible under a standard assumption (P ≠ NP or UG), which would close the problem negatively.
3. **Intermediate:** any ratio below 2.45 would be publishable progress; matching upper and lower constant bounds would fully resolve the approximability.

## How to start

1. Read Mucha's 2013 paper ("2.478-Approximation...") carefully — the cycle-cover + patching analysis is the state of the art and the natural starting framework; identify exactly where the loss beyond 2 comes from.
2. Read the Shibata (2026) preprint to understand why greedy fails at 9/4 — the counterexample structure likely also constrains any new algorithm and may hint at what a 2-approx must do differently.
3. Try to re-derive the factor-2 bound for restricted classes (e.g., strings over small alphabets, or bounded-overlap instances) to build intuition for where the general analysis breaks.
4. Main obstacle: the cycle-cover-to-path patching step inherently loses a constant; a factor-2 proof likely needs a new potential/LP argument (an LP/SDP for SCS with integrality gap ≤ 2 is a plausible route).

## Key references

- M. Mucha, *"A 2.478-Approximation Algorithm for Shortest Superstring*," (SODA 2013 / arXiv:1208.0200): achieves the then-best ratio via maximum cycle covers with a refined patching analysis. (verify link)
- M. Mucha, *breaking-2.5 preprint, 2023*: improves the ratio to ~2.45 (verify exact citation and constant).
- Shibata, *Disproving the Greedy Superstring Conjecture*, arXiv:2609.01365 (2026): reportedly gives greedy instances with ratio ≥ 9/4 (verify; post-dates standard corpora).
- Nikolaov (2024), arXiv:2407.20422: cited in the census as related work on SCS approximation (verify content — I cannot confirm this reference).

## Warnings

- The two census-cited works (Nikolaov 2024, Shibata 2026) are recent/future-dated preprints; treat their claims as unverified until read directly. Do not cite their results secondhand.
- The greedy counterexample does **not** resolve this problem — don't conflate "greedy is not a 2-approx" with "no 2-approx exists."
- Beware known dead ends: the classical cycle-cover framework seems stuck above 2.4; naive LP relaxations for SCS have integrality gaps exceeding 2 (verify). Also remember preprocessing (removing contained strings) is free but must be accounted for in the analysis.

---
*`ALGO-000167` · unverified*

## Acceptance guidance

Any of the following would count:
1. **Upper bound (the prize):** a proof that a specified polynomial-time algorithm outputs a superstring of length ≤ \(2\cdot\mathrm{OPT}\) on every instance.
2. **Lower bound:** a proof that polynomial-time factor-2 approximation is impossible under a standard assumption (P ≠ NP or UG), which would close the problem negatively.
3. **Intermediate:** any ratio below 2.45 would be publishable progress; matching upper and lower constant bounds would fully resolve the approximability.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/f7f5d926-2951-4b5f-b2ea-d31da7e84150?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000167.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000167)

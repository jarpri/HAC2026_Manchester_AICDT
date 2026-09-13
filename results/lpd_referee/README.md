# LPD + flow, with an independent renderer choosing per body

Asteroid04.stl … Asteroid10.stl. **5.5632 / 6** on the public models under the organisers' own
evaluation code, against **5.5442** for the convex stage — the only pipeline we measured that
beats convex.

A learned primal-dual convex inversion gives a convex body from the lightcurves and a
conditional flow carves concavities onto it. Then, per model, the better of the two is chosen
by an independent forward model — DAMIT's renderer scored against the Blender lightcurves that
ship with all ten bodies. The shapes are ours; only the *choice* between them is outsourced,
because our own misfit is anti-correlated with shape accuracy while the referee picks the
higher-scoring body 3 times out of 3 on the public models.

Carved on 4, 5, 6, 7, 9, 10; convex on 8.

Full method, scoreboard and everything tried and rejected: branch **`harry/lpd-referee`**
(`submission/`, `BENCHMARKS.md`). Reproduce the score with

    PYTHONPATH=. python scripts/benchmark.py results/referee_public results/convex --models 1 2 3

**Caveat:** that is three public bodies, two of them near-convex. Nothing here is measured on
models 4–10, and the selection rule is validated 3/3 — but that is 3.

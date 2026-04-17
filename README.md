# CIVIL-534 Course Project

This repository contains the group project for the course *CIVIL-534: Computational Systems Thinking for Sustainable Engineering*.

The project is organized into two main parts:

* **milestone_part1/**: World2 model characterization, including parameter analysis and system behavior exploration.
* **milestone_part2/**: World3-based automated policy design, including policy screening, grid search, and sustainability evaluation.

Each folder contains a self-contained notebook along with the corresponding input data and output results.


## Part 1 — World2 Parameter Characterisation

**Notebook:** [milestone_part1/world2_parameter_tests.ipynb](milestone_part1/world2_parameter_tests.ipynb)

Eight directional scenarios test how World2 responds to ±20% shifts in four key parameters: capital investment rate, birth rate, death rate, and pollution production rate. The notebook extends this with:

- **Leverage-point screening** across seven parameters (BRN, DRN, CIGN, CIDN, NRUN, POLN, FC)
- **Policy synergy check** — whether combined interventions differ from the sum of individual effects

**Key outputs:** time-series comparison across population / pollution / resources / quality-of-life, summary heatmap, and a QoL-sensitivity tornado chart.

## Part 2 — World3 Automated Policy Design

**Notebook:** [milestone_part2/part2.ipynb](milestone_part2/part2.ipynb)

A full data-driven pipeline that finds sustainability-maximising World3 policies:

1. **Indicator screening** — 14 candidate output variables → 4 selected via collapse-magnitude, correlation (|r|>0.85 pruned), and discrimination-power analysis
2. **Control-variable screening** — 8 candidate policy levers → 4 kept via single-parameter sensitivity scan
3. **Sustainability score** (defined in [sustainability_score.md](sustainability_score.md)): weighted sum of natural-resource, pollution, life-expectancy, and population sub-scores
4. **Grid search** — 600 scenarios over `{nruf2, ppgf2, dcfsn, pyear}`
5. **Analysis** — tornado chart, score distribution, optimal-vs-baseline trajectories, parameter-interaction heatmap

**Optimal policy found:** `nruf2=0.20, ppgf2=0.10, dcfsn=3.0, pyear=1975` → sustainability score **0.88** vs baseline **0.39**.

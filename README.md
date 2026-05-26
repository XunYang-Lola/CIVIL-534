# CIVIL-534 Course Project

Group project for *CIVIL-534: Computational Systems Thinking for Sustainable Engineering*.

**Authors:** Zhiyan Ke, Xun Yang, Yizhi Zhao
**Final report:** [CIVIL_534_final_report (5).pdf](CIVIL_534_final_report%20%285%29.pdf)

The project combines **system dynamics**, **network analysis**, and **automated policy search** on the World2/World3 models to identify leverage points for sustainable development.

## Repository Structure

* **milestone_part1/** — World2 parameter characterisation (sensitivity, leverage screening, synergy check).
* **milestone_part2/** — World3 milestone policy design (indicator/lever screening, sustainability score, grid search).
* **final/** — Final deliverable: network analysis + refined policy search.
* **pyworld2-main/**, **pyworld3-main/** — Upstream simulation libraries used by the notebooks.
* **src/** — Shared helper code.

## Notebooks

| Notebook | Content |
|----------|---------|
| [milestone_part1/world2_parameter_tests.ipynb](milestone_part1/world2_parameter_tests.ipynb) | World2 ±20% scenarios, leverage screening, policy synergy. |
| [milestone_part2/part2.ipynb](milestone_part2/part2.ipynb) | World3 milestone pipeline: indicator/lever screening, 600-scenario grid search. |
| [final/network_analysis.ipynb](final/network_analysis.ipynb) | World3 graph (316 nodes, 507 edges): centrality, cycles, Louvain communities, k-core. |
| [final/candidates_selection.ipynb](final/candidates_selection.ipynb) | Network-based leverage-point screen for policy variables. |
| [final/policy_design.ipynb](final/policy_design.ipynb) | 500-scenario exhaustive grid search over network-selected levers. |

## Headline Result

Optimal policy: `pyear = 1985, icor2 = 4.0, ppgf2 = 0.10, nruf2 = 0.10` → sustainability score **0.764** vs baseline **0.390** (+96%).

See the [final report](CIVIL_534_final_report%20%285%29.pdf) for the full analysis, the refined sustainability metric, and discussion.

## Environment

Conda environment specification in [environment.yml](environment.yml).

# Sustainability Score Definition

## Total Score

$$
S_{\text{total}} = 0.35\, S_{\text{nr}} + 0.30\, S_{\text{pol}} + 0.20\, S_{\text{le}} + 0.15\, S_{\text{pop}}
$$

where $S_{\text{total}} \in [0, 1]$, composed of four weighted sub-indicators defined below.

---

## 1. Natural Resource Score $S_{\text{nr}}$ (weight 35%)

$$
S_{\text{nr}} = \operatorname{clip}\!\left(\frac{\mathrm{nr}(2100)\,/\,\mathrm{nr}(1900)}{0.30},\; 0,\; 1\right)
$$

Full score is awarded when the fraction of non-renewable resources remaining in 2100 is at least 30% of the initial stock.

---

## 2. Pollution Score $S_{\text{pol}}$ (weight 30%)

$$
S_{\text{pol}} = \operatorname{clip}\!\left(1 - \frac{\max_{t}\mathrm{ppolx}(t) - 2.0}{6.0},\; 0,\; 1\right)
$$

Full score when the peak persistent pollution index does not exceed 2.0; the score drops to zero when the peak reaches 8.0.

---

## 3. Life Expectancy Score $S_{\text{le}}$ (weight 20%)

$$
S_{\text{le}} = \operatorname{clip}\!\left(\frac{\overline{\mathrm{le}}_{\,[2050,\,2100]}}{60},\; 0,\; 1\right),
\qquad
\overline{\mathrm{le}}_{\,[2050,\,2100]} = \frac{1}{|T|}\sum_{t \in T} \mathrm{le}(t)
$$

where $T = \{\, t : 2050 \leq t \leq 2100 \,\}$. Full score is awarded when the mean life expectancy over the second half of the century reaches 60 years.

---

## 4. Population Stability Score $S_{\text{pop}}$ (weight 15%)

$$
S_{\text{pop}} = \operatorname{clip}\!\left(\frac{\overline{P}_{\,[2090,\,2100]}}{4 \times 10^{9}},\; 0,\; 1\right)
\cdot
\operatorname{clip}\!\left(R_{\text{crash}},\; 0,\; 1\right)
$$

where:

$$
\overline{P}_{\,[2090,\,2100]} = \frac{1}{|T'|}\sum_{t \in T'} \mathrm{pop}(t),
\qquad
T' = \{\, t : t \geq 2090 \,\}
$$

$$
R_{\text{crash}} = \frac{\min_{\,t \geq 2000}\, \mathrm{pop}(t)}{\mathrm{pop}(2000)}
$$

Unlike the other sub-scores, $S_{\text{pop}}$ is a **product** of a size term and a crash-penalty term. If either factor approaches zero, the score collapses. This design explicitly penalises overshoot-and-collapse scenarios in which population peaks and then falls below its year-2000 level.

---

## Auxiliary Definitions

$$
\operatorname{clip}(x,\, a,\, b) = \min\!\bigl(\max(x,\, a),\; b\bigr)
$$

| Symbol | Meaning | Source |
|---|---|---|
| $\mathrm{nr}(t)$ | Non-renewable resources at time $t$ | `model.nr` |
| $\mathrm{ppolx}(t)$ | Persistent pollution index | `model.ppolx` |
| $\mathrm{le}(t)$ | Life expectancy at birth (years) | `model.le` |
| $\mathrm{pop}(t)$ | Total population (persons) | `model.pop` |

---



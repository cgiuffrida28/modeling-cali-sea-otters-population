# Modeling California Sea Otter Population

**How do exponential and logistic models describe sea otter population growth, and how can population management be designed so it stabilizes at the carrying capacity?**

A mathematical modeling project (MATH374) that uses discrete recurrence models in MATLAB to simulate the California sea otter population over 100 years, test artificial population additions, and design a management strategy with a provable stable equilibrium.

---

## Overview

California sea otters are a threatened species, so understanding how their population grows, and how conservation efforts could change it, is a useful modeling problem. This project starts from a population of 3,000 otters and a carrying capacity of 16,000, and compares three environmental scenarios using intrinsic annual growth rates drawn from Monterey Bay Aquarium and UCSB research:

| Scenario | Growth rate (r) |
|---|---|
| Best | 0.052 |
| Average | 0.011 |
| Worst | -0.029 |

---

## Project Structure

```
├── MATH374_Mini-Project_1_Report.pdf   # Full written report (code in Appendix A)
└── README.md
```

---

## Report Structure

| Section | Description |
|---|---|
| 1. Identifying the Problem | Background and project objective |
| 2. Variables, Parameters, Assumptions | Model setup and simplifying assumptions |
| 3. Exponential Model | Unbounded growth, P(n+1) = (1 + r)P(n) |
| 4. Logistic Model | Growth limited by carrying capacity K = 16,000 |
| 5. Adding to the Population | Constant and proportional additions, and how they shift the equilibrium |
| 6. Stabilization at Carrying Capacity | A deficit-based management rule with fixed-point and stability analysis |
| 7. Conclusion | Findings, limitations, and possible extensions |
| Appendix A | MATLAB code for all simulations |

---

## Methods

- **Exponential model:** annual change proportional to the current population.
- **Logistic model:** exponential growth multiplied by a limiting factor, `(1 - P/K)`.
- **Managed model:** logistic growth plus an addition term `A(P)`, tested with four strategies: +3 otters/year, +10 otters/year, +1% of population/year, and +5% of population/year.
- **Stabilization strategy:** `A(P) = a * max(K - P, 0)`, which adds a fraction of the remaining population deficit each year and stops once K is reached.
- **Analysis tools:** fixed-point analysis (`f(K) = K`) and derivative-based stability analysis (`|f'(K)| < 1`).

Built with **MATLAB**.

---

## Key Findings

- The exponential model is unrealistic over long horizons: in the best case the population reaches roughly 477,000 otters after 100 years, while the worst case falls to about 158.
- The logistic model gives a much more realistic picture. The best case levels off near 16,000, the average case rises steadily, and the worst case declines toward extinction, since the carrying capacity is a ceiling, not a floor.
- Constant and proportional additions shift the long-run equilibrium *above* K. The larger the addition, the higher the new equilibrium (about 88,700 for the 5% strategy), which is mathematically valid but ecologically unrealistic.
- The deficit-based strategy keeps K = 16,000 as a fixed point. Since `f'(K) = 1 - r - a`, K is stable for all tested values (a = 0.01, 0.05, 0.10), and larger values of `a` reach K faster.

**Conclusion:** Simply adding otters changes the model's equilibrium, but tying additions to the remaining deficit lets management speed up recovery while preserving the carrying capacity.

---

## Limitations

The models assume constant growth rates and a fixed carrying capacity, and they ignore age structure, random events such as disease or extreme weather, and migration. Extending the models to include these factors would be a natural next step.

---

## Authors

**Cole Giuffrida**, **Abdalla Mohammed Ali**, **David Nunez**

MATH374, Instructor: Kelli Gutierrez, September 2026

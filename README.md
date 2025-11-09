# A/B Test Analysis: The Impact of In-Game Gates on Player Retention in "Cookie Cats"


This project analyzes the results of an A/B test to quantify the strategic impact of a product change on user retention and inform a final go/no-go decision for the "Cookie Cats" product team.

---

### 1. Project Overview & Business Problem

This project analyzes the results of an A/B test conducted on the popular mobile game, "Cookie Cats". The game has in-game "gates" that force players to wait a certain amount of time or make an in-app purchase to progress.

* **Business Question:** What is the impact of moving the first gate from level 30 to level 40 on player retention?
* **Goal:** Provide a data-driven recommendation to the product team on whether to keep the gate at level 30 (Control Group) or move it to level 40 (Test Group).

---

### 2. Data & Methodology

* **Dataset:** `cookie_cats.csv` (from `data/` directory), containing A/B test data for 90,189 players. Each player was assigned to either the control group (`gate_30`) or the test group (`gate_40`).
* **Key Metrics (KPIs):**
    * **1-Day Retention:** Percentage of players returning 1 day after install.
    * **7-Day Retention:** Percentage of players returning 7 days after install.
* **Statistical Method:** A **Chi-Squared Test of Independence** was performed to determine if the observed differences in retention rates between the two groups were statistically significant.
    * **Significance Level (Alpha):** `0.05`

---

### 3. Key Findings

The analysis yielded the following objective, data-driven findings:

* ✅ **Well-Designed Test:** The two experimental groups were well-balanced, with a near 50/50 split of the player base (gate_30: 44,700 players, gate_40: 45,489 players).
* ❌ **No Significant Impact on Short-Term Retention:** The change had **no statistically significant impact** on 1-day retention. The observed difference falls within the margin of random chance (**p-value = 0.0755**).
* 📉 **Significant NEGATIVE Impact on Long-Term Retention:** Moving the gate to level 40 resulted in a **statistically significant decrease** in 7-day retention (**p-value = 0.0016**). The control group (gate_30) outperformed the test group.
* ➡️ **No Significant Impact on Engagement:** There was no significant difference in player engagement (measured by `sum_gamerounds`) between the two groups. This indicates the change affected the *decision to return*, not the *volume of play*.

---

### 4. Business Impact & Interpretation (The "Why")

The data strongly suggests that moving the gate to level 40 is **detrimental to long-term player retention.**

While the change does not impact immediate, next-day returns, it has a proven negative effect on keeping players engaged for a full week. A plausible hypothesis for this outcome is related to player psychology and the timing of the "friction point":

* The gate is a mandatory "pay-or-wait" mechanic. When placed at level 30, it serves as an early filter and a milestone.
* By delaying this first mandatory break to level 40, players experience a longer, uninterrupted period of gameplay, setting an expectation of frictionless progression.
* When they finally encounter the gate, this **sudden disruption** can be perceived as more frustrating, leading to higher churn among players who were otherwise on a path to becoming long-term users.

This interpretation explains why the negative impact is concentrated on 7-day retention; the change primarily affects the decision-making of moderately engaged players.

---

### 5. Final Recommendation

Based on the statistically significant negative impact on long-term player retention (p < 0.05), it is strongly recommended NOT to implement the change of moving the gate to level 40.
The existing version with the gate at level 30 should be maintained to prevent long-term player churn and protect the existing player lifecycle. Further A/B tests could explore alternative mechanics to increase retention without introducing late-game friction.

### Tools Used

Python: For data analysis and scripting.

Pandas: For data manipulation and analysis.

Matplotlib / Seaborn: For data visualization.

SciPy: For statistical testing (Chi-Squared test).

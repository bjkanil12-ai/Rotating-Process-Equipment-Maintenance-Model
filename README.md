# Rotating-Process-Equipment-Maintenance-Model
This project uses Multiple Linear Regression in Google Sheets to analyze the AI4I 2020 sensor dataset. It identifies statistically significant predictors of machine failure (like torque, speed, and wear) without writing any code.

### Part 1: Overall Model Grade (Is the model useful?)

We look at two numbers to judge the whole model:

* **R Square (0.417):**
    * **What it is:** This is the model's "accuracy" score.
    * **What it means:** The model successfully explains **41.7%** of the factors that lead to a machine failure. This result shows that sensor data is highly relevant.

* **Significance F (0.00000000267):**
    * **What it is:** This is the model's "proof of validity."
    * **What it means:** Because this number is extremely small (much less than 0.05), it confirms the entire model is **statistically significant**. The relationships found were real and not just a random coincidence.

**Conclusion:** The model is valid and useful.

---

### Part 2: Key Drivers (Which sensors *actually* matter?)

This is the most important part. We look at the `P-value` column. The rule is: **If `P-value` < 0.05, the factor is a SIGNIFICANT predictor.**

* **`Rotational Speed (rpm)` (P-value = 0.000000016):**
    * **Finding:** **Extremely Significant.** This is a critical and reliable driver of failure.

* **`Torque (Nm)` (P-value = 0.0000032):**
    * **Finding:** **Extremely Significant.** Just like speed, the load on the machine is a primary cause of failure.

* **`Power (W)` (P-value = 0.0027):**
    * **Finding:** **Significant.** The `power_W` feature you created is a valid predictor.

* **`Tool Wear (min)` (P-value = 0.0319):**
    * **Finding:** **Significant.** This confirms a core engineering principle: the age of a component has a real, measurable effect on its likelihood of failing.

* **`Temperature Difference (K)` (P-value = 0.0847):**
    * **Finding:** **Not Significant.** This is a key insight. The P-value is *higher* than 0.05, so in this 100-row sample, it's not a reliable predictor.

* **`Air Temp (K)` (P-value = 0.2235):**
    * **Finding:** **Not Significant.** This also makes sense. The ambient air temperature doesn't directly cause a failure.

---

### Part 3: Engineering Conclusion

Based on these results, we can confidently state:

1.  We have built a **statistically valid model** to predict machine failure.
2.  We have proven that the most critical, reliable predictors of a breakdown are the **`Rotational Speed`**, **`Torque`**, and the **`Tool Wear`** (age) of the component.
3.  A predictive maintenance program should focus on monitoring these three key factors.

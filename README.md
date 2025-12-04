# Hi-Paris-Hi-ckathon-2025
Hi!ckathon 6 (Nov 2025), organized by Hi! PARIS (HEC &amp; IP Paris), was a premier 48-hour AI challenge. Teams leveraged the massive PISA dataset to build socially impactful solutions, bridging advanced data science with business strategy, supported by industry leaders like Capgemini &amp; L'Oréal.


# EducAId: AI for Educational Continuity

![Hackathon](https://img.shields.io/badge/Hi!ckathon_6-Laureate-gold)
![Award](https://img.shields.io/badge/Award-Best_Scientific_Approach-blue)
![Model](https://img.shields.io/badge/Model-CatBoost-green)
![R2 Score](https://img.shields.io/badge/R²-0.7909-brightgreen)

> "To teach the mind, you must reach the human."

EducAId is an AI-driven Early Intervention System developed during Hi!ckathon 6 (organized by HEC Paris & Institut Polytechnique de Paris). It addresses the "Volume Barrier" in education where teachers managing 90+ students become "managers of grades" rather than mentors. Our model restores educational continuity by detecting at-risk students before they disconnect.

---

## Achievements

* **Ranked 7th** on the Leaderboard (out of 68 teams).
* **Honorable Mention** from the Grand Jury.
* **Selected** to represent France at the Hi!Paris x IPAI Foundation Hackathon 2026 (Germany).

---

## The Scientific Approach

We analyzed the PISA Dataset (1.7 Million rows, 300+ features). Our winning strategy moved beyond standard modeling by focusing on robustness in unseen environments.

### 1. Innovation: Anticipatory Data Pruning

Instead of relying solely on training set feature importance, we analyzed the structure of the unseen test set.

* **The Problem:** Many features present in the training data were sparse or non-existent in the real-world test scenario.
* **The Fix:** We proactively pruned 74 columns that had extremely high sparsity in the test environment.
* **The Result:** This prevented the model from "hallucinating" on patterns that wouldn't exist in deployment, significantly boosting our generalization capability.

### 2. Model Architecture
 
Our solution utilized a sophisticated Heterogeneous Stacking approach, combining powerful gradient boosting frameworks to find the optimal predictor.

#### Model 1: XGBoost Regressor
We deployed XGBoost as our primary estimator to capture non-linear relationships in the numerical data. It served as a robust baseline, offering high computational efficiency and effective handling of sparse data structures post-pruning.

#### Model 2: CatBoost Regressor
CatBoost was selected as the specialized engine for the PISA survey data due to its superior handling of categorical features and "ordered boosting" technique, which reduces overfitting on small datasets.

**Hyperparameters (Final Tuned):**
We fine-tuned this model extensively, utilizing Grid Search to reach the following optimal parameters:
* Iterations: 8195
* Learning Rate: 0.0166
* Depth: 11
* L2 Leaf Regularization: 0.024
* Bagging Temperature: 1.47
* Random Strength: 5.29
* Border Count: 221
* Grow Policy: Depthwise
* Loss Function: RMSE

#### Model 3: Heterogeneous Stacking (Final Predictor)
For the final predictions, we did not rely on a single model. We implemented a Non-linear Meta-Learner that stacked the predictions from XGBoost and CatBoost. This allowed us to leverage the strengths of both algorithms XGBoost's efficiency with numerical splits and CatBoost's precision with categorical logic resulting in a final validation R² of 0.7909.

---

## Results

| Metric | Score |
| :--- | :--- |
| **Validation R²** | **0.7909** |

---

## Acknowledgements

Huge thanks to Hi! PARIS Center, HEC Paris, Institut Polytechnique de Paris, and corporate sponsors (Capgemini, L'Oréal, VINCI, TotalEnergies, Schneider Electric) for the support and coaching.

*Project developed for Hi!ckathon 6 (Nov 2025).*

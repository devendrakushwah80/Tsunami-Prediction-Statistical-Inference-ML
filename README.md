# 🌊 Tsunami Prediction Using Earthquake Features

## 📌 Project Overview

This project focuses on predicting **tsunami occurrence (Yes/No)** based on historical **earthquake characteristics** using machine learning and statistical inference.

Rather than treating ML as a pure black‑box prediction task, this notebook emphasizes **interpretability and hypothesis testing**, answering not only *"what the model predicts"* but also *"which features truly matter and why"*.

---

## 📊 Dataset Description

The dataset contains seismic event records with the following key features:

| Feature             | Description                                       |
| ------------------- | ------------------------------------------------- |
| magnitude           | Earthquake magnitude                              |
| depth               | Depth of earthquake (km)                          |
| latitude, longitude | Epicenter location                                |
| mmi                 | Modified Mercalli Intensity                       |
| cdi                 | Community Decimal Intensity                       |
| sig                 | Overall significance score                        |
| nst                 | Number of seismic stations                        |
| gap                 | Azimuthal gap                                     |
| dmin                | Minimum station distance                          |
| Year, Month         | Temporal features                                 |
| tsunami             | **Target variable** (1 = tsunami, 0 = no tsunami) |

---

## ⚙️ Methodology

### 1️⃣ Data Preprocessing

* Selected relevant numerical features
* Target variable: `tsunami`
* **Train‑test split** applied
* **RobustScaler** used to handle outliers common in seismic data

---

### 2️⃣ Model Selection

A **Gradient Boosting Classifier** was chosen due to:

* Ability to model non‑linear relationships
* Strong performance on tabular structured data
* Built‑in feature importance capability

**Model configuration:**

* `n_estimators = 200`
* `learning_rate = 0.05`
* `max_depth = 3`
* `random_state = 42`

---

### 3️⃣ Model Evaluation

The model was evaluated using:

* **Classification Report** (Precision, Recall, F1‑Score)
* **ROC‑AUC Score** (Primary metric)

This ensured both **class‑wise performance** and **overall discrimination ability** were assessed.

---

## 🧪 Hypothesis Testing (Core Contribution)

Instead of relying only on feature importance plots, **statistical hypothesis testing** was performed using a **Permutation Test**.

### Hypothesis Framework

For each feature:

* **H₀ (Null Hypothesis):** Feature has no significant contribution to tsunami prediction
* **H₁ (Alternative Hypothesis):** Feature significantly contributes to tsunami prediction

### Testing Procedure

1. Compute baseline ROC‑AUC
2. Randomly permute a single feature
3. Recalculate ROC‑AUC
4. Repeat for 100 permutations
5. Compute **p‑value** for each feature

---

## 📈 Key Findings

✔ **Geophysical features** such as:

* Magnitude
* Depth
* Latitude / Longitude
* Seismic intensity metrics (MMI, CDI, SIG)

showed **statistically significant impact** on tsunami prediction.

❌ **Temporal features** (Year, Month) showed **weak or insignificant contribution**, confirming that tsunami occurrence depends more on **physical characteristics** than time patterns.

---

## ✅ Final Conclusion

This project demonstrates that:

* Machine learning should not stop at prediction accuracy
* **Statistical inference validates model trustworthiness**
* Permutation‑based hypothesis testing is a powerful tool for interpreting complex models

By combining **Gradient Boosting** with **formal hypothesis testing**, the analysis provides both **high performance** and **scientific credibility** — a critical requirement in real‑world disaster prediction systems.

---

## 🛠️ Tech Stack

* Python
* Pandas, NumPy
* Scikit‑learn
* Matplotlib, Seaborn

---

## 📌 Future Improvements

* Add SHAP‑based explanations
* Compare with Logistic Regression & Random Forest
* Extend to multi‑class tsunami severity prediction

---

⭐ *If you found this project insightful, feel free to star the repository!*

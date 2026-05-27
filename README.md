# Corporate Risk & Premium Analytics: Predictive Modeling of Healthcare Costs

An enterprise-level data science and business intelligence case study focused on auditing, modeling, and predicting individual healthcare liabilities. This project transitions from basic correlation analysis to engineered multiple linear regression pipelines, establishing an optimized operational model for actuarial risk forecasting.

---

## 🎯 Executive Summary & Business Case

### The Problem
Traditional health insurance premium underwriting often relies on generalized historical brackets, leading to mispriced policies, adverse selection risks, and competitive disadvantages. To safeguard profit margins while ensuring fair, competitive pricing, financial underwriting teams must understand exactly which demographic, physiological, and lifestyle traits drive real-world medical claims variance, and quantify that impact mathematically.

### The Solution
This analytical framework ingests historical policyholder records to isolate premium drivers, audit statistical variances, and construct an automated predictive pipeline. 

By employing **Recursive Feature Elimination (RFE)**, the model strips out non-contributing operational variables (such as biological sex and geographic region), creating a lean, high-performing asset that captures the vast majority of premium variance with minimal data overhead.

---

## 📊 Key Analytical & Business Insights

### 1. The Baseline Exposure (Age vs. Charges)
A foundational simple linear regression establishes a clear baseline for structural cost escalation:
* **Annual Accrual Rate:** On average, baseline medical charges increase by **$257.72 per year** of age.
* **Base Intercept:** The model establishes a zero-anchor starting charge of **$3,165.89**.
* **The Analytical Limitation:** Age in isolation yields an **$R^2$ score of only 0.0894**. This indicates that while age is statistically significant, it accounts for **less than 9%** of total premium variance, proving that a univariate pricing model introduces severe financial risk.

### 2. Lifestyle Stratification (The Smoking Premium)
Introducing smoking status completely transforms the cost distribution landscape:
* Non-smokers occupy a tightly bound, predictable lower baseline cost band.
* Smokers shift entirely into elevated, high-liability cost tiers. Across every single age demographic, a policyholder who smokes incurs a drastic, immediate baseline premium spike of thousands of dollars, completely outpacing standard chronological age progression.

### 3. Physiological Multipliers (BMI Interaction)
Evaluating Body Mass Index (BMI) reveals a critical interaction dynamic:
* For non-smokers, an increasing BMI results in a negligible, flat slope regarding overall costs.
* For smokers, an increasing BMI behaves as an exponential risk multiplier. High BMI combined with a positive smoking status triggers the highest financial exposure in the entire dataset, signaling that underwriting models must treat these features as interconnected risks rather than isolated variables.

### 4. Advanced Multi-Variable Optimization
By expanding the framework into an encoded, scaled Multiple Linear Regression model, the predictive capacity expands drastically:
* **Predictive Accuracy ($R^2$):** **0.7836** — The optimized model successfully explains **78.36% of the variance** in real-world medical charges.
* **Mean Absolute Error (MAE):** **$4,181.19** — On average, the model's automated premium predictions deviate from actual historical costs by roughly $4,180, a major improvement over simple baseline estimates.
* **Root Mean Squared Error (RMSE):** **$5,796.28**

---

## 🛠️ Feature Optimization & Architecture (RFE)

To streamline data collection overhead for underwriting agents, a Recursive Feature Elimination workflow was engineered to rank independent predictors by structural importance:

| Priority Rank | Engineered Feature | Business Significance | Strategic Action |
| :---: | :--- | :--- | :--- |
| **1** | `smoker_yes` | Primary driver of high-cost volatility | Mandatory Input Field |
| **2** | `age` | Linear baseline risk progression | Mandatory Input Field |
| **3** | `bmi` | Chronic health risk multiplier | Mandatory Input Field |
| **4** | `children` | Dependent liability adjustments | Mandatory Input Field |
| **5** | `region_southwest` | Regional demographic variation | Omit (Negligible Return) |
| **6** | `region_southeast` | Regional demographic variation | Omit (Negligible Return) |
| **7** | `region_northwest` | Regional demographic variation | Omit (Negligible Return) |
| **8** | `sex_male` | Biological gender classification | Omit (Zero Statistical Value) |

**Strategic Underwriting Conclusion:** The optimal operational model requires a maximum of **3 to 4 features** (`smoker`, `age`, `bmi`, and `children`). Including geographic regions or biological sex adds architectural complexity and computational overhead without providing any statistically significant reductions in prediction error.

---

## 📂 Repository Blueprint

* 📓 **`M11 Casestudy Sean Nelson-1-1.ipynb`** — End-to-end technical execution file. Contains data engineering, dummy encoding, feature scaling pipelines, model training, cross-validation, and visualization generation.
* 📊 **`insurance.csv`** — Clean structured database containing historical parameter entries for 1,338 policyholders.
* 📄 **`MedicalCostsSection3.docx`** — Project brief outlining corporate core objectives, instructions, and analytical prompts.

---

## 🚀 Deployment & Local Execution Guide

Follow these steps to deploy this analytics workspace on your local machine using **Git Bash**.

### Prerequisite Environment Configuration
Ensure your machine has Python 3.x installed. Open your terminal or Git Bash and install the required data processing, visualization, and machine learning dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn notebook

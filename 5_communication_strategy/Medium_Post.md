# 🚀 How I Increased Satellite Observation Success Rates by 38.8% Using Machine Learning

## An MIT Capstone Project with Real Impact for the SatNOGS Community

![Satellite Observation Success Improvement](https://via.placeholder.com/800x400/0d47a1/ffffff?text=Success+Rate+49.5%25+→+88.3%25)

*When ground station operators worldwide are wasting half their observation time, the solution might just be a well-tuned Random Forest model. This is the story of how I built one—and why it matters.*

---

## The Problem: Wasted Satellite Observations

As part of the **MIT Emerging Talent Program in Computer and Data Science**, I worked on a capstone project rooted in a very real challenge faced by the amateur satellite community: **predicting satellite observation success**.

The **SatNOGS (Satellite Networked Open Ground Station)** network is powered by hundreds of volunteer-operated ground stations around the world. Together, they collect millions of satellite observations every year.

But there’s a problem:

> **Nearly 50% of all satellite observations fail.**

That means wasted equipment time, energy, and missed scientific opportunities.

### Why This Matters

- Over **12.5 million observations** stored in the SatNOGS database  
- **600+ volunteer ground stations** worldwide  
- Observations are often scheduled with *no predictive guidance*  
- Every failed pass equals lost scientific data  

---

## The Goal: Can We Do Better Than 49.5%?

Random scheduling produces a **49.5% success rate**.

The goal of this project was simple—but ambitious:

> **Can we predict the likelihood of success *before* scheduling an observation?**

If so, ground station operators could focus their limited resources on passes that actually work.

---

## The Data: 578,000 Observations Over Four Years

I extracted and processed **four years of SatNOGS data (2021–2025)**.

After cleaning and validation, the final dataset contained:

- **578,010 satellite observations**
- **39 original features**
- Temporal, geometric, geographic, and operational information

Examples of features included:
- Time of day and season  
- Maximum satellite altitude  
- Station latitude, longitude, and altitude  
- Whether an observation was archived  

---

## The “Oh No” Moment: Data Leakage

Early experiments looked *too good to be true*.

Some models achieved **100% accuracy**.

That’s when I discovered a classic machine learning trap: **data leakage**.

The `status` column in the dataset *perfectly defined* whether an observation succeeded or failed. Including it as a feature completely invalidated the results.

Once those leaked features were removed, performance dropped to a realistic baseline of **56.9% accuracy**.

> Lesson learned:  
> **Always question perfect results.**

---

## The Machine Learning Journey

### Phase 1: Baseline Models

I started with simple models to establish benchmarks.

- Logistic Regression struggled
- Decision Trees improved performance
- Ensemble methods dominated

Random Forests and XGBoost clearly outperformed linear models, showing that the problem was highly non-linear.

---

### Phase 2: Advanced Optimization

With feature engineering and hyperparameter tuning, performance improved dramatically.

![ROC Curve](https://via.placeholder.com/600x400/1976d2/ffffff?text=ROC-AUC+94.6%25)

The best model turned out to be a **tuned Random Forest**, achieving:

- **88.3% accuracy**
- **94.6% ROC-AUC**
- Strong generalization on unseen data

It struck the best balance between performance, stability, and interpretability.

---

## What Actually Drives Observation Success?

Using **permutation feature importance**, several clear patterns emerged.

![Feature Importance](https://via.placeholder.com/600x400/388e3c/ffffff?text=Archive+Status+19%25+Importance)

The most important factors were:

1. **Archived status**  
2. **Year of observation**  
3. **Station latitude**  
4. **Station altitude**  
5. **Station longitude**

These weren’t abstract signals—they translated directly into actionable insights.

---

## Insights That Changed Everything

### 1. Archive Management Is Critical

Archived observations were **19.4% more successful**.

This suggests that stations with good operational discipline perform significantly better.

**Action:**  
Automatically prioritize or learn from archived observations.

---

### 2. Geography Matters More Than Expected

Success rates varied dramatically by location.

- Optimal latitude band: **40.2°–52.7°**
- Southern hemisphere stations performed better overall

**Action:**  
Optimize station selection and regional scheduling strategies.

---

### 3. The Confidence Paradox

One surprising discovery:  
**Incorrect predictions were often more confident than correct ones.**

This highlighted the need for *human-in-the-loop* decision making.

**Action:**  
Use confidence thresholds to flag predictions for manual review.

---

## Practical Rules Ground Station Operators Can Use Today

From the model insights, I derived simple, deployable rules:

- Prioritize archived observations from recent years  
- Favor stations in optimal latitude bands  
- Only auto-approve predictions above a high confidence threshold  
- Schedule observations during historically successful time windows  

These rules alone can dramatically improve outcomes—even without full automation.

---

## The Impact: From 49.5% to 88.3%

### Before Machine Learning
- Success rate: **49.5%**
- Scheduling: Random
- Resource waste: High

### After Machine Learning
- Success rate: **88.3%**
- Failed observations reduced by **76.8%**
- Nearly **double the successful observations** using the same infrastructure

> This isn’t just a better model—it’s a better use of community resources.

---

## Why This Matters

Machine learning isn’t about chasing perfect metrics.

It’s about **changing decisions**.

In this case, a well-designed model helps satellite operators worldwide:
- Save time  
- Reduce wasted energy  
- Collect more scientific data  

All without new hardware.

---

## The MIT Capstone Experience

This project was completed as part of the **MIT Emerging Talent Program in Computer and Data Science**.

It reinforced several key lessons:

- Rigorous methodology matters  
- Interpretability is just as important as accuracy  
- Real impact requires understanding stakeholders—not just data  

---

## Resources & Code

- **Project Repository:**  
  https://github.com/ShadiShadab/ELO2-SatNOGs-repo-main  
  *(Actively being populated)*

- **SatNOGS Network:**  
  https://satnogs.org  

---

## Final Thoughts

The most important metric in this project wasn’t ROC-AUC; It was **how many additional successful satellite observations we enabled for the community**.

If you work with satellite data, community science, or real-world ML systems, I hope this story is useful.  
And if you’re a SatNOGS operator—try these ideas. You might be surprised by the results.

Let’s make satellite observation more successful—together. 🚀

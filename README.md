# MULTI-OBJECTIVE EVOLUTIONARY FEATURE SELECTION README

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=6366f1&height=120&section=header&text=Evolutionary%20Feature%20Selection&fontSize=32&fontColor=ffffff&fontAlignY=38&desc=NSGA-II%20for%20Medical%20Tabular%20Data&descAlignY=60&descSize=15&descColor=a5b4fc" width="100%"/>

[![License: MIT](https://img.shields.io/badge/License-MIT-6366f1?style=flat-square)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Algorithm](https://img.shields.io/badge/Algorithm-NSGA--II-14b8a6?style=flat-square)]()
[![Domain](https://img.shields.io/badge/Domain-Medical%20Tabular-f59e0b?style=flat-square)]()

</div>

---

## Overview

This project applies multi-objective evolutionary optimization (NSGA-II) to feature selection on medical tabular data simultaneously optimizing two competing objectives: maximizing model accuracy and minimizing feature count.

Standard feature selection treats this as a single-objective problem, collapsing the trade-off into a single metric. This implementation uses Pareto-front optimization to surface the full trade-off curve, giving practitioners explicit control over the accuracy-complexity trade-off.

> *Every feature you keep has a cost. Every feature you drop has a risk. NSGA-II finds the Pareto front between them.*

---

## The Problem

In medical ML, fewer features means:
- Lower data collection cost
- Reduced patient burden
- More interpretable models
- Lower overfitting risk

But fewer features also means potential accuracy loss. The optimal trade-off is dataset-dependent and cannot be determined by a single metric.

---

## Algorithm: NSGA-II

Non-dominated Sorting Genetic Algorithm II (NSGA-II) is a multi-objective evolutionary algorithm that maintains a population of candidate feature subsets and evolves them across generations using:

- **Non-dominated sorting** : ranks solutions by Pareto dominance
- **Crowding distance** : preserves diversity along the Pareto front
- **Tournament selection** : selects parents for crossover and mutation
- **Elitism** : preserves best solutions across generations

```
Population of Feature Subsets
         │
         ▼
┌─────────────────────┐
│  Evaluate           │   Accuracy + Feature Count
│  (two objectives)   │   for each candidate subset
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Non-dominated Sort │   Rank by Pareto dominance
│  + Crowding Distance│   Preserve diversity
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Selection +        │   Tournament selection
│  Crossover +        │   Bit-flip mutation
│  Mutation           │   New generation
└──────────┬──────────┘
           │
     Next Generation
           │
     (repeat until convergence)
           │
           ▼
      Pareto Front of Feature Subsets
```

---

## Results

The Pareto front reveals the full accuracy-complexity trade-off from the minimal feature subset that preserves acceptable accuracy to the full feature set at maximum accuracy. Practitioners choose any point on this front based on deployment constraints.

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Optimization** | NSGA-II (custom implementation) |
| **ML Evaluation** | scikit-learn |
| **Data** | Medical tabular datasets |
| **Visualization** | Matplotlib |
| **Language** | Python 3.10+ |

---

## Getting Started

```bash
git clone https://github.com/royxlead/multi-objective-evolutionary-feature-selection-python.git
cd multi-objective-evolutionary-feature-selection-python

pip install -r requirements.txt
python nsga2_feature_selection.py
```

---

## Research Context

Multi-objective feature selection is an active area in medical ML where interpretability requirements conflict with accuracy maximization. NSGA-II is one of the most widely cited multi-objective evolutionary algorithms, offering strong theoretical guarantees on Pareto front convergence and diversity preservation.

---

<div align="center">

**[Portfolio](https://royxlead.netlify.app) · [LinkedIn](https://linkedin.com/in/royxlead) · [ORCID](https://orcid.org/0009-0009-6582-2295)**

<img src="https://capsule-render.vercel.app/api?type=waving&color=6366f1&height=80&section=footer" width="100%"/>

</div>

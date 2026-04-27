# 📊 Data Imputation for Trajectory Reconstruction

This repository implements a **mask-aware and safety-aware adaptive data imputation framework** for reconstructing missing trajectory data in connected autonomous vehicle (CAV) systems.

The work builds upon the **LSTM + Graph Laplacian Regularized Matrix Factorization (LSTM-GL-ReMF)** model and introduces a **dynamic weighting mechanism** to improve performance under varying missing data conditions.

---

## 🚀 Key Features

- 🔄 **Adaptive Temporal-Spatial Fusion**
  - Dynamically balances temporal (LSTM) and spatial (graph-based) predictions
  - Learns context-aware weights instead of using fixed parameters

- 🧠 **Mask-Aware Learning**
  - Uses missing data patterns (gap length, missing ratio, etc.)
  - Adjusts model behavior based on data availability

- ⚙️ **Safety-Aware Adjustment**
  - Ensures physically realistic trajectories
  - Applies constraints on acceleration, jerk, and motion continuity

- 📉 **Improved Robustness**
  - Handles different missing patterns:
    - MCAR (Missing Completely At Random)
    - TCM (Temporally Continuous Missing)
    - SCM (Spatially Correlated Missing)

---

## 🏗️ Model Overview

The framework consists of two main branches:

### 1. Temporal Branch (LSTM)
- Captures time-based vehicle motion patterns
- Predicts missing values based on past trajectory

### 2. Spatial Branch
- Uses neighboring data or graph relationships
- Captures spatial correlations

### 🔀 Fusion Mechanism

The final prediction is computed as:

X̂ₜ = αₜ · X̂_tempₜ + (1 − αₜ) · X̂_spatₜ

Where:
- αₜ is dynamically computed using a gating network
- Ensures adaptive weighting between temporal and spatial estimates

---

## 🧩 Key Components

- **Mask Feature Extraction**
  - Missing ratio
  - Gap length
  - Neighbor availability
  - Data variability

- **Gate Network**
  - Lightweight neural network
  - Outputs adaptive weight αₜ

- **Safety Module**
  - Validates trajectory using kinematic constraints
  - Adjusts weights based on physical plausibility

---

## 📊 Evaluation Metrics

- RMSE (Root Mean Square Error)
- MAPE (Mean Absolute Percentage Error)

